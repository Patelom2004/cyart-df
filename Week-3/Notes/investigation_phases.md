# Structured Investigation Process (Mock Case: Deleted Files)

## 1. Identification
- Source: Disk image `deleted_file_image.dd` provided by instructor.
- File system: NTFS.

## 2. Preservation
- Used FTK Imager with write blocker to create `evidence.E01` and `evidence.dd`.
- Verified SHA-256 hash: `a3f5c9...` (before analysis).

## 3. Analysis (Autopsy)
- Ran file carving for JPEG, PDF, DOCX.
- Built timeline – discovered deletion timestamp: May 10, 14:23.
- Found file fragment in unallocated space: `confidential.xlsx`.

## 4. Documentation
- Logged every Autopsy module run.
- Screenshots of carved files and timeline.
- Exported hash of recovered file for integrity.

## 5. Presentation
- Report delivered to mock stakeholder (PDF) summarizing: recovery success, timeline, hash match.

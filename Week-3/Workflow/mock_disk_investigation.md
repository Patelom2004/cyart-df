# Mock Investigation: Recover Deleted Files from a Disk Image

**Dataset:** A small NTFS disk image (e.g., from Digital Corpora or a self‑created USB image)

## Step‑by‑Step Workflow

### Preparation
1. Install FTK Imager, Autopsy, HashMyFiles.
2. Obtain disk image `deleted.dd` (mock data: contains deleted `secret.docx`).

### Preservation
3. **Hash original image**  
   `shasum -a 256 deleted.dd` → `ABC123`
4. **Create forensic copy**  
   FTK Imager → File → Create Disk Image → Select `deleted.dd` → output `work.E01` with SHA-256 verification.
5. **Verify hash of `work.E01`** – must match `ABC123`.

### Analysis (Autopsy)
6. **New case** → Add host → Add image `work.E01`.
7. Run **File Carving** module (JPEG, PDF, DOCX, ZIP).
8. Run **Timeline** module – filter by deletion date (if known).
9. Locate `secret.docx` in unallocated space; extract and save.

### Documentation
10. Export carve results as CSV.
11. Hash the recovered `secret.docx` (`DEF456`).
12. Take screenshots of timeline and carved file.
13. Fill chain-of-custody form (mock transfer to Autopsy tool).

### Presentation
14. Write one‑page report including:  
    - Original hash, working copy hash, recovered file hash (all different but integrity proven)  
    - Timeline screenshot  
    - Conclusion: file recovered with intact contents.

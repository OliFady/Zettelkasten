# Git Architecture

## Basics

- Git Commits Snapshot of files not chars and each Commit points to its parent
- Every Object has a unique id using consistent Hashing(SHA-1).
- HEAD points to the latest Commit
- Hello => "blob 11\0Hello, Git" | shasum (adds type,size,contents)

## Git Objects
- Tree: Folder's Contentsand its metadata
- Blob: File's contents and its Metadata
- Commit: Wrapper around Tree and Blob that tracks patches 
- Tagged Annotation: 

## 3 Tree Architecture

- Working Tree (Untracked Files) -> git add 
- Staging Area or Index (Tracked Files) -> git commit (creates a Snapshot)
- Repo

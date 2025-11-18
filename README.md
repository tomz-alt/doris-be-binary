# Apache Doris 4.0.1 BE Binary

Backend (BE) binary for Apache Doris 4.0.1, split into 24 chunks for GitHub hosting.

## Download and Reassemble

```bash
# Download all chunks
for chunk in {aa..ax}; do
  wget https://raw.githubusercontent.com/tomz-alt/doris-be-binary/main/be-chunk-$chunk
done

# Reassemble
cat be-chunk-* > apache-doris-4.0.1-be-only.tar.gz

# Extract
tar -xzf apache-doris-4.0.1-be-only.tar.gz

# Cleanup
rm be-chunk-* apache-doris-4.0.1-be-only.tar.gz
```

## Contents
- Original size: 3.9GB (uncompressed)
- Compressed: 2.2GB
- Split into: 24 chunks × 95MB each
- Source: Apache Doris 4.0.1 official release

## Start BE
```bash
cd be/bin
./start_be.sh --daemon
```

# Apache Doris 4.0.1 Binaries

Backend (BE) and Frontend (FE) binaries for Apache Doris 4.0.1, split into chunks for GitHub hosting.

## Download Backend (BE)

```bash
# Download all 24 BE chunks
for chunk in aa ab ac ad ae af ag ah ai aj ak al am an ao ap aq ar as at au av aw ax; do
  wget https://raw.githubusercontent.com/tomz-alt/doris-be-binary/master/be-chunk-$chunk
done

# Reassemble and extract
cat be-chunk-* > apache-doris-4.0.1-be-only.tar.gz
tar -xzf apache-doris-4.0.1-be-only.tar.gz

# Cleanup
rm be-chunk-* apache-doris-4.0.1-be-only.tar.gz

# Start BE
cd be/bin
./start_be.sh --daemon
```

## Download Frontend (FE)

```bash
# Download all 9 FE chunks
for chunk in aa ab ac ad ae af ag ah ai; do
  wget https://raw.githubusercontent.com/tomz-alt/doris-be-binary/master/fe-chunk-$chunk
done

# Reassemble and extract
cat fe-chunk-* > apache-doris-4.0.1-fe-only.tar.gz
tar -xzf apache-doris-4.0.1-fe-only.tar.gz

# Cleanup
rm fe-chunk-* apache-doris-4.0.1-fe-only.tar.gz

# Start FE
cd fe/bin
./start_fe.sh --daemon
```

## Download Both BE + FE (One Script)

```bash
#!/bin/bash
# Download BE
for chunk in aa ab ac ad ae af ag ah ai aj ak al am an ao ap aq ar as at au av aw ax; do
  wget -q --show-progress https://raw.githubusercontent.com/tomz-alt/doris-be-binary/master/be-chunk-$chunk
done
cat be-chunk-* > be.tar.gz && tar -xzf be.tar.gz && rm be-chunk-* be.tar.gz

# Download FE
for chunk in aa ab ac ad ae af ag ah ai; do
  wget -q --show-progress https://raw.githubusercontent.com/tomz-alt/doris-be-binary/master/fe-chunk-$chunk
done
cat fe-chunk-* > fe.tar.gz && tar -xzf fe.tar.gz && rm fe-chunk-* fe.tar.gz

echo "✓ Doris BE and FE downloaded successfully!"
```

## Contents

### Backend (BE)
- Original size: 3.9GB (uncompressed)
- Compressed: 2.2GB
- Split into: 24 chunks × 95MB each

### Frontend (FE)
- Original size: 860MB (uncompressed)
- Compressed: 778MB
- Split into: 9 chunks × 95MB each

**Source:** Apache Doris 4.0.1 official release
**Download:** https://apache-doris-releases.oss-accelerate.aliyuncs.com/apache-doris-4.0.1-bin-x64.tar.gz

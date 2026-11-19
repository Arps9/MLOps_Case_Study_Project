
FROM python:3.9-slim

WORKDIR /app

RUN apt-get update && apt-get install -y --no-install-recommends \
    libgomp1 \
    && rm -rf /var/lib/apt/lists/*

COPY requirements.txt .

RUN pip install --no-cache-dir --no-compile -r requirements.txt

COPY app.py .

RUN useradd -m -u 1000 user

USER user

ENV HOME=/home/user
ENV PATH=/home/user/.local/bin:$PATH

EXPOSE 8501

CMD streamlit run app.py --server.port=8501 --server.address=0.0.0.0 --server.enableXsrfProtection=false


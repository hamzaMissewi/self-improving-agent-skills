FROM python:3.12-slim

WORKDIR /app

COPY agent_skills/backend/requirements.txt /app/requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

COPY . /app

ENV PYTHONUNBUFFERED=1

EXPOSE 7860

CMD ["sh", "-c", "cd /app/agent_skills/backend && uvicorn app:app --host 0.0.0.0 --port ${PORT:-7860}"]
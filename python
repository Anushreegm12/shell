import re
import json

log_file_path = "/tmp/timestamp.log"
output_json_path = "/tmp/errors.json"

# Regular expression pattern to match log lines with ERROR
pattern = re.compile(r"(\d{4}-\d{2}-\d{2} \d{2}:\d{2}:\d{2},\d{3}).*?ERROR.*?- (.*)", re.IGNORECASE)

errors = []

with open(log_file_path, 'r') as log_file:
    for line in log_file:
        match = pattern.search(line)
        if match:
            timestamp, message = match.groups()
            errors.append({"timestamp": timestamp, "error": message.strip()})

# Write extracted data to JSON
with open(output_json_path, 'w') as json_file:
    json.dump(errors, json_file, indent=4)

print(f"Extracted {len(errors)} error(s) into {output_json_path}")

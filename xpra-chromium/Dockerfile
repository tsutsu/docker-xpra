FROM xpra-base:latest

RUN apt-get install -y chromium-browser
ADD chromium-unsandboxed /usr/bin/chromium-unsandboxed
ENTRYPOINT ["/usr/local/bin/start-under-xpra", "/usr/bin/chromium-unsandboxed"]

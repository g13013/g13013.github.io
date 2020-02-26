FROM node:alpine
RUN apk update
RUN apk add chromium
RUN apk add nss
RUN apk add freetype
RUN apk add freetype-dev
RUN apk add harfbuzz
RUN apk add ca-certificates
RUN apk add ttf-freefont

ENV PUPPETEER_SKIP_CHROMIUM_DOWNLOAD true

WORKDIR /home
ADD package.json .
RUN npm install
RUN set -eux; \
    sed -i "s/headless\: true/headless: true,executablePath: '\/usr\/bin\/chromium-browser',args\: \['--no-sandbox', '--disable-dev-shm-usage'\]/" node_modules/kiss-my-resume/build.js; \
    sed -i "s/await browser\.close/if \(browser\) await browser\.close/" node_modules/kiss-my-resume/build.js;
    # sed -i "s/waitUntil\: 'networkidle0'/waitUntil: 'domcontentloaded'/" node_modules/resume-cli/lib/export-resume/index.js
ADD resume.template node_modules/jsonresume-theme-paper/resume.template
ENTRYPOINT [ "./node_modules/.bin/kissmyresume" ]
CMD ["build"]
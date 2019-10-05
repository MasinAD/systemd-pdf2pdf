# systemd-pdf2pdf
systemd units for automatically converting PDFs to PDFs to correct errors

## Installation
Copy `pdf2pdf` to `$HOME/bin`.
Copy `pdf2pdf.path` and `pdf2pdf.service` into `$HOME/.config/systemd/user/`. Reload user daemon:
```
systemctl --user daemon-reload
```
Then enable and start pdf2pdf.path:
```
systemctl --user enable pdf2pdf.path
systemctl --user start pdf2pdf.path
```
`pdf2pdf.path` monitors the directory `$HOME/pdf` for changes. If something changes the service unit is invoked which just executes `pdf2pdf`. `pdf2pdf` scans the directory `$HOME/pdf` for PDF files and converts them using `pdftocairo`. The bash script is configured to output the converted files to `$(xdg-user-dir DOCUMENTS)`. After conversion the original file gets removed.

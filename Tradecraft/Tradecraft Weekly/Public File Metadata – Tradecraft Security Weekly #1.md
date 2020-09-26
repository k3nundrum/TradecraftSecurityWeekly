Public File Metadata – Tradecraft Security Weekly #1

Google Search:
```
site:domain.com filetype:pdf
```
Tools:
- FOCA
- Metagoofil
- PowerMeta 
# PowerMeta
https://github.com/dafthack/PowerMeta
- to get usernames
```
C:\powershell.exe -exec bypass
PS > Import-module .\PowerMeta.ps1
PS > Get-Help Invoke-Powermeta -Examples
PS > Invoke-PowerMeta -TargetDomain spotify.com
y to download the files
y to extract metadata
```
- To get all the metadata:
```
PS > ExtractMetadata -OutputDir .\2020-5-32\ -ExtractAll
```

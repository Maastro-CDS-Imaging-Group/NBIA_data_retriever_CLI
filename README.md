# NBIA data retriever CLI

A command line replacement of NBIA data retriever.
Forked from [ygidtu/NBIA_data_retriever_CLI](https://github.com/ygidtu/NBIA_data_retriever_CLI).

---

## Install Dependencies

Since the scripts are written in [go](https://golang.org), some dependencies need to be installed before running `build.sh`:

```
sudo apt install golang-go

go get -v github.com/voxelbrain/goptions
go get -v github.com/rs/zerolog/log

```

After running `build.sh`, three files (`nbia_cli_linux_amd64`, `nbia_cli_darwin` and `nbia_cli_win64.exe`) are built in the directory. Assuming one wants to run the NBIA command line data retriever on linux, after the previous step one can go on and simply run `nbia_cli_linux_amd64` with the syntax that follows (see the "Command Line Usage" section for details):

```
./nbia_cli_linux_amd64 --input ../data/path_to_manifest/NBIA-manifest-xxxxxxxxxxx.tcia --output ../data/path_to_output/
```

## Command Line Usage

```bash
Usage: nbia_cli_xxxx [global options]                                       
                                                                              
Global options:                                                               
        -i, --input   Path to tcia file                                       
        -o, --output  Output directory, or output file when --meta enabled (default: downloads)                                                             
        -x, --proxy   Proxy                                                   
        -t, --timeout Due to limitation of target server, please set this time out value as big as possible (default: 1200000)                               
        -p, --process Start how many download at same time (default: 1)       
        -m, --meta    Get Meta info of all files                              
        -v, --version Show version                                            
            --debug   Show debug info                                         
            --help    Show this help
```

The aforementioned TCIA (`NBIA-manifest-xxxxxxxxx.tcia`) file can be obtained directly from the dataset page on [The TCIA website](https://wiki.cancerimagingarchive.net).

---

## Known Issues

Known issues:
- The `public.cancerimagingarchive.net/nbia-download/servlet` use `POST` to transfer data from server to local, the connection may be terminated even before the download is complete. Therefore, **PLEASE** set timeout as huge as possible
- progress bar is a mess when using multiple process
- I do not have a account of NBIA, therefore this program could not handle the restricted data for now.

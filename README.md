# Backup files to MEGA.nz hosting service.

Uses Python and the awesome [mega.py](https://github.com/odwyersoftware/mega.py) module to interact with MEGA's servers.

## Installation

Install the `mega.py` package into your system or environment through pip:

    pip install mega.py

Clone this repository:

    git clone https://github.com/pinguiminvestidor/megabackup

Copy `megabackup` to your executable path, e.g.:

    cd megabackup
    sudo cp megabackup /usr/local/bin

Create a credential file in the JSON format in your `$HOME/.config` directory:

    cat > $HOME/.config/megabackuprc <<EOF
    {
        "username": "yourmegaemail@example.tld",
        "password": "yourpassword"
    }
    EOF

Ensure that only you can read that `megabackuprc` file:

    chmod 600 $HOME/.config/megabackuprc


## Usage

Command syntax:

    megabackup [-p] FILE1 FILE2 ... FILEN

Pass `-p` if you'd like to obtain a shareable link to your newly-uploaded files. Note that this makes the file semi-public, as in anyone with that link can download it. By default, files are not public.

`megabackup` (currently) only uploads files to your storage root. You must authenticate with your MEGA.nz account's email address and password in order to proceed, and it may take a little time since authentication and uploading are done in two separate steps.

## Known issues

`megabackup` does not overwrite existing files in MEGA.nz: if you upload a file with the exactly same name as an existing one, MEGA will treat it as a new file, coexisting along with the other one (the difference is in the file ID).

This might be fixed further on, but for now, keep in mind that only "fresh" backups work. Pull requests to fix this are welcome.

## Roadmap

 - Directory upload (currently only files)
 - Better progress tracker (currently only 'x out of y' style)
 - Be able to upload to other directories rather than root.

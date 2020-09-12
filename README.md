# parse_fritzbox_voicemail
Parse Fritzbox Voicemail messages, and tries to transcribe the wav message via https://github.com/mwalliczek/wav2text

# Setup with dovecot and sieve
## Install
Place this file in /usr/lib/dovecot/sieve-filter

## dovecot config
```
plugin {
  sieve_extensions = +vnd.dovecot.filter
  sieve_plugins = sieve_extprograms
  sieve_filter_bin_dir = /usr/lib/dovecot/sieve-filter
}
```
## sieve filter 
```
require ["vnd.dovecot.filter"];

if address :contains "From" "fritzbox@example.com" {
    filter "parse_fritzbox_voicemail";
}
```

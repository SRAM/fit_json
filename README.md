# Round-Trip FIT ↔ JSON Conversion

A small pure-Python interpreter that converts [FIT files](http://www.thisisant.com/developer/ant/ant-fs-and-fit1) to JSON and back.

## Motivation

This is useful for examining files in the FIT format, which is an opaque format not easily processed with textual tools.

The FIT SDK includes a FIT-to-CSV utility, but CSV is a poor format and the utility doesn't cleanly round-trip undefined fields and profiles.

## Usage

Convert a FIT file to JSON using the `-j` option:

```
./fit_json.py -j < Settings.fit > Settings.json
```

The resulting JSON file can be edited with any text editor.

Convert back to FIT using the `-f` option:

```
./fit_json.py -f < Settings.json > Settings.fit
```

## Limitations

- Arrays and subfields are not supported. Everything is represented in its most basic form — enums are represented as integers, and no scaling, offsetting, or units are applied.
- String lengths are not preserved through the round trip; string field lengths are calculated to fit their contents.
- Null values receive no special handling. Missing values are not encoded at all.

## Files

| File | Description |
|------|-------------|
| `fit_json.py` | Main script |
| `fit.py` | FIT decoder |
| `fit_writer.py` | FIT encoder |
| `profile.pickle` | FIT profile definitions |
| `read_profile.py` | Script to read `profile.pickle` |
| `read_xl_pandas.py` | Script to convert `Profile.xls` to `profile.pickle` |
| `Settings.fit` | Example FIT file (settings from an Edge 510) |
| `Settings.json` | Example decoded file |
| `COPYING` | 2-clause BSD license |
| `README.txt` | This file |

# pip

## Full reinstall:

```bash
sudo pip3 install --upgrade --force-reinstall pylint
```

## Where has `pip` installed everything related to a module?:

```bash
pip3 show -f pylint > output.txt
```

## Alternative e.g. `pip3` syntax:

```bash
python3 -m pip install [module]
```
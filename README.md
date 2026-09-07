# Dotreniravanje modela Qwen3-1.7B primjenom QLoRA metode u području forenzičnog računovodstva

Ovaj repozitorij sadrži kod, skup podataka i rezultate korištene u izradi završnog rada.

## Opis projekta

Cilj rada bio je istražiti mogućnosti parametarski učinkovitog dotreniravanja velikih jezičnih modela primjenom metode **QLoRA**. Kao bazni model korišten je **Qwen3-1.7B**, koji je dotreniran na vlastitom instrukcijskom skupu podataka iz područja revizije i forenzičnog računovodstva.

Nakon postupka dotreniravanja provedena je evaluacija baznog i dotreniranog modela primjenom pristupa **LLM-as-a-Judge**, pri čemu su uspoređeni prema više kriterija kvalitete odgovora.

## Struktura repozitorija

```
dataset/      Instrukcijski skup podataka korišten za dotreniravanje
notebooks/    Google Colab bilježnica s postupkom dotreniravanja i evaluacije
results/      Konačni rezultati evaluacije modela
README.md
```

## Korištene tehnologije

- Python
- Transformers
- PEFT
- TRL
- BitsAndBytes
- PyTorch

## Korišteni model

- Bazni model: **Qwen3-1.7B**
- Metoda dotreniravanja: **QLoRA**

## Skup podataka

Instrukcijski skup podataka izrađen je na temelju međunarodnih revizijskih standarda:

- ISA 240
- ISA 315 (Revised 2019)
- ISA 500 (Exposure Draft)

Skup podataka sastoji se od instrukcijsko-odgovornih parova koji obuhvaćaju teorijska pitanja i složenije revizijske scenarije iz područja revizije i forenzičnog računovodstva.

## Rezultati

U repozitoriju se nalazi konačna tablica evaluacije koja sadrži odgovore baznog i dotreniranog modela te ocjene dobivene primjenom pristupa **LLM-as-a-Judge**.

## Pokretanje projekta

1. Klonirati repozitorij:

```bash
git clone https://github.com/KrunoslavLesic/Zavrsni-rad-QLoRA-fine-tuning.git
```

2. Otvoriti bilježnicu `notebooks/qlora_finetuning.ipynb` u Google Colabu ili Jupyter Notebooku.

3. Pokrenuti ćelije redom od početka do kraja. Sve potrebne biblioteke instaliraju se automatski na početku bilježnice.

4. Prije pokretanja potrebno je prilagoditi putanje do skupa podataka i direktorije za spremanje modela prema vlastitom okruženju.

## Autor

**Krunoslav Lešić**

Fakultet primijenjene matematike i informatike, Sveučilište Josipa Jurja Strossmayera u Osijeku

Završni rad, 2026.
# Dotreniravanje modela Qwen3-1.7B primjenom QLoRA metode u području forenzičnog računovodstva

## Opis projekta

Cilj projekta bio je primjenom metode **QLoRA** dotrenirati veliki jezični model za područje revizije i forenzičnog računovodstva te poboljšati kvalitetu njegovih odgovora pri analizi složenih revizijskih scenarija, razvoju logičkih hipoteza i predlaganju odgovarajućih revizijskih postupaka.

Kao bazni model korišten je **Qwen3-1.7B**, koji je dotreniran na vlastitom instrukcijskom skupu podataka izrađenom na temelju međunarodnih revizijskih standarda.

Nakon dotreniravanja uspoređeni su odgovori baznog i dotreniranog modela. Evaluacija je provedena primjenom pristupa **LLM-as-a-Judge**, pri čemu su odgovori ocijenjeni prema kriterijima pokrivenosti, točnosti, kvalitete zaključivanja, količine nepotkrijepljenih informacija, jasnoće i ukupne kvalitete odgovora.

## Struktura repozitorija

```text
dataset/      Instrukcijski skup podataka korišten za dotreniranje
notebooks/    Jupyter bilježnice s postupkom dotreniranja i evaluacije
results/      Rezultati odgovora modela
README.md
```

## Korištene tehnologije

- Python
- Transformers
- PEFT
- TRL
- BitsAndBytes
- PyTorch
- OpenAI API

## Korišteni model

- Bazni model: **Qwen3-1.7B**
- Metoda dotreniravanja: **QLoRA**
- Kvantizacija: 4-bit

## Skup podataka

Instrukcijski skup podataka izrađen je na temelju međunarodnih revizijskih standarda:

- ISA 240
- ISA 315 (Revised 2019)
- ISA 500 (Exposure Draft)

Skup podataka sastoji se od instrukcijsko-odgovornih parova koji obuhvaćaju teorijska pitanja i složenije revizijske scenarije iz područja revizije i forenzičnog računovodstva.

## Evaluacija
Za procjenu kvalitete odgovora uspoređeni su bazni i dotrenirani model na istim primjerima iz testnog skupa.

Automatizirana evaluacija provedena je primjenom pristupa LLM-as-a-Judge, pri čemu je jezični model **GPT-5-mini** korišten za ocjenjivanje odgovora baznog i dotreniranog modela prema sljedećim kriterijima:

- Coverage
- Correctness
- Reasoning
- Unsupported Information
- Clarity
- Overall

Za svaki primjer bilježi se i pobjednik usporedbe te kratki komentar evaluatora. Rezultati evaluacije automatski se spremaju u CSV datoteku nakon svakog obrađenog primjera.

## Rezultati

Evaluacija je provedena na **255 primjera** primjenom pristupa **LLM-as-a-Judge**. 
Bazni i dotrenirani model uspoređeni su prema šest kriterija kvalitete odgovora.

| Kriterij | Bazni model | Dotrenirani model | Poboljšanje (FT − Base) |
| --- | ---: | ---: | ---: |
| Coverage | 80.66 | 86.28 | **+5.62** |
| Correctness | 81.99 | 91.28 | **+9.29** |
| Reasoning | 77.79 | 85.69 | **+7.89** |
| Unsupported Information | 70.12 | 83.93 | **+13.81** |
| Clarity | 85.96 | 91.23 | **+5.27** |
| Overall | **80.87** | **88.40** | **+7.53** |

### Usporedba pobjednika

U izravnoj usporedbi odgovora, dotrenirani model ocijenjen je kao bolji u **175 od 255 primjera (68,63 %)**, dok je bazni model bio bolji u **80 primjera (31,37 %)**.

| Model | Broj pobjeda | Udio pobjeda |
| --- | ---: | ---: |
| Bazni model | 80 | 31,37 % |
| Dotrenirani model | 175 | 68,63 % |


## Pokretanje projekta

1. Klonirati repozitorij:

   ```bash
   git clone https://github.com/KrunoslavLesic/Zavrsni-rad-QLoRA-fine-tuning.git
   cd Zavrsni-rad-QLoRA-fine-tuning

2. Kreirati virtualno okruženje:

    python -m venv .venv

3. Instalirati `ipykernel` i registrirati virtualno okruženje kao Jupyter kernel:

    .venv\Scripts\python.exe -m pip install ipykernel
    .venv\Scripts\python.exe -m ipykernel install --user --name zavrsni-rad --display-name "Python (zavrsni-rad)"


4. Aktivirati virtualno okruženje.

   **Windows:**

    .venv\Scripts\activate


5. Otvoriti `notebooks/qlora_finetuning.ipynb` u Jupyter Notebooku i pokrenuti ćelije od početka do kraja.

6. Ako je potrebno provesti automatiziranu LLM-as-a-Judge evaluaciju, otvoriti `notebooks/llm_judge_evaluation.ipynb`.

7. Za korištenje LLM-as-a-Judge evaluacije potrebno je izraditi vlastiti API ključ za OpenAI API te ga postaviti u okruženje.

**Napomena:** Dotreniranje modela zahtijeva GPU i neće se uspješno izvršiti do kraja na CPU-u.


## Autor

**Krunoslav Lešić**

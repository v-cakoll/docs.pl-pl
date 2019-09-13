---
title: Polecenie autouczenie w narzędziu CLI ML.NET
description: Przegląd, przykłady i dokumentacja polecenia autouczenie w narzędziu CLI ML.NET.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 8363a16ab5e793e715131ac37283106517850439
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929198"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a>Polecenie "autouczenie" w interfejsie wiersza polecenia ML.NET

> [!NOTE]
> Ten temat dotyczy ML.NET interfejsu wiersza polecenia i ML.NET AutoML, które są obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.

`auto-train` Polecenie jest głównym poleceniem udostępnianym przez narzędzie interfejsu wiersza polecenia ml.NET. Polecenie umożliwia generowanie modelu dobrego jakości ML.NET (serializowany model. zip) oraz przykładowego C# kodu do uruchomienia/oceny modelu. Ponadto C# kod służący do tworzenia/uczenia modelu jest również generowany, aby zbadać, jakiego algorytmu i ustawień używa dla tego wygenerowanego "najlepszego modelu".

Można generować te zasoby z własnych zestawów danych bez konieczności pisania ich przez siebie, dzięki czemu zwiększa się produktywność nawet wtedy, gdy znasz już ML.NET.

Obecnie zadania w ML obsługiwane przez interfejs wiersza polecenia ML.NET są następujące:

- `binary-classification`
- `multiclass-classification`
- `regression`

- Kontrakt Inne zadania uczenia maszynowego, takie jak
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

Przykład użycia w wierszu polecenia:

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

`mlnet auto-train` Polecenie generuje następujące zasoby:

- Serializowany model. zip ("najlepszy model") jest gotowy do użycia.
- C#kod do uruchomienia/oceny, który wygenerował model (aby dokonać prognoz w aplikacjach użytkowników końcowych przy użyciu tego modelu).
- C#kod z kodem szkoleniowym używanym do generowania tego modelu (cele uczenia).

Pierwsze dwa zasoby mogą być bezpośrednio używane w aplikacjach użytkowników końcowych (ASP.NET Core aplikacji sieci Web, usług, aplikacji klasycznej itp.) w celu utworzenia prognoz dla tego wygenerowanego modelu ML.

Trzeci element zawartości, kod szkoleniowy, pokazuje, jaki kod interfejsu API ML.NET był używany przez interfejs wiersza polecenia do uczenia wygenerowanego modelu, aby można było sprawdzić, jakie konkretne Trainer/algorytm i funkcja Hyper-Parameters zostały wybrane przez interfejs wiersza polecenia i aparat ML.NET AutoML.

## <a name="the-auto-train-command-uses-the-automl-engine"></a>Polecenie "autouczenie" używa aparatu AutoML

Interfejs wiersza polecenia używa aparatu ML.NET AutoML (pakiet NuGet) do inteligentnego wyszukiwania najlepszych modeli jakości, jak pokazano na poniższym diagramie:

![obraz](./media/ml-net-automl-working-diagram.png "Aparat AutoML pracuje wewnątrz interfejsu wiersza polecenia ml.NET")

W przypadku uruchamiania narzędzia interfejsu wiersza polecenia ML.NET z poleceniem "autouczenie" zobaczysz narzędzie próbujące wykonać wiele iteracji z różnymi algorytmami i kombinacjami konfiguracji.

## <a name="reference-for-auto-train-command"></a>Odwołanie do polecenia "autouczenie"

## <a name="examples"></a>Przykłady

Najprostszym poleceniem interfejsu wiersza polecenia dla binarnego problemu klasyfikacji (AutoML będzie musiał wnioskować większość konfiguracji z dostarczonych danych):

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

Inne proste polecenie interfejsu wiersza polecenia dla problemu z regresją:

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

Tworzenie i uczenie modelu klasyfikacji binarnej z zestawem danych, testowym zestawem danych i dodatkowymi argumentami dostosowania:

```console
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="name"></a>Nazwa

`mlnet auto-train`-Pociąga za sobą wiele modeli (iteracje "n") na podstawie podanego zestawu danych, a następnie wybiera najlepszy model, zapisuje go jako serializowany C# plik zip, a następnie generuje powiązany kod na potrzeby oceniania i uczenia.

## <a name="synopsis"></a>Streszczenie

```console
> mlnet auto-train

--task | --mltask | -T <value>

--dataset | -d <value>

[
 [--validation-dataset | -v <value>]
  --test-dataset | -t <value>
]

--label-column-name | -n <value>
|
--label-column-index | -i <value>

[--ignore-columns | -I <value>]

[--has-header | -h <value>]

[--max-exploration-time | -x <value>]

[--verbosity | -V <value>]

[--cache | -c <value>]

[--name | -N <value>]

[--output-path | -o <value>]

[--help | -h]

```

Nieprawidłowe Opcje wejściowe powinny spowodować, że narzędzie interfejsu wiersza polecenia emituje listę prawidłowych danych wejściowych, a komunikat o błędzie wyjaśniający, który argument nie występuje, jeśli tak się dzieje.

## <a name="options"></a>Opcje

 ----------------------------------------------------------

`--task | --mltask | -T`parametry

Pojedynczy ciąg, który umożliwia rozproszenie problemu. Na przykład dowolne z następujących zadań (interfejs wiersza polecenia będzie ostatecznie obsługiwał wszystkie zadania obsługiwane w AutoML):

- `regression`-Wybierz, czy model ML będzie używany do przewidywania wartości liczbowej
- `binary-classification`-Wybierz, czy wynik modelu ML ma dwie możliwe wartości logiczne kategorii (0 lub 1).
- `multiclass-classification`-Wybierz, czy wynik modelu ML ma wiele możliwych wartości kategorii.

W przyszłych wersjach dodatkowe zadania i scenariusze, takie jak `recommendations`i `clustering` `ranking` , będą obsługiwane.

 W tym argumencie należy podać tylko jedno zadanie ML.

 ----------------------------------------------------------

`--dataset | -d`parametry

Ten argument zawiera jedną z następujących opcji:

- *Z Plik całego zestawu danych:* W przypadku korzystania z tej opcji, a użytkownik nie `--test-dataset` zapewnia `--validation-dataset`i, a następnie do walidacji modelu są używane wewnętrzne metody sprawdzania poprawności (z podziałem, itp.) lub zautomatyzowanego podziału danych. W takim przypadku użytkownik będzie musiał tylko podać ścieżkę zestawu danych.

- *B: Plik zestawu danych szkoleniowych:* Jeśli użytkownik udostępnia również zestawy danych do walidacji modelu (za pomocą `--test-dataset` i opcjonalnie `--validation-dataset`), `--dataset` argument oznacza, aby miał jedynie "zestaw danych szkoleniowych". Na przykład w przypadku korzystania z 80%-20% podejścia do weryfikowania jakości modelu i uzyskiwania metryk dokładności, "zestaw danych szkoleniowych" będzie miał 80% danych, a "testowy zestaw danych" miałby 20% danych.

----------------------------------------------------------

`--test-dataset | -t`parametry

Ścieżka pliku wskazująca plik zestawu danych testowych, na przykład w przypadku korzystania z 80%-20% podejścia podczas regularnego sprawdzania poprawności w celu uzyskania metryk dokładności.

Jeśli `--dataset` jest `--test-dataset`używana, również jest wymagane.

`--test-dataset` Argument jest opcjonalny, chyba że jest używany element--Validation-DataSet. W takim przypadku użytkownik musi użyć trzech argumentów.

----------------------------------------------------------

`--validation-dataset | -v`parametry

Ścieżka pliku wskazująca plik zestawu danych walidacji. Zestaw danych walidacji jest opcjonalny w każdym przypadku.

W przypadku korzystania `validation dataset`z programu zachowanie powinno być następujące:

- Argumenty `test-dataset` i`--dataset` są również wymagane.

- Ten `validation-dataset` zestaw danych służy do szacowania błędu prognozowania dla wyboru modelu.

- `test-dataset` Służy do oceny błędu generalizacji końcowego wybranego modelu. Najlepiej, aby zestaw testów był przechowywany w "magazynie" i znajdować się tylko na końcu analizy danych.

W zasadzie, podczas korzystania `validation dataset` z znaku `test dataset`Plus, faza walidacji jest dzielona na dwie części:

1. W pierwszej części Przyjrzyjmy się modelom i wybieramy najlepsze podejście przy użyciu danych sprawdzania poprawności (= Walidacja).
2. Następnie należy oszacować dokładność wybranego podejścia (= test).

W związku z tym rozdzielenie danych może wynosić 80/10/10 lub 75/15/10. Przykład:

- `training-dataset`plik powinien mieć 75% danych.
- `validation-dataset`plik powinien mieć 15% danych.
- `test-dataset`plik powinien mieć 10% danych.

W każdym przypadku te wartości procentowe zostaną określone przez użytkownika przy użyciu interfejsu wiersza polecenia, który udostępni już pliki.

----------------------------------------------------------

`--label-column-name | -n`parametry

W przypadku tego argumentu określona kolumna celu/Target (zmienna, która ma zostać przewidywalna) można określić za pomocą nazwy kolumny ustawionej w nagłówku zestawu danych.

Ten argument jest używany tylko w przypadku zadań nadzorowanych ML, takich jak *problem klasyfikacji*. Nie można jej używać dla zadań nienadzorowanych ML, takich jak *klastrowanie*.

----------------------------------------------------------

`--label-column-index | -i`ZAOKR

Z tym argumentem określona kolumna celu/Target (zmienna, która ma zostać przewidywalna) może być określana za pomocą indeksu liczbowego kolumny w pliku zestawu danych (wartości indeksu kolumn zaczynają się od 1).

*Uwaga:* Jeśli użytkownik używa `--label-column-name`również `--label-column-name` , jest używany.

Ten argument jest używany tylko dla zadania nadzorowanego ML, takiego jak *problem klasyfikacji*. Nie można jej używać dla zadań nienadzorowanych ML, takich jak *klastrowanie*.

----------------------------------------------------------

`--ignore-columns | -I`parametry

Za pomocą tego argumentu można zignorować istniejące kolumny w pliku DataSet, aby nie zostały one załadowane i wykorzystane przez procesy szkoleniowe.

Określ nazwy kolumn, które mają być ignorowane. Użyj "," (przecinek z spacją) lub "" (spacja), aby rozdzielić wiele nazw kolumn. Można używać cudzysłowów dla nazw kolumn zawierających odstępy (np. "zalogowane").

Przykład:

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

`--has-header | -h`logiczna

Określ, czy pliki zestawu danych mają wiersz nagłówka.
Możliwe wartości to:

- `true`
- `false`

Wartość domyślna to `true` Jeśli ten argument nie jest określony przez użytkownika.

Aby można było użyć `--label-column-name` argumentu, musisz mieć nagłówek w pliku DataSet i `--has-header` ustawić na `true` (domyślnie).

----------------------------------------------------------

`--max-exploration-time | -x`parametry

Domyślnie maksymalny czas eksploracji to 30 minut.

Ten argument ustawia maksymalny czas (w sekundach), przez który proces ma eksplorować wiele instruktorów i konfiguracji. Skonfigurowany czas może zostać przekroczony, jeśli podany czas jest zbyt krótki (wypowiedz 2 sekundy) dla jednej iteracji. W takim przypadku rzeczywisty czas to wymagany czas na utworzenie jednej konfiguracji modelu w jednej iteracji.

Czas trwania iteracji może się różnić w zależności od rozmiaru zestawu danych.

----------------------------------------------------------

`--cache | -c`parametry

W przypadku korzystania z buforowania cały zestaw danych szkoleniowych zostanie załadowany w pamięci.

W przypadku małych i średnich zestawów danych użycie pamięci podręcznej może znacząco poprawić wydajność uczenia, co oznacza, że czas uczenia może być krótszy niż w przypadku braku użycia pamięci podręcznej.

Jednak w przypadku dużych zestawów danych ładowanie wszystkich znajdujących się w pamięci może wpływać negatywnie na brak pamięci. W przypadku szkolenia z plikami z dużymi zestawami danych, które nie używają pamięci podręcznej, ML.NET będzie przesyłać strumieniowo fragmenty danych z dysku, gdy będzie konieczne załadowanie większej ilości danych podczas uczenia się.

Można określić następujące wartości:

`on`: Wymusza użycie pamięci podręcznej do uczenia się.
`off`: Wymusza użycie pamięci podręcznej w przypadku szkolenia.
`auto`: W zależności od heurystyki AutoML pamięć podręczna zostanie użyta. Zazwyczaj małe i średnie zestawy danych będą używać pamięci podręcznej, a duże zestawy danych nie będą używać pamięci `auto` podręcznej, jeśli zostanie użyty wybór.

Jeśli `--cache` parametr nie zostanie określony, domyślnie zostanie użyta `auto` konfiguracja pamięci podręcznej.

----------------------------------------------------------

`--name | -N`parametry

Nazwa utworzonego projektu lub rozwiązania wyjściowego. Jeśli nazwa nie zostanie określona, zostanie użyta nazwa `sample-{mltask}` .

Plik modelu ML.NET (. Plik ZIP) będzie mieć taką samą nazwę, jak również.

----------------------------------------------------------

`--output-path | -o`parametry

Główna lokalizacja/folder, w którym mają zostać umieszczone wygenerowane dane wyjściowe. Ustawieniem domyślnym jest bieżący katalog.

----------------------------------------------------------

`--verbosity | -V`parametry

Ustawia poziom szczegółowości danych wyjściowych Standard.

Dozwolone wartości to:

- `q[uiet]`
- `m[inimal]`(domyślnie)
- `diag[nostic]`(poziom informacji rejestrowania)

Domyślnie narzędzie interfejsu wiersza polecenia powinno pokazać pewną minimalną opinię (minimalną) podczas pracy, na przykład wzmiankę o tym, że działa, a jeśli to możliwe, ile czasu pozostało lub jaki procent czasu jest zakończony.

----------------------------------------------------------

`-h|--help`

Drukuje pomoc dla polecenia z opisem dla każdego parametru polecenia.

----------------------------------------------------------

## <a name="see-also"></a>Zobacz także

- [Jak zainstalować narzędzie interfejsu wiersza polecenia ML.NET](../how-to-guides/install-ml-net-cli.md)
- [Automatyzacja szkoleń modeli przy użyciu interfejsu wiersza polecenia ML.NET](../automate-training-with-cli.md)
- [Samouczek: Automatycznie Generuj klasyfikator binarny przy użyciu interfejsu wiersza polecenia ML.NET](../tutorials/mlnet-cli.md)
- [Dane telemetryczne w interfejsie wiersza polecenia ML.NET](../resources/ml-net-cli-telemetry.md)

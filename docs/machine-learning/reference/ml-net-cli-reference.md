---
title: Dokumentacja poleceń interfejsu wiersza polecenia ML.NET
description: Przegląd, przykłady i dokumentacja polecenia autouczenie w narzędziu CLI ML.NET.
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 397f6fda8554024624b3ef630856dc8eca9696b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594546"
---
# <a name="the-mlnet-cli-command-reference"></a>Dokumentacja poleceń interfejsu wiersza polecenia ML.NET

`classification`Polecenia, `regression` , i `recommendation` są głównymi poleceniami udostępnianymi przez narzędzie interfejsu wiersza polecenia ml.NET. Te polecenia umożliwiają generowanie modeli ML.NET dobrych jakości dla modeli klasyfikacji, regresji i rekomendacji przy użyciu funkcji automatycznego uczenia maszynowego (AutoML), a także przykładowy kod w języku C# do uruchamiania/oceny modelu. Ponadto kod C# do uczenia modelu jest generowany na potrzeby badania algorytmu i ustawień modelu.

> [!NOTE]
> Ten temat dotyczy ML.NET interfejsu wiersza polecenia i ML.NET AutoML, które są obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.

## <a name="overview"></a>Omówienie

Przykład użycia: 

```console
mlnet regression --dataset "cars.csv" --label-col price
```

`mlnet`Polecenia ml zadania ( `classification` , `regression` i `recommendation` ) generują następujące zasoby:

- Serializowany model. zip ("najlepszy model") jest gotowy do użycia.
- Kod C# do uruchomienia/oceny, który wygenerował model.
- Kod C# z kodem szkoleniowym używanym do generowania tego modelu.

Pierwsze dwa elementy zawartości mogą być bezpośrednio używane w aplikacjach użytkowników końcowych (ASP.NET Core aplikacji sieci Web, usług, aplikacji klasycznych i innych) do prognozowania modelu.

Trzeci element zawartości, kod szkoleniowy, pokazuje, w jaki sposób kod interfejsu API ML.NET był używany przez interfejs wiersza polecenia do uczenia wygenerowanego modelu, aby można było zbadać określony algorytm i ustawienia modelu.

## <a name="examples"></a>Przykłady

Najprostszym poleceniem interfejsu wiersza polecenia dla problemu klasyfikacji (AutoML wnioskuje większość konfiguracji z dostarczonych danych):

```console
mlnet classification --dataset "customer-feedback.tsv" --label-col Sentiment
```

Inne proste polecenie interfejsu wiersza polecenia dla problemu z regresją:

``` console
mlnet regression --dataset "cars.csv" --label-col Price
```

Tworzenie i uczenie modelu klasyfikacji z zestawem danych, testowym zestawem danych i dodatkowymi argumentami dostosowania:

```console
mlnet classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-col "InsuranceRisk" --cache on --train-time 600
```

## <a name="command-options"></a>Opcje polecenia

`mlnet`Polecenia ml zadania ( `classification` , `regression` i `recommendation` ) szkolą wiele modeli na podstawie dostarczonego zestawu danych i opcji interfejsu wiersza polecenia ml.NET. Te polecenia umożliwiają również wybranie najlepszego modelu, zapisanie modelu jako serializowanego pliku zip i wygenerowanie powiązanego kodu w języku C# na potrzeby oceniania i uczenia.

### <a name="classification-options"></a>Opcje klasyfikacji

Uruchomienie `mlnet classification` będzie szkolić model klasyfikacji. Wybierz to polecenie, jeśli chcesz, aby model ML miał kategoryzację danych do dwóch lub więcej klas (np. analizy tonacji).

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="regression-options"></a>Opcje regresji

Uruchomienie `mlnet regression` będzie szkolić model regresji. Wybierz to polecenie, jeśli chcesz, aby model ML przewidział wartość liczbową (np. prognozowanie cen).

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="recommendation-options"></a>Opcje rekomendacji

Uruchomienie `mlnet recommendation` będzie szkolić model rekomendacji.  Wybierz to polecenie, jeśli chcesz, aby model ML polecał elementy użytkownikom na podstawie klasyfikacji (np. zalecenia dotyczące produktu).

```console
mlnet classification

--dataset <path> (REQUIRED)

--item-col <col> (REQUIRED)

--rating-col <col> (REQUIRED)

--user-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

Nieprawidłowe Opcje wejściowe powodują, że narzędzie interfejsu wiersza polecenia emituje listę prawidłowych danych wejściowych i komunikat o błędzie.

## <a name="dataset"></a>Dataset

`--dataset | -d`parametry

Ten argument zawiera jedną z następujących opcji:

- Odp *.: plik całego zestawu danych:* W przypadku korzystania z tej opcji, a użytkownik nie zapewnia `--test-dataset` i `--validation-dataset` , a następnie do walidacji modelu są używane wewnętrzne metody sprawdzania poprawności (z podziałem, itp.) lub zautomatyzowanego podziału danych. W takim przypadku użytkownik będzie musiał tylko podać ścieżkę zestawu danych.

- *B: plik zestawu danych szkoleniowych:* Jeśli użytkownik udostępnia również zestawy danych do walidacji modelu (za pomocą `--test-dataset` i opcjonalnie `--validation-dataset` ), `--dataset` argument oznacza, aby miał jedynie "zestaw danych szkoleniowych". Na przykład w przypadku korzystania z 80%-20% podejścia do weryfikowania jakości modelu i uzyskiwania metryk dokładności, "zestaw danych szkoleniowych" będzie miał 80% danych, a "testowy zestaw danych" miałby 20% danych.

## <a name="test-dataset"></a>Testowy zestaw danych

`--test-dataset | -t`parametry

Ścieżka pliku wskazująca plik zestawu danych testowych, na przykład w przypadku korzystania z 80%-20% podejścia podczas regularnego sprawdzania poprawności w celu uzyskania metryk dokładności.

Jeśli `--test-dataset` jest używana, `--dataset` również jest wymagane.

`--test-dataset`Argument jest opcjonalny, chyba że jest używany element--Validation-DataSet. W takim przypadku użytkownik musi użyć trzech argumentów.

## <a name="validation-dataset"></a>Zestaw danych walidacji

`--validation-dataset | -v`parametry

Ścieżka pliku wskazująca plik zestawu danych walidacji. Zestaw danych walidacji jest opcjonalny w każdym przypadku.

W przypadku korzystania z programu `validation dataset` zachowanie powinno być następujące:

- `test-dataset`Argumenty i `--dataset` są również wymagane.

- Ten `validation-dataset` zestaw danych służy do szacowania błędu prognozowania dla wyboru modelu.

- Służy `test-dataset` do oceny błędu generalizacji końcowego wybranego modelu. Najlepiej, aby zestaw testów był przechowywany w "magazynie" i znajdować się tylko na końcu analizy danych.

W zasadzie, podczas korzystania z znaku `validation dataset` Plus `test dataset` , faza walidacji jest dzielona na dwie części:

1. W pierwszej części Przyjrzyjmy się modelom i wybieramy najlepsze podejście przy użyciu danych sprawdzania poprawności (= Walidacja).
2. Następnie należy oszacować dokładność wybranego podejścia (= test).

W związku z tym rozdzielenie danych może wynosić 80/10/10 lub 75/15/10. Przykład:

- `training-dataset`plik powinien mieć 75% danych.
- `validation-dataset`plik powinien mieć 15% danych.
- `test-dataset`plik powinien mieć 10% danych.

W każdym przypadku te wartości procentowe zostaną określone przez użytkownika przy użyciu interfejsu wiersza polecenia, który udostępni już pliki.

## <a name="label-column"></a>Kolumna etykiety

`--label-col`(int lub String)

Za pomocą tego argumentu określona kolumna celu/Target (zmienna, którą chcesz przewidzieć) można określić za pomocą nazwy kolumny ustawionej w nagłówku zestawu danych lub indeksu liczbowego kolumny w pliku zestawu danych (wartości indeksu kolumn zaczynają się od 0).

Ten argument jest używany w przypadku problemów z *klasyfikacją* i *regresją* .

## <a name="item-column"></a>Kolumna elementu

`--item-col`(int lub String)

Kolumna Item zawiera listę elementów, które użytkownicy klasyfikują (elementy są zalecane dla użytkowników). Tę kolumnę można określić za pomocą nazwy kolumny ustawionej w nagłówku zestawu danych lub indeksu liczbowego kolumny w pliku zestawu danych (wartości indeksu kolumn zaczynają się od 0).

Ten argument jest używany tylko dla zadania *rekomendacji* .

## <a name="rating-column"></a>Kolumna oceny

`--rating-col`(int lub String)

Kolumna Ocena zawiera listę ocen, które są przekazywane do elementów przez użytkowników. Tę kolumnę można określić za pomocą nazwy kolumny ustawionej w nagłówku zestawu danych lub indeksu liczbowego kolumny w pliku zestawu danych (wartości indeksu kolumn zaczynają się od 0).

Ten argument jest używany tylko dla zadania *rekomendacji* .

## <a name="user-column"></a>Kolumna użytkownika

`--user-col`(int lub String)

Kolumna użytkownik zawiera listę użytkowników, którzy dają klasyfikację do elementów. Tę kolumnę można określić za pomocą nazwy kolumny ustawionej w nagłówku zestawu danych lub indeksu liczbowego kolumny w pliku zestawu danych (wartości indeksu kolumn zaczynają się od 0).

Ten argument jest używany tylko dla zadania *rekomendacji* .

## <a name="ignore-columns"></a>Ignoruj kolumny

`--ignore-columns`parametry

Za pomocą tego argumentu można zignorować istniejące kolumny w pliku DataSet, aby nie zostały one załadowane i wykorzystane przez procesy szkoleniowe.

Określ nazwy kolumn, które mają być ignorowane. Użyj "," (przecinek z spacją) lub "" (spacja), aby rozdzielić wiele nazw kolumn. Można używać cudzysłowów dla nazw kolumn zawierających odstępy (np. "zalogowane").

Przykład:

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a>Ma nagłówek

`--has-header`logiczna

Określ, czy pliki zestawu danych mają wiersz nagłówka.
Możliwe wartości:

- `true`
- `false`

Interfejs wiersza polecenia ML.NET podejmie próbę wykrycia tej właściwości, jeśli ten argument nie zostanie określony przez użytkownika.

## <a name="train-time"></a>Czas uczenia

`--train-time`parametry

Domyślnie maksymalny czas eksploracji/uczenia to 30 minut.

Ten argument ustawia maksymalny czas (w sekundach), przez który proces ma eksplorować wiele instruktorów i konfiguracji. Skonfigurowany czas może zostać przekroczony, jeśli podany czas jest zbyt krótki (wypowiedz 2 sekundy) dla jednej iteracji. W takim przypadku rzeczywisty czas to wymagany czas na utworzenie jednej konfiguracji modelu w jednej iteracji.

Czas trwania iteracji może się różnić w zależności od rozmiaru zestawu danych.

## <a name="cache"></a>Pamięć podręczna

`--cache`parametry

W przypadku korzystania z buforowania cały zestaw danych szkoleniowych zostanie załadowany w pamięci.

W przypadku małych i średnich zestawów danych użycie pamięci podręcznej może znacząco poprawić wydajność uczenia, co oznacza, że czas uczenia może być krótszy niż w przypadku braku użycia pamięci podręcznej.

Jednak w przypadku dużych zestawów danych ładowanie wszystkich znajdujących się w pamięci może wpływać negatywnie na brak pamięci. W przypadku szkolenia z plikami z dużymi zestawami danych, które nie używają pamięci podręcznej, ML.NET będzie przesyłać strumieniowo fragmenty danych z dysku, gdy będzie konieczne załadowanie większej ilości danych podczas uczenia się.

Można określić następujące wartości:

`on`: Wymusza użycie pamięci podręcznej do uczenia się.
`off`: Wymusza użycie pamięci podręcznej w przypadku szkolenia.
`auto`: W zależności od AutoML heurystyki, pamięć podręczna zostanie użyta. Zazwyczaj małe i średnie zestawy danych będą używać pamięci podręcznej, a duże zestawy danych nie będą używać pamięci podręcznej, jeśli zostanie użyty `auto` wybór.

Jeśli parametr nie zostanie określony `--cache` , `auto` domyślnie zostanie użyta konfiguracja pamięci podręcznej.

## <a name="name"></a>Nazwa

`--name`parametry

Nazwa utworzonego projektu lub rozwiązania wyjściowego. Jeśli nazwa nie zostanie określona, `sample-{mltask}` zostanie użyta nazwa.

Plik modelu ML.NET (. Plik ZIP) będzie mieć taką samą nazwę, jak również.

## <a name="output-path"></a>Ścieżka wyjściowa

`--output-path | -o`parametry

Główna lokalizacja/folder, w którym mają zostać umieszczone wygenerowane dane wyjściowe. Ustawieniem domyślnym jest bieżący katalog.

## <a name="verbosity"></a>Szczegółowość

`--verbosity | -v`parametry

Ustawia poziom szczegółowości danych wyjściowych Standard.

Dozwolone wartości to:

- `q[uiet]`
- `m[inimal]`(domyślnie)
- `diag[nostic]`(poziom informacji rejestrowania)

Domyślnie narzędzie interfejsu wiersza polecenia powinno pokazać pewną minimalną opinię ( `minimal` ) podczas pracy, na przykład wzmiankę o tym, że działa, a jeśli to możliwe, ile czasu pozostało lub jaki procent czasu jest zakończony.

## <a name="help"></a>Pomoc

`-h |--help`

Drukuje pomoc dla polecenia z opisem dla każdego parametru polecenia.

## <a name="see-also"></a>Zobacz też

- [Jak zainstalować narzędzie interfejsu wiersza polecenia ML.NET](../how-to-guides/install-ml-net-cli.md)
- [Przegląd interfejsu wiersza polecenia ML.NET](../automate-training-with-cli.md)
- [Samouczek: analizowanie tonacji przy użyciu interfejsu wiersza polecenia ML.NET](../tutorials/sentiment-analysis-cli.md)
- [Dane telemetryczne w interfejsie wiersza polecenia ML.NET](../resources/ml-net-cli-telemetry.md)

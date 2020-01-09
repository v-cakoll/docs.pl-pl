---
title: Dokumentacja poleceń interfejsu wiersza polecenia ML.NET
description: Przegląd, przykłady i dokumentacja polecenia autouczenie w narzędziu CLI ML.NET.
ms.date: 12/18/2019
ms.openlocfilehash: 5e59eba91721b26622360818a73adb07a654dc28
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636123"
---
# <a name="the-mlnet-cli-command-reference"></a>Dokumentacja poleceń interfejsu wiersza polecenia ML.NET

Polecenie `auto-train` jest głównym poleceniem udostępnianym przez narzędzie interfejsu wiersza polecenia ML.NET. Polecenie umożliwia wygenerowanie dobrego modelu ML.NET jakości przy użyciu funkcji automatycznego uczenia maszynowego (AutoML) oraz przykładowego C# kodu do uruchomienia/oceny modelu. Ponadto C# kod służący do uczenia modelu jest generowany, aby przeanalizować algorytm i ustawienia modelu.

> [!NOTE]
> Ten temat dotyczy ML.NET interfejsu wiersza polecenia i ML.NET AutoML, które są obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.

## <a name="overview"></a>Omówienie

Przykładowe użycie:

```console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

Polecenie `mlnet auto-train` generuje następujące zasoby:

- Serializowany model. zip ("najlepszy model") jest gotowy do użycia.
- C#kod do uruchomienia/oceny, który wygenerował model.
- C#kod z kodem szkoleniowym używanym do generowania tego modelu.

Pierwsze dwa elementy zawartości mogą być bezpośrednio używane w aplikacjach użytkowników końcowych (ASP.NET Core aplikacji sieci Web, usług, aplikacji klasycznych i innych) do prognozowania modelu.

Trzeci element zawartości, kod szkoleniowy, pokazuje, w jaki sposób kod interfejsu API ML.NET był używany przez interfejs wiersza polecenia do uczenia wygenerowanego modelu, aby można było zbadać określony algorytm i ustawienia modelu.

## <a name="examples"></a>Przykłady

Najprostsze polecenie interfejsu wiersza polecenia dla binarnego problemu klasyfikacji (AutoML wnioskuje większość konfiguracji z dostarczonych danych):

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

Inne proste polecenie interfejsu wiersza polecenia dla problemu z regresją:

``` console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

Tworzenie i uczenie modelu klasyfikacji binarnej z zestawem danych, testowym zestawem danych i dodatkowymi argumentami dostosowania:

```console
mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="command-options"></a>Opcje polecenia

`mlnet auto-train` pociąga za sobą wiele modeli na podstawie podanego zestawu danych, a następnie wybiera najlepszy model, zapisuje go jako serializowany C# plik zip, a następnie generuje powiązany kod na potrzeby oceniania i uczenia.

```console
mlnet auto-train

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

Nieprawidłowe Opcje wejściowe powodują, że narzędzie interfejsu wiersza polecenia emituje listę prawidłowych danych wejściowych i komunikat o błędzie.

## <a name="task"></a>Zadanie

`--task | --mltask | -T` (ciąg)

Pojedynczy ciąg, który umożliwia rozproszenie problemu. Na przykład dowolne z następujących zadań (interfejs wiersza polecenia będzie ostatecznie obsługiwał wszystkie zadania obsługiwane w AutoML):

- `regression` — wybierz, czy model ML będzie używany do przewidywania wartości liczbowej
- `binary-classification` — wybierz, czy wynik modelu ML ma dwie możliwe wartości logiczne kategorii (0 lub 1).
- `multiclass-classification` — wybierz, czy wynik modelu ML ma wiele możliwych wartości kategorii.

W tym argumencie należy podać tylko jedno zadanie ML.

## <a name="dataset"></a>Zestaw danych

`--dataset | -d` (ciąg)

Ten argument zawiera jedną z następujących opcji:

- Odp *.: plik całego zestawu danych:* W przypadku korzystania z tej opcji, gdy użytkownik nie dostarcza `--test-dataset` i `--validation-dataset`, do walidacji modelu są używane wewnętrznie Walidacja (k-zgięcie itp.) lub zautomatyzowane podejścia do podziału danych. W takim przypadku użytkownik będzie musiał tylko podać ścieżkę zestawu danych.

- *B: plik zestawu danych szkoleniowych:* Jeśli użytkownik udostępnia również zestawy danych do walidacji modelu (przy użyciu `--test-dataset` i opcjonalnie `--validation-dataset`), wówczas argument `--dataset` oznacza tylko zestaw danych szkoleniowych. Na przykład w przypadku korzystania z 80%-20% podejścia do weryfikowania jakości modelu i uzyskiwania metryk dokładności, "zestaw danych szkoleniowych" będzie miał 80% danych, a "testowy zestaw danych" miałby 20% danych.

## <a name="test-dataset"></a>Testowy zestaw danych

`--test-dataset | -t` (ciąg)

Ścieżka pliku wskazująca plik zestawu danych testowych, na przykład w przypadku korzystania z 80%-20% podejścia podczas regularnego sprawdzania poprawności w celu uzyskania metryk dokładności.

W przypadku używania `--test-dataset`, `--dataset` jest również wymagany.

Argument `--test-dataset` jest opcjonalny, chyba że jest używany element--Validation-DataSet. W takim przypadku użytkownik musi użyć trzech argumentów.

## <a name="validation-dataset"></a>Sprawdzanie poprawności zestawu danych

`--validation-dataset | -v` (ciąg)

Ścieżka pliku wskazująca plik zestawu danych walidacji. Zestaw danych walidacji jest opcjonalny w każdym przypadku.

W przypadku używania `validation dataset`zachowanie powinno być następujące:

- Argumenty `test-dataset` i `--dataset` są również wymagane.

- `validation-dataset` DataSet służy do szacowania błędu prognozowania dla wyboru modelu.

- `test-dataset` służy do oceny błędu generalizacji końcowego wybranego modelu. Najlepiej, aby zestaw testów był przechowywany w "magazynie" i znajdować się tylko na końcu analizy danych.

W zasadzie, w przypadku używania `validation dataset` i `test dataset`, faza weryfikacji jest dzielona na dwie części:

1. W pierwszej części Przyjrzyjmy się modelom i wybieramy najlepsze podejście przy użyciu danych sprawdzania poprawności (= Walidacja).
2. Następnie należy oszacować dokładność wybranego podejścia (= test).

W związku z tym rozdzielenie danych może wynosić 80/10/10 lub 75/15/10. Na przykład:

- plik `training-dataset` powinien mieć 75% danych.
- plik `validation-dataset` powinien mieć 15% danych.
- plik `test-dataset` powinien mieć 10% danych.

W każdym przypadku te wartości procentowe zostaną określone przez użytkownika przy użyciu interfejsu wiersza polecenia, który udostępni już pliki.

## <a name="label-column-name"></a>Nazwa kolumny etykiety

`--label-column-name | -n` (ciąg)

W przypadku tego argumentu określona kolumna celu/Target (zmienna, która ma zostać przewidywalna) można określić za pomocą nazwy kolumny ustawionej w nagłówku zestawu danych.

Ten argument jest używany tylko w przypadku zadań nadzorowanych ML, takich jak *problem klasyfikacji*. Nie można jej używać dla zadań nienadzorowanych ML, takich jak *klastrowanie*.

## <a name="label-column-index"></a>Indeks kolumny etykiety

`--label-column-index | -i` (int)

Z tym argumentem określona kolumna celu/Target (zmienna, która ma zostać przewidywalna) może być określana za pomocą indeksu liczbowego kolumny w pliku zestawu danych (wartości indeksu kolumn zaczynają się od 1).

*Uwaga:* Jeśli użytkownik używa również `--label-column-name`, `--label-column-name` jest używany.

Ten argument jest używany tylko dla zadania nadzorowanego ML, takiego jak *problem klasyfikacji*. Nie można jej używać dla zadań nienadzorowanych ML, takich jak *klastrowanie*.

## <a name="ignore-columns"></a>Ignoruj kolumny

`--ignore-columns | -I` (ciąg)

Za pomocą tego argumentu można zignorować istniejące kolumny w pliku DataSet, aby nie zostały one załadowane i wykorzystane przez procesy szkoleniowe.

Określ nazwy kolumn, które mają być ignorowane. Użyj "," (przecinek z spacją) lub "" (spacja), aby rozdzielić wiele nazw kolumn. Można używać cudzysłowów dla nazw kolumn zawierających odstępy (np. "zalogowane").

Przykład:

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a>Ma nagłówek

`--has-header | -h` (bool)

Określ, czy pliki zestawu danych mają wiersz nagłówka.
Możliwe wartości to:

- `true`
- `false`

Wartość domyślna jest `true`, jeśli ten argument nie zostanie określony przez użytkownika.

Aby można było użyć argumentu `--label-column-name`, musisz mieć nagłówek w pliku DataSet i `--has-header` ustawić jako `true` (co jest domyślnie).

## <a name="max-exploration-time"></a>Maksymalny czas eksploracji

`--max-exploration-time | -x` (ciąg)

Domyślnie maksymalny czas eksploracji to 30 minut.

Ten argument ustawia maksymalny czas (w sekundach), przez który proces ma eksplorować wiele instruktorów i konfiguracji. Skonfigurowany czas może zostać przekroczony, jeśli podany czas jest zbyt krótki (wypowiedz 2 sekundy) dla jednej iteracji. W takim przypadku rzeczywisty czas to wymagany czas na utworzenie jednej konfiguracji modelu w jednej iteracji.

Czas trwania iteracji może się różnić w zależności od rozmiaru zestawu danych.

## <a name="cache"></a>Pamięć podręczna

`--cache | -c` (ciąg)

W przypadku korzystania z buforowania cały zestaw danych szkoleniowych zostanie załadowany w pamięci.

W przypadku małych i średnich zestawów danych użycie pamięci podręcznej może znacząco poprawić wydajność uczenia, co oznacza, że czas uczenia może być krótszy niż w przypadku braku użycia pamięci podręcznej.

Jednak w przypadku dużych zestawów danych ładowanie wszystkich znajdujących się w pamięci może wpływać negatywnie na brak pamięci. W przypadku szkolenia z plikami z dużymi zestawami danych, które nie używają pamięci podręcznej, ML.NET będzie przesyłać strumieniowo fragmenty danych z dysku, gdy będzie konieczne załadowanie większej ilości danych podczas uczenia się.

Można określić następujące wartości:

`on`: wymusza użycie pamięci podręcznej do uczenia się.
`off`: wymusza użycie pamięci podręcznej w przypadku szkolenia.
`auto`: w zależności od algorytmów heurystycznych AutoML pamięć podręczna zostanie użyta. Zazwyczaj małe i średnie zestawy danych będą korzystać z pamięci podręcznej i duże zestawy danych nie będą używać pamięci podręcznej, jeśli zostanie użyta opcja `auto`.

Jeśli nie określisz parametru `--cache`, zostanie użyta domyślna konfiguracja `auto` pamięci podręcznej.

## <a name="name"></a>Nazwa

`--name | -N` (ciąg)

Nazwa utworzonego projektu lub rozwiązania wyjściowego. Jeśli nazwa nie zostanie określona, zostanie użyta nazwa `sample-{mltask}`.

Plik modelu ML.NET (. Plik ZIP) będzie mieć taką samą nazwę, jak również.

## <a name="output-path"></a>Ścieżka wyjściowa

`--output-path | -o` (ciąg)

Główna lokalizacja/folder, w którym mają zostać umieszczone wygenerowane dane wyjściowe. Ustawieniem domyślnym jest bieżący katalog.

## <a name="verbosity"></a>Szczegółowość

`--verbosity | -V` (ciąg)

Ustawia poziom szczegółowości danych wyjściowych Standard.

Dozwolone wartości to:

- `q[uiet]`
- `m[inimal]` (domyślnie)
- `diag[nostic]` (poziom informacji rejestrowania)

Domyślnie narzędzie interfejsu wiersza polecenia powinno pokazać pewną minimalną opinię (minimalną) podczas pracy, na przykład wzmiankę o tym, że działa, a jeśli to możliwe, ile czasu pozostało lub jaki procent czasu jest zakończony.

## <a name="help"></a>Pomoc

`-h|--help`

Drukuje pomoc dla polecenia z opisem dla każdego parametru polecenia.

## <a name="see-also"></a>Zobacz także

- [Jak zainstalować narzędzie interfejsu wiersza polecenia ML.NET](../how-to-guides/install-ml-net-cli.md)
- [Przegląd interfejsu wiersza polecenia ML.NET](../automate-training-with-cli.md)
- [Samouczek: analizowanie tonacji przy użyciu interfejsu wiersza polecenia ML.NET](../tutorials/sentiment-analysis-cli.md)
- [Dane telemetryczne w interfejsie wiersza polecenia ML.NET](../resources/ml-net-cli-telemetry.md)

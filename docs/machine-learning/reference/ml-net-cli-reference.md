---
title: Polecenie train automatycznie za pomocą narzędzia interfejsu wiersza polecenia w strukturze ML.NET
description: Omówienie, przykłady i dokumentacja dotycząca poleceń train automatycznie za pomocą narzędzia interfejsu wiersza polecenia w strukturze ML.NET.
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: ce5994f392c492e80676b9e65ce54fe010cf03ab
ms.sourcegitcommit: 90f0bee0e8a416e45c78fa3ad4c91ef00e5228d5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66722599"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a>Polecenie "auto-train" w interfejsie wiersza polecenia w strukturze ML.NET

> [!NOTE]
> W tym temacie odnosi się do interfejsu wiersza polecenia w strukturze ML.NET i strukturze ML.NET AutoML, które są obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.

`auto-train` Polecenie jest polecenie główne udostępniane przez narzędzie interfejsu wiersza polecenia w strukturze ML.NET. Polecenie umożliwia generowanie modelu strukturze ML.NET dobrej jakości (pliku zip Zserializowany model) oraz w przykładzie C# kodu w celu uruchomienia/wynik tego modelu. Ponadto C# kod, aby utworzyć/szkolenie modelu zostanie również wygenerowany się dowiedzieć, jakie algorytmu i korzysta z tego ustawienia wygenerowany "najlepiej modelu".

Te zasoby można wygenerować z własne zestawy danych, bez kodowania przez siebie, więc również zwiększa wydajność pracy nawet wtedy, gdy znasz już strukturze ML.NET.

Obecnie są obsługiwane przez interfejs wiersza polecenia strukturze ML.NET zadania uczenia Maszynowego:

- `binary-classification`
- `multiclass-classification`
- `regression`

- Przyszłość: Inne usługi machine learning zadania, takie jak
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

Przykład użycia w wierszu polecenia:

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

`mlnet auto-train` Polecenie generuje następujące zasoby:

- Zserializowany model plik zip ("najlepszy model") gotowych do użycia.
- C#kod w celu uruchomienia/wynik, który jest generowany modelu (w celu prognozowania w aplikacji użytkownika końcowego za pomocą modelu).
- C#kod z kodem szkolenia, używany do generowania modelu (Learning celów).

Pierwsze dwa zasoby bezpośrednio można w aplikacjach użytkownika końcowego (aplikacji internetowej ASP.NET Core, usług, aplikacji klasycznej, itp.), tworzyć prognozy przy użyciu wygenerowanego modelu uczenia Maszynowego.

Trzeci zasobu, kod szkolenia, dowiesz się, jaki kod interfejsu API w strukturze ML.NET był używany przez interfejs wiersza polecenia do trenowania wygenerowane, dzięki czemu możesz zbadać, jakie określonego trainer/algorytmu i wybrano hyper paramenters interfejsu wiersza polecenia, a aparat AutoML strukturze ML.NET.

## <a name="the-auto-train-command-uses-the-automl-engine"></a>Polecenie "auto-train" używa aparatu AutoML

Interfejs wiersza polecenia używa aparatu AutoML strukturze ML.NET (pakiet NuGet) inteligentne wyszukiwanie najlepsze modeli jakości, jak pokazano na poniższym diagramie:

![obraz](./media/ml-net-automl-working-diagram.png "aparatu AutoML pracującym w strukturze ML.NET interfejsu wiersza polecenia")

Podczas uruchamiania narzędzia interfejsu wiersza polecenia w strukturze ML.NET z "auto-train polecenia zostaną wyświetlone narzędzie podjęcie próby liczby iteracji przy użyciu różnych algorytmów i kombinacji konfiguracji.

## <a name="reference-for-auto-train-command"></a>Dokumentacja dotycząca poleceń "auto-train"

## <a name="examples"></a>Przykłady

Najprostsza interfejsu wiersza polecenia dla problemu klasyfikacji binarnej (AutoML będą musieli wywnioskować większość konfiguracji na podstawie podanych danych):

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

Inny prosty polecenia interfejsu wiersza polecenia dla problem regresji:

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

Utwórz i wytrenuj model klasyfikacji danych binarnych z train zestawu danych, zestawy danych testowych i dalsze dostosowanie jawnych argumentów:

```console
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="name"></a>Nazwa

`mlnet auto-train` — Szkolenie modeli wielu modeli ("n" iteracji) na podstawie podanego zestawu danych, a na koniec wybiera najlepszy model, zapisuje go jako plik .zip serializacji, oraz generuje związane z C# kodu ocenianie i szkolenie.

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

Nieprawidłowe opcje danych wejściowych powinna spowodować, że narzędzie interfejsu wiersza polecenia emitować listę prawidłowych danych wejściowych i komunikat o błędzie wyjaśniający arg, który nie istnieje, jeśli tak jest rzeczywiście.

## <a name="options"></a>Opcje

 ----------------------------------------------------------

`--task | --mltask | -T` (string)

Pojedynczy ciąg dostarczający problemu uczenia Maszynowego do rozwiązania. Na przykład dowolny z następujących czynności (interfejs wiersza polecenia po pewnym czasie będzie obsługiwać wszystkie zadania obsługiwane w AutoML):

- `regression` — Wybierz, jeśli Model usługi uczenie Maszynowe będzie służyć do przewidywania wartości liczbowej
- `binary-classification` — Wybierz, czy wynik modelu usługi uczenie Maszynowe ma dwa możliwe podzielonych na kategorie wartości logiczne (0 lub 1).
- `multiclass-classification` — Wybierz, czy wynik modelu usługi uczenie Maszynowe ma wiele możliwych wartości podzielonych na kategorie.

W przyszłości zwalnia takich jak na dodatkowe zadania uczenia Maszynowego i scenariuszy `recommendations`, `clustering` i `ranking` będą obsługiwane.

 Tylko jeden ML zadań należy podać ten argument.

 ----------------------------------------------------------

`--dataset | -d` (string)

Ten argument zawiera ścieżkę pliku do jednego z następujących opcji:

- *ODP.: Plik całego zestawu danych:* Jeśli przy użyciu tej opcji i użytkownik nie dostarcza `--test-dataset` i `--validation-dataset`, a następnie krzyżowego sprawdzania poprawności (k zwijania itp.) lub dane podejście split będzie używana wewnętrznie do sprawdzania poprawności modelu. W takim przypadku użytkownik po prostu należy podać ścieżkę pliku zestawu danych.

- *B: Plik zestawu danych szkolenia:* Jeśli użytkownik udostępnia także zestawy danych do sprawdzania poprawności modelu (przy użyciu `--test-dataset` i opcjonalnie `--validation-dataset`), a następnie `--dataset` argument oznacza, że tylko mają "zestaw danych szkoleniowych". Na przykład korzystając z podejścia 80 – 20% do sprawdzania jakości modelu i uzyskać metryki dokładności, "zestaw danych szkoleniowych" będzie mieć 80% danych, a "zestawu danych testowych" miałyby 20% rozmiaru danych.

----------------------------------------------------------

`--test-dataset | -t` (string)

Ścieżka do pliku, który wskazuje plik zestawu danych testowych, na przykład korzystając z podejścia 80 – 20% podczas wprowadzania ocen regularnym uzyskać metryki dokładności.

Jeśli przy użyciu `--test-dataset`, następnie `--dataset` jest również wymagany.

`--test-dataset` Argument jest opcjonalny Jeśli użycia zestawu danych walidacji. W takim przypadku użytkownik musi użyć trzy argumenty.

----------------------------------------------------------

`--validation-dataset | -v` (string)

Ścieżka do pliku, który wskazuje plik zestawu danych walidacji. Sprawdzanie poprawności zestawu danych jest opcjonalna, w każdym przypadku.

Jeśli przy użyciu `validation dataset`, działanie powinno być:

- `test-dataset` i `--dataset` wymagane są również argumentów.

- `validation-dataset` Zestawu danych jest używany do oszacowania błędów prognoz dla modelu zaznaczenia.

- `test-dataset` Jest używana do oceny błąd Generalizacja końcowa wybranego modelu. W idealnym przypadku zestawu testowego powinny być przechowywane w "Magazyn" i można przełączyć tylko na końcu analizy danych.

Zasadniczo korzystając z `validation dataset` plus `test dataset`, fazę weryfikacja zostanie podzielona na dwie części:

1. W pierwszej części właśnie Przyjrzyj się do modeli i wybierz opcję najlepiej podejście przy użyciu danych sprawdzania poprawności (= weryfikacji)
2. Następnie można oszacować dokładność wybranej metody (= test).

Dzięki temu oddzielenie danych może być 80/10/10 lub 75/15/10. Na przykład:

- `training-dataset` Plik powinien zawierać 75% danych.
- `validation-dataset` Plik powinien zawierać 15% rozmiaru danych.
- `test-dataset` Plik powinien mieć 10% rozmiaru danych.

W każdym przypadku użytkownika przy użyciu interfejsu wiersza polecenia, który zapewni, że już Podziel pliki o tych wartości procentowe.

----------------------------------------------------------

`--label-column-name | -n` (string)

Dzięki temu argumentowi kolumny określony cel/element docelowy (zmiennej, którą chcesz przewidzieć) można określić przy użyciu nazwy kolumny w nagłówku typizowanego zestawu danych.

Ten argument jest używany tylko do nadzorowanego uczenia Maszynowego wykonywania zadań, takich jak *problemu klasyfikacji*. Nie można używać dla nienadzorowanych ML zadań takich jak *klastrowania*.

----------------------------------------------------------

`--label-column-index | -i` (int)

Dzięki temu argumentowi kolumny określony cel/element docelowy (zmiennej, którą chcesz przewidzieć) można określić przy użyciu indeksu liczbowego kolumny w pliku zestawu danych (indeks wartości w kolumnach są liczone od 1).

*Uwaga:* Jeśli użytkownik jest również za pomocą `--label-column-name`, `--label-column-name` jest używany.

Ten argument jest używany tylko w przypadku nadzorowanych zadania uczenia Maszynowego, takich jak *problemu klasyfikacji*. Nie można używać dla nienadzorowanych ML zadań takich jak *klastrowania*.

----------------------------------------------------------

`--ignore-columns | -I` (string)

Dzięki temu argumentowi można zignorować istniejących kolumn w pliku zestawu danych, więc nie są ładowane i wykorzystywane przez procesy szkolenia.

Określ nazwy kolumn, które chcesz zignorować. Użyj "," (przecinek ze spacją) lub "" (miejsca), aby oddzielić wiele nazw kolumn. Dla nazwy kolumny zawierające białe znaki (np. "zalogowany"), można użyć cudzysłowów.

Przykład:

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

`--has-header | -h` (wartość logiczna)

Określ, jeśli pliki zestawu danych ma wiersz nagłówka.
Możliwe wartości to:
- `true`
- `false`

Domyślna wartość to `true` Jeśli ten argument nie zostanie określony przez użytkownika.

Aby można było używać `--label-column-name` argument, musisz mieć nagłówka w pliku zestawu danych i `--has-header` równa `true` (która jest domyślnie).

----------------------------------------------------------

`--max-exploration-time | -x` (string)

Domyślnie podczas eksploracji maksymalna to 30 minut.

Ten argument Ustawia maksymalny czas (w sekundach) dla procesu zapoznać się z wielu instruktorów i konfiguracji. Jeśli podany czas jest zbyt krótki (np. 2 sekund) dla jednej iteracji, może zostać przekroczony skonfigurowany czas. W tym przypadku rzeczywistego czasu jest wymagany czas, aby utworzyć jedną konfigurację modelu w jednej iteracji.

Potrzebny czas dla iteracji, może się różnić w zależności od rozmiaru zestawu danych.

----------------------------------------------------------

`--cache | -c` (string)

Korzystając z buforowania, szkolenie całego zestawu danych będzie załadowanych w pamięci.

W przypadku małych i średnich zestawów danych przy użyciu pamięci podręcznej może znacząco zwiększyć wydajność szkolenia, co oznacza, że podczas szkolenia może być krótszy niż w przypadku nie użycia pamięci podręcznej.

Jednak dla dużych zestawów danych, podczas ładowania wszystkie dane w pamięci może wpłynąć na negatywny, ponieważ możesz otrzymać za mało pamięci. Podczas szkolenia z plikami duży zestaw danych i nie używa pamięci podręcznej, strukturze ML.NET będzie można przesyłanie strumieniowe dużych ilości danych z dysku kiedy zachodzi potrzeba załadowanie większej ilości danych podczas szkolenia.

Można określić następujące wartości:

`on`: Pamięć podręczna wymusza, który będzie używany podczas szkolenia.
`off`: Pamięć podręczna wymusza nie powinien być używany podczas szkolenia.
`auto`: W zależności od heurystyki AutoML pamięci podręcznej będą używane, lub nie. Zwykle małe i średnie zestawów danych będzie korzystać z pamięci podręcznej i dużych zestawów danych nie używać pamięci podręcznej, jeśli używasz `auto` wybór.

Jeśli nie określisz `--cache` parametru, a następnie pamięci podręcznej `auto` konfiguracja będzie używana domyślnie.

----------------------------------------------------------

`--name | -N` (string)

Nazwa wyjściowego utworzony projekt lub rozwiązanie. Jeśli nie określono nazwy, nazwa `sample-{mltask}` jest używany.

Plik modelu strukturze ML.NET (. Plik ZIP) otrzyma taką samą nazwę, jak również.

----------------------------------------------------------

`--output-path | -o` (string)

Lokalizacja/folder główny do umieszczenia wygenerowanych danych wyjściowych. Ustawieniem domyślnym jest bieżący katalog.

----------------------------------------------------------

`--verbosity | -V` (string)

Ustawia poziom szczegółowości wyjścia standardowego.

Dozwolone wartości to:

- `q[uiet]`
- `m[inimal]`  (domyślnie)
- `diag[nostic]` (poziom rejestrowania informacji)

Domyślnie narzędzie interfejsu wiersza polecenia powinny pokazywać niektóre minimalne opinii (minimalny) podczas pracy, takich jak wymienienie działa i jeśli to możliwe czas, jaki jest po lewej stronie lub zakończeniu jakie % czasu.

----------------------------------------------------------

`-h|--help`

Drukuje pomoc dotyczącą polecenia opis parametru każdego polecenia.

----------------------------------------------------------

## <a name="see-also"></a>Zobacz także

- [Jak zainstalować narzędzie interfejsu wiersza polecenia w strukturze ML.NET](../how-to-guides/install-ml-net-cli.md)
- [Automatyzowanie szkolenie modelu przy użyciu interfejsu wiersza polecenia strukturze ML.NET](../automate-training-with-cli.md)
- [Samouczek: Automatycznie Generuj Klasyfikator binarny przy użyciu interfejsu wiersza polecenia strukturze ML.NET](../tutorials/mlnet-cli.md)
- [Dane telemetryczne w interfejsie wiersza polecenia w strukturze ML.NET](../resources/ml-net-cli-telemetry.md)

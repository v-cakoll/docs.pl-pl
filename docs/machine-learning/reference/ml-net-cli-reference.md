---
title: ML.NET odwołanie do polecenia CLI
description: Przegląd, przykłady i odwołanie do polecenia automatycznego szkolenia w narzędziu ML.NET CLI.
ms.date: 12/18/2019
ms.custom: mlnet-tooling
ms.openlocfilehash: bb161c596a76134876ee2bf0a6229bc551e0dad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78848928"
---
# <a name="the-mlnet-cli-command-reference"></a>Odwołanie do polecenia ML.NET CLI

Polecenie `auto-train` jest poleceniem głównym dostarczonym przez narzędzie ML.NET CLI. Polecenie umożliwia wygenerowanie dobrej jakości modelu ML.NET przy użyciu automatycznego uczenia maszynowego (AutoML), a także przykładowego kodu C#, aby uruchomić/zdobyć ten model. Ponadto kod C# do uczenia modelu jest generowany do badania algorytmu i ustawień modelu.

> [!NOTE]
> Ten temat odnosi się do ML.NET cli i ML.NET AutoML, które są obecnie w wersji zapoznawczej, a materiał może ulec zmianie.

## <a name="overview"></a>Omówienie

Przykład użycia: 

```console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

Polecenie `mlnet auto-train` generuje następujące zasoby:

- Serializowany model .zip ("najlepszy model") gotowy do użycia.
- Kod Języka C# do uruchamiania/oceniania, który wygenerował model.
- Kod języka C# z kodem szkolenia używanym do generowania tego modelu.

Pierwsze dwa zasoby mogą być bezpośrednio używane w aplikacjach użytkowników końcowych (ASP.NET core aplikacji sieci web, usług, aplikacji komputerowej i więcej) do prognozowania z modelem.

Trzeci zasób, kod szkolenia, pokazuje, co ML.NET kod interfejsu API był używany przez interfejs ze swej pozycji do nauczenia wygenerowanego modelu, dzięki czemu można zbadać określony algorytm i ustawienia modelu.

## <a name="examples"></a>Przykłady

Najprostsze polecenie WIERSZA POLECENIA dla problemu z klasyfikacją binarną (AutoML wywnioskować większość konfiguracji z podanych danych):

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

Kolejne proste polecenie WIERSZA POLECENIA dla problemu regresji:

``` console
mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

Tworzenie i szkolenie modelu klasyfikacji binarnej za pomocą zestawu danych pociągu, zestawu danych testowych i dalszych argumentów jawnych dostosowywania:

```console
mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="command-options"></a>Opcje polecenia

`mlnet auto-train`trenuje wiele modeli na podstawie dostarczonego zestawu danych i ostatecznie wybiera najlepszy model, zapisuje go jako serializowany plik .zip oraz generuje powiązany kod C# do oceniania i szkolenia.

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

Nieprawidłowe opcje wprowadzania powodują, że narzędzie CLI emituje listę prawidłowych danych wejściowych i komunikat o błędzie.

## <a name="task"></a>Zadanie

`--task | --mltask | -T`(ciąg)

Pojedynczy ciąg zapewniający problem ml do rozwiązania. Na przykład dowolne z następujących zadań (identyfikator POJ po pewnym czasie będzie obsługiwał wszystkie zadania obsługiwane w programie AutoML):

- `regression`- Zdecyduj, czy model ML będzie używany do przewidywania wartości liczbowej
- `binary-classification`- Zdecydowanie, czy wynik modelu ML ma dwie możliwe kategoryczne wartości logiczne (0 lub 1).
- `multiclass-classification`- Wybierz, czy wynik modelu ML ma wiele możliwych wartości kategorii.

W tym argumencie należy podać tylko jedno zadanie ml.

## <a name="dataset"></a>Dataset

`--dataset | -d`(ciąg)

Ten argument udostępnia ścieżkę pliku do jednej z następujących opcji:

- *O: Cały plik zestawu danych:* Jeśli używasz tej opcji, a `--test-dataset` użytkownik `--validation-dataset`nie jest dostarczanie, a następnie krzyżowego sprawdzania poprawności (k-fold, itp.) lub zautomatyzowane metody podziału danych będą używane wewnętrznie do sprawdzania poprawności modelu. W takim przypadku użytkownik będzie musiał podać ścieżkę pliku zestawu danych.

- *B: Plik zestawu danych szkoleniowych:* Jeśli użytkownik udostępnia również zestawy danych do `--test-dataset` sprawdzania `--validation-dataset`poprawności modelu `--dataset` (przy użyciu i opcjonalnie), argument oznacza tylko "zestaw danych szkoleniowych". Na przykład w przypadku korzystania z 80% - 20% podejście do sprawdzania poprawności jakości modelu i uzyskania metryk dokładności, "zestaw danych szkolenia" będzie miał 80% danych i "test dataset" będzie miał 20% danych.

## <a name="test-dataset"></a>Testowanie zestawu danych

`--test-dataset | -t`(ciąg)

Ścieżka pliku wskazująca plik zestawu danych testowych, na przykład podczas korzystania z podejścia 80% - 20% podczas wykonywania regularnych weryfikacji w celu uzyskania metryk dokładności.

W `--test-dataset`przypadku `--dataset` korzystania , wymagane jest również.

Argument `--test-dataset` jest opcjonalny, chyba że używany jest zestaw danych --validation.The argument is optional, unless the --validation-dataset is used. W takim przypadku użytkownik musi użyć trzech argumentów.

## <a name="validation-dataset"></a>Sprawdzanie poprawności zestawu danych

`--validation-dataset | -v`(ciąg)

Ścieżka pliku wskazująca plik zestawu danych sprawdzania poprawności. W każdym przypadku zestaw danych sprawdzania poprawności jest opcjonalny.

W przypadku `validation dataset`korzystania z , zachowanie powinno być:

- I `test-dataset` `--dataset` argumenty są również wymagane.

- Zestaw `validation-dataset` danych służy do szacowania błędu przewidywania dla wyboru modelu.

- Służy `test-dataset` do oceny błędu uogólnienia ostatecznego wybranego modelu. W idealnym przypadku zestaw testów powinien być przechowywany w "przechowalni" i być wyprowadzony dopiero na końcu analizy danych.

Zasadniczo, w przypadku `validation dataset` korzystania `test dataset`z plus , faza sprawdzania poprawności jest podzielona na dwie części:

1. W pierwszej części wystarczy spojrzeć na swoje modele i wybrać najlepsze podejście wykonywania przy użyciu danych sprawdzania poprawności (=walidacja)
2. Następnie należy oszacować dokładność wybranego podejścia (=test).

W związku z tym oddzielenie danych może być 80/10/10 lub 75/15/10. Przykład:

- `training-dataset`powinien mieć 75% danych.
- `validation-dataset`powinien mieć 15% danych.
- `test-dataset`powinien mieć 10% danych.

W każdym przypadku te wartości procentowe zostaną ustalone przez użytkownika korzystającego z interfejsów firm, który dostarczy pliki już podzielone.

## <a name="label-column-name"></a>Nazwa kolumny etykiety

`--label-column-name | -n`(ciąg)

Za pomocą tego argumentu określony cel/kolumna docelowa (zmienna, którą chcesz przewidzieć) można określić przy użyciu zestawu nazw kolumny w nagłówku zestawu danych.

Ten argument jest używany tylko dla nadzorowanych zadań ml, takich jak *problem klasyfikacji*. Nie można go używać do nienadzorowanych zadań ml, takich jak *klastrowanie*.

## <a name="label-column-index"></a>Indeks kolumny etykiety

`--label-column-index | -i`(int)

Za pomocą tego argumentu określony cel/kolumna docelowa (zmienna, którą chcesz przewidzieć) można określić za pomocą indeksu liczbowego kolumny w pliku zestawu danych (wartości indeksu kolumny zaczynają się od 1).

*Uwaga:* Jeśli użytkownik jest również `--label-column-name`za `--label-column-name` pomocą , jest używany.

Ten argument jest używany tylko dla nadzorowanego zadania ML, takiego jak *problem klasyfikacji*. Nie można go używać do nienadzorowanych zadań ml, takich jak *klastrowanie*.

## <a name="ignore-columns"></a>Ignoruj kolumny

`--ignore-columns | -I`(ciąg)

Za pomocą tego argumentu można zignorować istniejące kolumny w pliku zestawu danych, aby nie były ładowane i używane przez procesy szkoleniowe.

Określ nazwy kolumn, które chcesz zignorować. Użyj ', ' (przecinek z miejscem) lub ' ' (spacja), aby oddzielić wiele nazw kolumn. Można użyć cudzysłowów dla nazw kolumn zawierających białe opacze (np. "zalogowany").

Przykład:

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a>Ma nagłówek

`--has-header | -h`(bool)

Określ, czy pliki zestawu danych mają wiersz nagłówka.
Możliwe wartości:

- `true`
- `false`

Domyślna wartość `true` jest, jeśli ten argument nie jest określony przez użytkownika.

Aby użyć argumentu, `--label-column-name` musisz mieć nagłówek w pliku zestawu `--has-header` danych `true` i ustawić na (co jest domyślnie).

## <a name="max-exploration-time"></a>Maksymalny czas eksploracji

`--max-exploration-time | -x`(ciąg)

Domyślnie maksymalny czas eksploracji wynosi 30 minut.

Ten argument ustawia maksymalny czas (w sekundach) dla procesu do eksplorowania wielu trenerów i konfiguracji. Skonfigurowany czas może zostać przekroczony, jeśli podany czas jest zbyt krótki (powiedzmy 2 sekundy) dla pojedynczej iteracji. W takim przypadku rzeczywisty czas jest wymagany czas do produkcji jednej konfiguracji modelu w pojedynczej iteracji.

Czas potrzebny na iteracje może się różnić w zależności od rozmiaru zestawu danych.

## <a name="cache"></a>Pamięć podręczna

`--cache | -c`(ciąg)

Jeśli używasz buforowania, cały zestaw danych szkolenia zostanie załadowany w pamięci.

W przypadku małych i średnich zestawów danych użycie pamięci podręcznej może drastycznie poprawić wydajność szkolenia, co oznacza, że czas szkolenia może być krótszy niż w przypadku, gdy nie używasz pamięci podręcznej.

Jednak w przypadku dużych zestawów danych ładowanie wszystkich danych w pamięci może mieć negatywny wpływ, ponieważ może się wymknąć z pamięci. Podczas szkolenia z plików dużych zestawów danych i nie przy użyciu pamięci podręcznej, ML.NET będzie przesyłania strumieniowego fragmentów danych z dysku, gdy musi załadować więcej danych podczas szkolenia.

Można określić następujące wartości:

`on`: Wymusza pamięć podręczną, która ma być używana podczas szkolenia.
`off`: Wymusza pamięć podręczną, która nie będzie używana podczas treningu.
`auto`: W zależności od heurystyki AutoML pamięć podręczna będzie używana lub nie. Zazwyczaj małe/średnie zestawy danych będą używać pamięci podręcznej, a duże `auto` zestawy danych nie będą używać pamięci podręcznej, jeśli użyjesz wyboru.

Jeśli nie określisz `--cache` parametru, `auto` konfiguracja pamięci podręcznej będzie używana domyślnie.

## <a name="name"></a>Nazwa

`--name | -N`(ciąg)

Nazwa utworzonego projektu wyjściowego lub rozwiązania. Jeśli nazwa nie jest określona, nazwa `sample-{mltask}` jest używana.

Plik modelu ML.NET (. ZIP) otrzyma również taką samą nazwę.

## <a name="output-path"></a>Ścieżka wyjściowa

`--output-path | -o`(ciąg)

Lokalizacja/folder główny, aby umieścić wygenerowane dane wyjściowe. Ustawieniem domyślnym jest bieżący katalog.

## <a name="verbosity"></a>Szczegółowość

`--verbosity | -V`(ciąg)

Ustawia poziom szczegółowości standardowego wyjścia.

Dozwolone wartości to:

- `q[uiet]`
- `m[inimal]`(domyślnie)
- `diag[nostic]`(poziom informacji o rejestrowaniu)

Domyślnie narzędzie CLI powinno wyświetlać minimalne informacje zwrotne (minimalne) podczas pracy, takie jak wzmianka, że działa i jeśli to możliwe, ile czasu pozostało lub jaki % czasu jest ukończony.

## <a name="help"></a>Pomoc

`-h|--help`

Drukuje pomoc polecenia z opisem parametru każdego polecenia.

## <a name="see-also"></a>Zobacz też

- [Jak zainstalować narzędzie ML.NET CLI](../how-to-guides/install-ml-net-cli.md)
- [Przegląd ML.NET CLI](../automate-training-with-cli.md)
- [Samouczek: Analizowanie tonacji przy użyciu interfejsu ML.NET interfejsu i funkcji interfejsu i analizy](../tutorials/sentiment-analysis-cli.md)
- [Telemetria w ML.NET CLI](../resources/ml-net-cli-telemetry.md)

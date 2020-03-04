---
title: Automatyzacja szkoleń modeli przy użyciu interfejsu wiersza polecenia ML.NET
description: Dowiedz się, jak za pomocą narzędzia interfejsu wiersza polecenia ML.NET automatycznie uczenie najlepszego modelu z wiersza poleceń.
ms.date: 12/17/2019
ms.custom: how-to
ms.openlocfilehash: 9c493b1df0dd326ad2f0a5d1cac0fc11d7cf37e2
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240626"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a>Automatyzacja szkoleń modeli przy użyciu interfejsu wiersza polecenia ML.NET

Interfejs wiersza polecenia ML.NET automatyzuje Generowanie modeli dla deweloperów platformy .NET.

Aby korzystać z interfejsu API ML.NET, (bez interfejsu wiersza polecenia ML.NET AutoML), należy wybrać Trainer (implementację algorytmu uczenia maszynowego dla określonego zadania) i zestaw przekształceń danych (inżynieria funkcji) do zastosowania do danych. Optymalny potok będzie różny dla każdego zestawu danych i wybranie optymalnego algorytmu ze wszystkich opcji zwiększa stopień złożoności. Jeszcze więcej, każdy algorytm ma zestaw parametrów, które mają być dostrojone. W związku z tym możesz spędzać tygodnie i czasami miesiące w optymalizacji modelu uczenia maszynowego, próbując znaleźć najlepsze kombinacje funkcji inżynierii, algorytmy uczenia i parametry.

Interfejs wiersza polecenia ML.NET upraszcza ten proces przy użyciu funkcji automatycznego uczenia maszynowego (AutoML). 

> [!NOTE]
> Ten temat dotyczy ML.NET **interfejsu wiersza polecenia** i ml.NET **AutoML**, które są obecnie dostępne w wersji zapoznawczej, a materiał może ulec zmianie.

## <a name="what-is-the-mlnet-command-line-interface-cli"></a>Co to jest interfejs wiersza polecenia ML.NET (CLI)?

Interfejs wiersza polecenia ML.NET jest [narzędziem platformy .NET Core](../core/tools/global-tools.md). Po zainstalowaniu należy przekazać zadanie uczenia maszynowego i zestaw danych szkoleniowych, a następnie wygenerować model ML.NET, a także C# kod do uruchomienia w celu użycia modelu w aplikacji.

Jak pokazano na poniższej ilustracji, można wygenerować model ML.NET o wysokiej jakości (serializowany model. zip) oraz przykładowy C# kod do uruchomienia/oceny modelu. Ponadto C# kod służący do tworzenia/uczenia modelu jest również generowany, aby można było zbadać algorytm i ustawienia używane dla tego wygenerowanego "najlepszego modelu".

![Image](media/automate-training-with-cli/cli-high-level-process.png "Aparat AutoML pracuje wewnątrz interfejsu wiersza polecenia ML.NET")

Można generować te zasoby z własnych zestawów danych bez konieczności pisania ich przez siebie, dzięki czemu zwiększa się produktywność nawet wtedy, gdy znasz już ML.NET.

Obecnie zadania w ML obsługiwane przez interfejs wiersza polecenia ML.NET są następujące:

- `binary-classification`
- `multiclass-classification`
- `regression`
- Przyszłość: inne zadania uczenia maszynowego, takie jak `recommendation`, `ranking`, `anomaly-detection``clustering`

Przykład użycia:

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![image](media/automate-training-with-cli/cli-model-generation.gif)

Można uruchomić je w taki sam sposób w programie *Windows PowerShell*, * MacOS/Linux bash lub *Windows cmd*. Jednak funkcja automatycznego uzupełniania tabelarycznego (sugestie parametryczne) nie będzie działała w programie *Windows cmd*.

## <a name="output-assets-generated"></a>Wygenerowane zasoby wyjściowe

Polecenie `auto-train` interfejsu wiersza polecenia generuje następujące zasoby w folderze wyjściowym:

- Serializowany model. zip ("najlepszy model") gotowy do użycia do uruchamiania prognoz.
- C#rozwiązanie z:
  - C#kod do uruchomienia/oceny, który wygenerował model (aby dokonać prognoz w aplikacjach użytkowników końcowych przy użyciu tego modelu).
  - C#kod z kodem szkoleniowym użytym do wygenerowania tego modelu (na potrzeby uczenia lub ponownego szkolenia modelu).
- Plik dziennika zawierający informacje o wszystkich iteracjach/odchyleniach, które są oceniane przez wiele algorytmów, łącznie z ich szczegółową konfiguracją/potoku.

Pierwsze dwa zasoby mogą być bezpośrednio używane w aplikacjach użytkowników końcowych (ASP.NET Core aplikacji sieci Web, usług, aplikacji klasycznej itp.) w celu utworzenia prognoz dla tego wygenerowanego modelu ML.

Trzeci element zawartości, kod szkoleniowy, pokazuje, jaki kod interfejsu API ML.NET był używany przez interfejs wiersza polecenia do uczenia wygenerowanego modelu, dzięki czemu można przeszkolić model i zbadać i wykonać iterację określonych Trainer/algorytmów i parametrów, które zostały wybrane przez interfejs wiersza polecenia i AutoML w ramach okładek.

## <a name="understanding-the-quality-of-the-model"></a>Omówienie jakości modelu

Po wygenerowaniu "najlepszego modelu" przy użyciu narzędzia interfejsu wiersza polecenia są wyświetlane metryki jakości (takie jak dokładność i R-kwadrat) odpowiednie dla zażądanego zadania ML.

W tym miejscu są podsumowywane pogrupowane według zadania ML, dzięki czemu można zrozumieć jakość automatycznie generowanego najlepszego modelu.

### <a name="metrics-for-binary-classification-models"></a>Metryki dla binarnych modeli klasyfikacji

Poniżej przedstawiono listę metryk zadań w klasyfikacji binarnej ML dla pierwszych pięciu modeli znalezionych w interfejsie wiersza polecenia:

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

Dokładność jest popularną metryką dla problemów klasyfikacji, jednak dokładność nie zawsze jest najlepszą metryką, aby wybrać najlepszy model, z wyjaśnienia w poniższych odwołaniach. Istnieją przypadki, w których należy oszacować jakość modelu z dodatkowymi metrykami.

Aby eksplorować i zrozumieć metryki, które są danymi wyjściowymi interfejsu wiersza polecenia, zobacz [metryki oceny dla klasyfikacji binarnej](resources/metrics.md#evaluation-metrics-for-binary-classification).

### <a name="metrics-for-multi-class-classification-models"></a>Metryki dla modeli klasyfikacji wieloklasowej

Poniżej przedstawiono listę metryk zadań klasyfikacji wieloklasowych dla pierwszych pięciu modeli znalezionych przez interfejs wiersza polecenia:

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

Aby eksplorować i zrozumieć metryki, które są danymi wyjściowymi interfejsu wiersza polecenia, zobacz [metryki oceny dla klasyfikacji wieloklasowej](resources/metrics.md#evaluation-metrics-for-multi-class-classification).

### <a name="metrics-for-regression-and-recommendation-models"></a>Metryki dla modeli regresji i rekomendacji

Model regresji dopasowuje się do danych, jeśli różnice między obserwowanymi wartościami i wartościami przewidywanymi przez model są małe i nieobciążone. Regresję można ocenić przy użyciu określonych metryk.

Zostanie wyświetlona podobna lista metryk dla najlepiej najlepszych pięciu modeli jakości dostępnych w interfejsie wiersza polecenia. W tym konkretnym przypadku związanego z zadaniem regresji ML:

![image](media/automate-training-with-cli/cli-regression-metrics.png)

Aby eksplorować i zrozumieć metryki, które są danymi wyjściowymi interfejsu wiersza polecenia, zobacz [metryki oceny dla regresji](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).

## <a name="see-also"></a>Zobacz też

- [Jak zainstalować narzędzie interfejsu wiersza polecenia ML.NET](how-to-guides/install-ml-net-cli.md)
- [Samouczek: analizowanie tonacji przy użyciu interfejsu wiersza polecenia ML.NET](tutorials/sentiment-analysis-cli.md)
- [Dokumentacja poleceń interfejsu wiersza polecenia ML.NET](reference/ml-net-cli-reference.md)
- [Dane telemetryczne w interfejsie wiersza polecenia ML.NET](resources/ml-net-cli-telemetry.md)

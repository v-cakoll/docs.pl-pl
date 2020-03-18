---
title: Automatyzacja szkolenia modelu z ML.NET CLI
description: Dowiedz się, jak używać narzędzia ML.NET CLI do automatycznego uczenia najlepszego modelu z wiersza polecenia.
ms.date: 12/17/2019
ms.custom: how-to, mlnet-tooling
ms.openlocfilehash: 3344ed15266503d4d5c7cd9db0a0596f58a904fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185880"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a>Automatyzacja szkolenia modelu z ML.NET CLI

ML.NET CLI automatyzuje generowanie modelu dla deweloperów .NET.

Aby korzystać z ML.NET interfejsu API samodzielnie (bez interfejsu ML.NET interfejsu i interfejsów funkcji automl) należy wybrać trenera (implementacja algorytmu uczenia maszynowego dla określonego zadania) i zestaw przekształceń danych (inżynieria funkcji) do zastosowania do danych. Optymalny potok będzie się różnić dla każdego zestawu danych i wybierając optymalny algorytm ze wszystkich wyborów dodaje do złożoności. Co więcej, każdy algorytm ma zestaw hiperparametrów do dostrojenia. W związku z tym można spędzić tygodnie, a czasem miesiące na optymalizacji modelu uczenia maszynowego próbuje znaleźć najlepsze kombinacje inżynierii funkcji, algorytmów uczenia się i hiperparametrów.

ML.NET CLI upraszcza ten proces przy użyciu automatycznego uczenia maszynowego (AutoML).

> [!NOTE]
> Ten temat odnosi się do ML.NET **CLI** i ML.NET **AutoML**, które są obecnie w wersji zapoznawczej, a materiał może ulec zmianie.

## <a name="what-is-the-mlnet-command-line-interface-cli"></a>Co to jest interfejs wiersza polecenia ML.NET??'em ?

ML.NET CLI jest [narzędziem .NET Core](../core/tools/global-tools.md). Po zainstalowaniu nadać mu zadanie uczenia maszynowego i zestaw danych szkoleniowych i generuje model ML.NET, a także kod C# do uruchomienia w celu użycia modelu w aplikacji.

Jak pokazano na poniższej rysunku, jest proste do generowania wysokiej jakości modelu ML.NET (serializowany model .zip file) oraz przykładowy kod C# do uruchomienia/ocena tego modelu. Ponadto kod C# do tworzenia/uczenia tego modelu jest również generowany, dzięki czemu można badać i itetenować algorytm i ustawienia używane dla tego wygenerowanego "najlepszy model".

![Obrazu](media/automate-training-with-cli/cli-high-level-process.png "Silnik AutoML pracujący wewnątrz ML.NET CLI")

Możesz wygenerować te zasoby z własnych zestawów danych bez samodzielnego kodowania, więc zwiększa to również wydajność, nawet jeśli wiesz, ML.NET.

Obecnie zadania ML obsługiwane przez ML.NET CLI to:

- `binary-classification`
- `multiclass-classification`
- `regression`
- Przyszłość: inne zadania `recommendation`uczenia `ranking` `anomaly-detection`maszynowego, takie jak , ,`clustering`

Przykład użycia:

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![image](media/automate-training-with-cli/cli-model-generation.gif)

Można go uruchomić w ten sam sposób na *Windows PowerShell*, * macOS / Linux bash lub *Windows CMD*. Jednak tabelaryczne automatyczne uzupełnianie (sugestie parametrów) nie będzie działać na *CMD systemu Windows*.

## <a name="output-assets-generated"></a>Wygenerowane aktywa wyjściowe

Polecenie WIERSZA POLECENIA `auto-train` generuje następujące zasoby w folderze wyjściowym:

- Serializowany model .zip ("najlepszy model") gotowy do użycia do uruchamiania prognoz.
- Rozwiązanie C# z:
  - Kod języka C# do uruchamiania/oceniania, który wygenerował model (do prognozowania w aplikacjach użytkownika końcowego z tego modelu).
  - Kod języka C# z kodem szkolenia używanym do generowania tego modelu (do celów uczenia się lub ponownego szkolenia modelu).
- Plik dziennika z informacjami o wszystkich iteracjach/wyciągnięciach po ścieżce w wielu ocenianych algorytmach, w tym o ich szczegółowej konfiguracji/potoku.

Pierwsze dwa zasoby mogą być bezpośrednio używane w aplikacjach użytkownika końcowego (ASP.NET core aplikacji sieci web, usług, aplikacji klasycznej, itp.) do prognozowania z tego wygenerowanego modelu ML.

Trzeci zasób, kod szkolenia, pokazuje, co ML.NET kod interfejsu API został użyty przez interfejs użytkownika do uczenia wygenerowanego modelu, dzięki czemu można ponownie trenować modelu i zbadać i iterować, na których określony trener/algorytm i hiperparametry zostały wybrane przez interfejs ów i automl pod przykrywką.

## <a name="understanding-the-quality-of-the-model"></a>Zrozumienie jakości modelu

Podczas generowania "najlepszego modelu" za pomocą narzędzia CLI zobaczysz metryki jakości (takie jak dokładność i R-Kwadrat) jako odpowiednie dla zadania ml, na które kierujesz reklamy.

Tutaj te metryki są sumowane pogrupowane według zadania ML, dzięki czemu można zrozumieć jakość automatycznie generowanego "najlepszego modelu".

### <a name="metrics-for-binary-classification-models"></a>Metryki dla modeli klasyfikacji binarnej

Poniżej przedstawiono listę metryk zadań ml klasyfikacji binarnej dla pięciu najlepszych modeli znalezionych przez cli:

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

Dokładność jest popularną metryką dla problemów z klasyfikacją, jednak dokładność nie zawsze jest najlepszą metryką, aby wybrać najlepszy model, jak wyjaśniono w poniższych odwołaniach. Istnieją przypadki, w których należy ocenić jakość modelu z dodatkowych metryk.

Aby zbadać i zrozumieć metryki, które są dane wyjściowe przez identyfikator y, zobacz [Metryki oceny dla klasyfikacji binarnej](resources/metrics.md#evaluation-metrics-for-binary-classification).

### <a name="metrics-for-multi-class-classification-models"></a>Metryki dla modeli klasyfikacji wieloklasowej

Poniżej przedstawiono wieloklasową listę metryk zadań ml klasyfikacji dla pięciu najlepszych modeli znalezionych przez wiersz wiersza wiersza:

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

Aby zbadać i zrozumieć metryki, które są dane wyjściowe przez wiersz wiersza wiersza wiersza, zobacz [Metryki oceny dla klasyfikacji wieloklasowej](resources/metrics.md#evaluation-metrics-for-multi-class-classification).

### <a name="metrics-for-regression-and-recommendation-models"></a>Metryki dla modeli regresji i rekomendacji

Model regresji dobrze pasuje do danych, jeśli różnice między obserwowanymi wartościami a przewidywanymi wartościami modelu są małe i bezstronne. Regresja można ocenić za pomocą niektórych metryk.

Zobaczysz podobną listę danych dla najlepszych pięciu modeli jakości znalezionych przez cli. W tym konkretnym przypadku związane z zadaniem regresji ML:

![image](media/automate-training-with-cli/cli-regression-metrics.png)

Aby zbadać i zrozumieć metryki, które są dane wyjściowe przez linie cli, zobacz [Metryki oceny regresji](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation).

## <a name="see-also"></a>Zobacz też

- [Jak zainstalować narzędzie ML.NET CLI](how-to-guides/install-ml-net-cli.md)
- [Samouczek: Analizowanie tonacji przy użyciu interfejsu ML.NET interfejsu i funkcji interfejsu i analizy](tutorials/sentiment-analysis-cli.md)
- [ML.NET odwołanie do polecenia CLI](reference/ml-net-cli-reference.md)
- [Telemetria w ML.NET CLI](resources/ml-net-cli-telemetry.md)

---
title: Automatyzowanie szkolenie modelu przy użyciu interfejsu wiersza polecenia strukturze ML.NET
description: Dowiedz się, jak za pomocą narzędzia interfejsu wiersza polecenia w strukturze ML.NET automatycznie szkolenie najlepszy model z wiersza polecenia.
author: CESARDELATORRE
ms.date: 04/17/2019
ms.custom: how-to
ms.openlocfilehash: e5f75dc70ea5a76951d8698ea9c0d07cb2d4ddec
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663925"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a>Automatyzowanie szkolenie modelu przy użyciu interfejsu wiersza polecenia strukturze ML.NET

Interfejs wiersza polecenia strukturze ML.NET "demokratyzuje" strukturze ML.NET dla deweloperów platformy .NET po strukturze ML.NET uczenia.

Używanie interfejsu API strukturze ML.NET przez siebie, (bez AutoML strukturze ML.NET interfejs wiersza polecenia), musisz wybrać trainer (wykonanie Algorytm uczenia maszynowego, dla określonego zadania), a zbiór przekształceń danych (technicznego opracowywania funkcji) do zastosowania do danych. Optymalne potoku będą się różnić dla każdego zestawu danych, a następnie wybierając optymalnego algorytmu z listy opcji dodaje do złożoności. Dodatkowo każdy algorytm ma zestaw hiperparametrów do dostrajania konfiguracji. Dzięki temu możesz poświęcić tygodni na przygotowaniu i czasami miesięcy na uczenia modelu optymalizacji próby znalezienia najlepsze kombinacji hiperparametrów, technicznego opracowywania funkcji i algorytmów uczenia maszynowego.

Proces ten można zautomatyzować za pomocą strukturze ML.NET interfejsu wiersza polecenia, która implementuje aparatu inteligentne AutoML strukturze ML.NET.

> [!NOTE]
> W tym temacie odnosi się do strukturze ML.NET **interfejsu wiersza polecenia** i strukturze ML.NET **AutoML**, które są obecnie dostępne w wersji zapoznawczej i materiał może ulec zmianie.

## <a name="what-is-the-mlnet-command-line-interface-cli"></a>Co to jest strukturze ML.NET interfejsu wiersza polecenia (CLI)?

Strukturze ML.NET interfejsu wiersza polecenia można uruchomić na dowolnym wiersza polecenia (Windows, Mac lub Linux) do generowania modeli strukturze ML.NET dobrej jakości i kod źródłowy, w oparciu o zestaw danych szkoleniowych.

Jak pokazano na poniższej ilustracji, możesz się łatwo wygenerować model strukturze ML.NET wysokiej jakości (pliku zip Zserializowany model) oraz przykład C# kodu w celu uruchomienia/wynik tego modelu. Ponadto C# kod, aby utworzyć/szkolenie modelu zostanie również wygenerowany, dzięki czemu można zbadać i powtarzanie czynności w algorytmie i ustawień używanych na potrzeby tego wygenerowany "najlepiej modelu".

![obraz](media/automate-training-with-cli/cli-high-level-process.png "aparatu AutoML pracującym w strukturze ML.NET interfejsu wiersza polecenia")

Te zasoby można wygenerować z własne zestawy danych, bez kodowania przez siebie, więc również zwiększa wydajność pracy nawet wtedy, gdy znasz już strukturze ML.NET.

Obecnie są obsługiwane przez interfejs wiersza polecenia strukturze ML.NET zadania uczenia Maszynowego:

- `binary-classification`
- `multiclass-classification`
- `regression`
- Przyszłość: inne usługi machine learning zadań takich jak `recommendation`, `ranking`, `anomaly-detection`, `clustering`

Przykład użycia:

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![obraz](media/automate-training-with-cli/cli-model-generation.gif)

Można go uruchomić taki sam sposób na *programu Windows PowerShell*, * bash systemu macOS/Linux lub *Windows CMD*. Jednak tabelarycznych automatycznego uzupełniania (parametr sugestie) nie będzie działać na *Windows CMD*.

## <a name="output-assets-generated"></a>Zasoby danych wyjściowych wygenerowanych

Interfejs wiersza polecenia `auto-train` polecenie generuje następujące zasoby w folderze danych wyjściowych:

- Zserializowany model plik zip ("najlepszy model") gotowych do użycia dla wykonywania prognoz.
- C#rozwiązanie:
  - C#kod w celu uruchomienia/wynik, który jest generowany modelu (w celu prognozowania w aplikacji użytkownika końcowego za pomocą modelu).
  - C#kod z kodem szkolenia, używany do generowania modelu (w przypadku uczenia celów lub ponownego szkolenia modelu).
- Plik dziennika o informacje o wszystkich iteracji/symulacji w wielu algorytmów oceniane, łącznie z ich szczegółowe konfiguracji/potoku.

Pierwsze dwa zasoby bezpośrednio można w aplikacjach użytkownika końcowego (aplikacji internetowej ASP.NET Core, usług, aplikacji klasycznej, itp.), tworzyć prognozy przy użyciu wygenerowanego modelu uczenia Maszynowego.

Trzeci zasobu, kod szkolenia pokazuje możesz jaki kod interfejsu API w strukturze ML.NET był używany przez interfejs wiersza polecenia do nauczenia modelu wygenerowane, aby można było ponowne szkolenie modelu i zbadaj i iteracji na którym określonego trainer/algorytmu i hiperparametrów wybrano przez interfejs wiersza polecenia i AutoML Dzieje się w tle.

## <a name="understanding-the-quality-of-the-model"></a>Informacje o jakość modelu

Podczas generowania "najlepszy model" za pomocą narzędzia interfejsu wiersza polecenia zostanie wyświetlony metryk jakości (takie jak dokładności i R-kwadrat) zgodnie z potrzebami zadania uczenia Maszynowego, które są obsługiwane.

W tym miejscu zawiera podsumowanie tych metryk, pogrupowane według zadań uczenia Maszynowego, aby umożliwić poznanie jakość usługi auto-generated "najlepszy model".

### <a name="metrics-for-binary-classification-models"></a>Metryki dla modeli klasyfikacji binarnej

Następujące Wyświetla listę metryk klasyfikacji binarnej ML zadań, aby najważniejsze pięć modeli znalezione przez interfejs wiersza polecenia:

![obraz](media/automate-training-with-cli/cli-binary-classification-metrics.png)

Dokładność jest popularnych metryki dla problemów klasyfikacji, jednak dokładności nie zawsze jest najlepszym metrykę, aby wybrać najlepszy model z jak wyjaśniono w odwołaniach poniżej. Istnieją przypadki, w którym należy ocenić jakość modelu za pomocą dodatkowe metryki.

Aby poznać i zrozumieć metryki, które są danymi wyjściowymi interfejsu wiersza polecenia, zobacz [metryki dla klasyfikacji binarnej](resources/metrics.md#metrics-for-binary-classification).

### <a name="metrics-for-multi-class-classification-models"></a>Metryki dla modeli klasyfikacji wieloklasowej

Następujące Wyświetla listę metryk klasyfikacji wieloklasowej ML zadań, aby najważniejsze pięć modeli znalezione przez interfejs wiersza polecenia:

![obraz](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

Aby poznać i zrozumieć metryki, które są danymi wyjściowymi interfejsu wiersza polecenia, zobacz [metryki dla klasyfikacji wieloklasowej](resources/metrics.md#metrics-for-multi-class-classification).

### <a name="metrics-for-regression-models"></a>Metryki dla modele regresji

Model regresji dopasowanie do danych w dobrze, jeśli różnice między obserwacji wartości i wartości prognozowanej modelu są małe i nieobciążonej. Regresja może zostać oceniony przy użyciu określonych metryk.

Zostanie wyświetlona lista podobne metryk dla najlepsze modeli najwyższej jakości pięć znalezione przez interfejs wiersza polecenia. W tym konkretnym przypadku dotyczące regresji zadania uczenia Maszynowego:

![obraz](media/automate-training-with-cli/cli-regression-metrics.png)

Aby poznać i zrozumieć metryki, które są danymi wyjściowymi interfejsu wiersza polecenia, zobacz [metryki dotyczące regresji](resources/metrics.md#metrics-for-regression).

## <a name="see-also"></a>Zobacz także

- [Jak zainstalować narzędzie interfejsu wiersza polecenia w strukturze ML.NET](how-to-guides/install-ml-net-cli.md)
- [Samouczek: Automatycznie Generuj Klasyfikator binarny przy użyciu interfejsu wiersza polecenia strukturze ML.NET](tutorials/mlnet-cli.md)
- [Dokumentacja poleceń interfejsu wiersza polecenia w strukturze ML.NET](reference/ml-net-cli-reference.md)
- [Dane telemetryczne w interfejsie wiersza polecenia w strukturze ML.NET](resources/ml-net-cli-telemetry.md)

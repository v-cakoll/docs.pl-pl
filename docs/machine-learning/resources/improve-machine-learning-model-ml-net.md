---
title: 'Instrukcje: poprawianie dokładności modelu'
description: Dowiedz się, jak poprawić dokładność modelu
ms.date: 04/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc
ms.openlocfilehash: 8f3b283de378a37bfe429688207ea9fb52f9ca7f
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75739576"
---
# <a name="improve-mlnet-model-accuracy"></a>Popraw dokładność modelu ML.NET

Dowiedz się, jak poprawić dokładność modelu.

## <a name="reframe-the-problem"></a>Przeszkieletowanie problemu

Czasami poprawa modelu może nie mieć nic do wykonania z danymi lub technikami używanymi do uczenia modelu. Zamiast tego może być, że prośba o niewłaściwe pytanie. Weź pod uwagę problemy związane z różnymi kątami i wykorzystaniem danych do wyodrębnienia ukrytych wskaźników i ukrytych relacji, aby uściślić pytanie.

## <a name="provide-more-data-samples"></a>Podaj więcej próbek danych

Podobnie jak ludzie, coraz więcej algorytmy szkoleniowe uzyskują, prawdopodobieństwo zwiększenia wydajności. Jednym ze sposobów poprawy wydajności modelu jest zapewnienie większej ilości danych szkoleniowych do algorytmów. Im więcej danych, z których uczy się, tym bardziej mogą one identyfikować.

## <a name="add-context-to-the-data"></a>Dodawanie kontekstu do danych

Znaczenie pojedynczego punktu danych może być trudne do zinterpretowania. Kontekst kompilowania wokół punktów danych ułatwia stosowanie algorytmów, a także lepszych decyzji ekspertów. Na przykład fakt, że siedziba domu ma trzy sypialniamiy, nie jest w stanie właściwym wskazaniem jego ceny. Jeśli jednak dodasz kontekst i teraz wiesz, że znajduje się w okolicy w regionie geomiejskim poza głównym obszarem metropolitalnychu, w którym średni wiek to 38, Przeciętny dochód gospodarstwa domowego to $80 000, a szkoły są w największej 20 percentylu, algorytm ma więcej informacji na podstawie jego decyzje w dniu. Wszystkie te kontekstu można dodać jako dane wejściowe do modelu uczenia maszynowego jako funkcje.

## <a name="use-meaningful-data-and-features"></a>Korzystanie z znaczących danych i funkcji

Mimo że więcej próbek i funkcji danych może pomóc poprawić dokładność modelu, mogą także spowodować zakłócenia, ponieważ nie wszystkie dane i funkcje są istotne. W związku z tym ważne jest, aby zrozumieć, które funkcje są tymi, które mają największe wpływ na decyzje podejmowane przez algorytm. Używanie technik, takich jak ważność funkcji permutacji (PFI), może pomóc w identyfikacji tych funkcji najważniejsze i nie tylko pomóc w wyjaśnieniu modelu, ale także użyć danych wyjściowych jako metody wyboru funkcji, aby zmniejszyć ilość szumów przeprowadzonych do procesu szkoleniowego.

Aby uzyskać więcej informacji o korzystaniu z programu PFI, zobacz [wyjaśnienie modelowania modelu przy użyciu funkcji permutacji](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md).

## <a name="cross-validation"></a>Krzyżowe sprawdzanie poprawności

Wzajemne sprawdzanie poprawności to technika szkoleń i oceny modelu, która dzieli dane na kilka partycji i pociąga za siebie wiele algorytmów na tych partycjach. Ta technika podnosi niezawodność modelu przez wyprowadzenie danych z procesu szkolenia. Oprócz poprawy wydajności niewidocznych obserwacji w środowiskach z ograniczonymi danymi może być skutecznym narzędziem dla modeli szkoleniowych z mniejszym zestawem danych.

Skorzystaj z następującego linku, aby dowiedzieć się, [jak używać sprawdzania krzyżowego w ml.NET](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md)

## <a name="hyperparameter-tuning"></a>Dostrajanie hiperparametrów

Uczenie modeli uczenia maszynowego jest procesem iteracyjnym i badawczym. Na przykład jaka jest Optymalna liczba klastrów podczas uczenia modelu przy użyciu algorytmu K-oznacza? Odpowiedź zależy od wielu czynników, takich jak struktura danych. Znalezienie tego numeru wymaga eksperymentowania z różnymi wartościami dla k, a następnie oceny wydajności w celu określenia, która wartość jest Najlepsza. Sposób dostrajania tych parametrów w celu znalezienia optymalnego modelu jest znany jako dostrajanie parametrów funkcji Hyper-Parameter.

## <a name="choose-a-different-algorithm"></a>Wybierz inny algorytm

Zadania uczenia maszynowego, takie jak regresja i klasyfikacja, zawierają różne implementacje algorytmów. Może tak być w przypadku, gdy problem, który próbujesz rozwiązać, i sposób, w jaki dane są strukturalne, nie mieszczą się w bieżącym algorytmie. W takim przypadku Rozważ użycie innego algorytmu dla zadania, aby sprawdzić, czy uczy się lepiej od danych.

Poniższy link zawiera więcej [wskazówek dotyczących wybranego algorytmu](../how-to-choose-an-ml-net-algorithm.md).

---
title: 'Instrukcje: Poprawa dokładności modelu'
description: Dowiedz się, jak zwiększyć dokładność modelu
ms.date: 04/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc
ms.openlocfilehash: 8f3b283de378a37bfe429688207ea9fb52f9ca7f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75739576"
---
# <a name="improve-mlnet-model-accuracy"></a>Zwiększ ML.NET dokładność modelu

Dowiedz się, jak zwiększyć dokładność modelu.

## <a name="reframe-the-problem"></a>Przeformułuj problem

Czasami ulepszanie modelu może mieć nic wspólnego z danymi lub technikami używanymi do uczenia modelu. Zamiast tego może być tak, że zadaje się niewłaściwe pytanie. Rozważ przyjrzenie się problemowi pod różnymi kątami i wykorzystanie danych do wyodrębnienia ukrytych wskaźników i ukrytych relacji w celu zawężenia pytania.

## <a name="provide-more-data-samples"></a>Podaj więcej próbek danych

Podobnie jak ludzie, im więcej algorytmów szkoleniowych, zwiększa się prawdopodobieństwo lepszej wydajności. Jednym ze sposobów poprawy wydajności modelu jest zapewnienie więcej próbek danych szkoleniowych do algorytmów. Im więcej danych się uczy, tym więcej przypadków jest w stanie poprawnie zidentyfikować.

## <a name="add-context-to-the-data"></a>Dodawanie kontekstu do danych

Znaczenie pojedynczego punktu danych może być trudne do zinterpretowania. Budowanie kontekstu wokół punktów danych pomaga algorytmom, a także ekspertom w dziedzinie lepiej podejmować decyzje. Na przykład fakt, że dom ma trzy sypialnie, nie daje dobrego wskazania jego ceny. Jeśli jednak dodasz kontekst i teraz wiesz, że znajduje się w podmiejskiej dzielnicy poza głównym obszarem metropolitalnym, gdzie średni wiek wynosi 38 lat, średni dochód gospodarstwa domowego wynosi 80 000 USD, a szkoły znajdują się w pierwszej 20 percentylu, a następnie algorytm ma więcej informacji, aby oprzeć swój decyzji w tej sprawie. Cały ten kontekst można dodać jako dane wejściowe do modelu uczenia maszynowego jako funkcje.

## <a name="use-meaningful-data-and-features"></a>Korzystanie z istotnych danych i funkcji

Chociaż więcej próbek danych i funkcji może pomóc zwiększyć dokładność modelu, mogą one również wprowadzić szum, ponieważ nie wszystkie dane i funkcje mają znaczenie. Dlatego ważne jest, aby zrozumieć, które funkcje są te, które najsilniej wpływają na decyzje podejmowane przez algorytm. Przy użyciu technik, takich jak Permutacja Feature Importance (PFI) może pomóc zidentyfikować te istotne funkcje i nie tylko pomóc wyjaśnić model, ale także użyć danych wyjściowych jako metody wyboru funkcji, aby zmniejszyć ilość hałaśliwych funkcji wchodzących w proces szkolenia.

Aby uzyskać więcej informacji na temat korzystania z PFI, zobacz [Przewidywanie modelu przy użyciu znaczenia funkcji permutacji](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md).

## <a name="cross-validation"></a>Krzyżowe sprawdzanie poprawności

Krzyżowa weryfikacja jest techniką oceny szkolenia i modelu, która dzieli dane na kilka partycji i szkoli wiele algorytmów na tych partycjach. Technika ta poprawia niezawodność modelu, przechowując dane z procesu szkolenia. Oprócz poprawy wydajności w niewidocznych obserwacjach, w środowiskach ograniczonych danymi może być skutecznym narzędziem do szkolenia modeli z mniejszym zestawem danych.

Odwiedź poniższy link, aby dowiedzieć [się, jak korzystać z weryfikacji krzyżowej w ML.NET](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md)

## <a name="hyperparameter-tuning"></a>Dostrajanie hiperparametrów

Modele uczenia maszynowego szkolenia jest procesem iteracyjnym i badawczym. Na przykład jaka jest optymalna liczba klastrów podczas szkolenia modelu przy użyciu algorytmu K-Means? Odpowiedź zależy od wielu czynników, takich jak struktura danych. Znalezienie tej liczby wymagałoby eksperymentowania z różnymi wartościami dla k, a następnie oceny wydajności w celu określenia, która wartość jest najlepsza. Praktyka dostrajania tych parametrów w celu znalezienia optymalnego modelu jest znana jako dostrajanie hiperparametrów.

## <a name="choose-a-different-algorithm"></a>Wybierz inny algorytm

Zadania uczenia maszynowego, takie jak regresja i klasyfikacja, zawierają różne implementacje algorytmów. Może się okazać, że problem, który próbujesz rozwiązać, a sposób, w jaki twoje dane są zorganizowane, nie pasuje dobrze do bieżącego algorytmu. W takim przypadku należy rozważyć użycie innego algorytmu dla zadania, aby sprawdzić, czy uczy się lepiej z danych.

Poniższy link zawiera więcej [wskazówek, który algorytm wybrać](../how-to-choose-an-ml-net-algorithm.md).

---
title: 'Instrukcje: Zwiększ dokładność modelu'
description: Dowiedz się, jak zwiększyć dokładność modelu
ms.date: 04/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc
ms.openlocfilehash: 6a2899b81fa165dc1bed759079c1ae8506b983e8
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65066161"
---
# <a name="improve-mlnet-model-accuracy"></a>Zwiększ dokładność modelu strukturze ML.NET

Dowiedz się, jak w celu zwiększenia dokładności modelu. 

## <a name="reframe-the-problem"></a>Reframe problem

Czasami ulepszanie modelu może być nic wspólnego z danymi lub techniki do nauczenia modelu. Zamiast tego po prostu może być niewłaściwy pytanie jest pytany. Należy wziąć pod uwagę spojrzenie na problem pod różnymi kątami i wykorzystywanie danych do wyodrębniania ukrytego wskaźników i ukryte relacje, aby uściślić pytanie.

## <a name="provide-more-data-samples"></a>Podaj więcej przykładów danych

Jak ludzi więcej algorytmy szkolenia uzyskać, prawdopodobieństwo wzrostu wydajności lepiej danych. Jednym ze sposobów poprawy wydajności modelu jest zapewnienie większej liczby próbek danych szkoleniowych do algorytmów. Im więcej danych dowie się, więcej przypadków jest w stanie poprawnie zidentyfikować. 

## <a name="add-context-to-the-data"></a>Dodawanie kontekstu do danych

Znaczenie pojedynczego punktu danych może być trudne do interpretacji. Tworzenie kontekstu wokół punktów danych pomaga algorytmów, a także ekspertów z danej dziedziny lepsze podejmowanie decyzji. Na przykład fakt, że domu ma trzy i nie samodzielnie zapewniają dobrym wskaźnikiem jej miesięczna cena. Jednak jeśli dodać kontekstowego, teraz już wiesz, że jest on podmiejskie otoczenie poza główne obszarze metropolitarnym, gdzie średni wiek to 38 średni dochód gospodarstwa domowego jest $ 80 000 operacji i szkoły są w górny percentyl 20, a następnie algorytm ma więcej informacji na temat podstawowej jego decyzje dotyczące. Wszystkie tego kontekstu może zostać dodana jako dane wejściowe dla modelu usługi machine learning jako funkcje. 

## <a name="use-meaningful-data-and-features"></a>Za pomocą zrozumiałej danych i funkcji

Mimo że liczby próbek danych i funkcji może zwiększyć dokładność modelu, również mogą wprowadzać szumu ponieważ nie wszystkie dane i funkcje mają znaczenie. W związku z tym ważne jest zrozumienie, jakie funkcje są tymi, które najczęściej wykonywane wpływ na decyzje przez algorytm. Przy użyciu technik, takich jak znaczenie funkcji permutacji (PFI) może pomóc w zidentyfikowaniu tych najważniejsze funkcje i nie tylko ułatwia zrozumienie modelu, ale również użyć danych wyjściowych jako metoda wyboru funkcji, aby zmniejszyć ilość funkcje generujące dużo alertów, przechodząc do procesu uczenia. 

Dowiedz się, jak używać PFI w następującej [łącza](../how-to-guides/explain-machine-learning-model-permutation-feature-importance-ml-net.md)

## <a name="cross-validation"></a>krzyżowa Weryfikacja

Krzyżowa Weryfikacja jest szkolenia i model oceny technika, która dzieli dane na wiele partycji, a następnie szkolenie modeli wielu algorytmów na te partycje. Ta technika zwiększa niezawodność modelu, zawierający dane z procesu uczenia. Oprócz poprawianie wydajności niewidzianych uwagi, w środowiskach ograniczonego danych może być skutecznym narzędziem do szkolenia modele z mniejszych zestawu danych.

Skorzystaj z następującego linku, aby dowiedzieć się więcej [sposób użycia krzyżowego sprawdzania poprawności w strukturze ML.NET](../how-to-guides/train-machine-learning-model-cross-validation-ml-net.md)

## <a name="hyperparameter-tuning"></a>do strojenia hiperparametrycznego

Modele uczenia maszynowego szkolenia to proces iteracyjny i poznawczych. Na przykład co to jest optymalną liczbę klastrów, podczas uczenia modelu przy użyciu algorytmu K-średnich? Odpowiedź zależy od wielu czynników, takich jak struktury danych. Znajdowanie, że liczba wymaga eksperymentowania z różnymi wartościami dla k i ocenę wydajności, aby określić, która wartość jest najlepsze. Praktyka dostosowywania tych parametrów można znaleźć optymalne modelu jest określany jako dostrajanie parametrów. 

## <a name="choose-a-different-algorithm"></a>Wybierz innego algorytmu

Zadania uczenia maszynowego, takich jak regresji i klasyfikacji zawierają różne implementacje algorytmu. Może to być problem, który próbujesz rozwiązać i sposób, w jaki dane są skonstruowane nie pasują do algorytmu bieżącego przypadku. W takim przypadku należy wziąć pod uwagę przy użyciu innego algorytmu zadania, aby zobaczyć, jeśli dowie się lepiej z Twoich danych. 

Kliknięcie następującego łącza zawiera więcej [wskazówki, na który algorytm wyboru](../how-to-choose-an-ml-net-algorithm.md). 
 

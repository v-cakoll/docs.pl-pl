---
title: Podsumowanie drzew wyrażeń
description: Ponowne użycie drzew wyrażeń do tworzenia programów dynamicznych, które interpretują kod jako dane i tworzą nowe funkcje na podstawie tego kodu.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 43715c94b70f1cd7f758cde91ae7c8d1b2f70f9f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036755"
---
# <a name="expression-trees-summary"></a>Podsumowanie drzew wyrażeń

[Poprzednie — tłumaczenie wyrażeń](expression-trees-translating.md)

W tej serii pokazano, jak można używać *drzew wyrażeń* do tworzenia programów dynamicznych, które interpretują kod jako dane i tworzą nowe funkcje na podstawie tego kodu.

Można sprawdzić drzewa wyrażeń, aby zrozumieć intencję algorytmu. Nie można przeanalizować tego kodu. Można utworzyć nowe drzewa wyrażeń, które reprezentują zmodyfikowane wersje oryginalnego kodu.

Można również użyć drzew wyrażeń do przyjrzeć się algorytmowi i przetłumaczyć ten algorytm na inny język lub środowisko. 

## <a name="limitations"></a>Ograniczenia

Istnieją pewne nowsze C# elementy języka, które nie są poprawnie tłumaczone na drzewa wyrażeń. Drzewa wyrażeń nie mogą zawierać wyrażeń `await` ani `async` wyrażeń lambda. Wiele funkcji dodanych w C# 6 Release nie pojawia się dokładnie jako zapisywana w drzewach wyrażeń. Zamiast tego nowe funkcje zostaną uwidocznione w drzewach wyrażeń w równoważnej, wcześniejszej składni. Może to nie być tak samo, jak to możliwe. W rzeczywistości oznacza to, że kod, który interpretuje drzewa wyrażeń prawdopodobnie nadal będzie działał tak samo, gdy zostaną wprowadzone nowe funkcje językowe.

Nawet przy tych ograniczeniach drzewa wyrażeń umożliwiają tworzenie algorytmów dynamicznych, które opierają się na interpretowaniu i modyfikowaniu kodu, który jest reprezentowany jako struktura danych. Jest to zaawansowane narzędzie i jest jednym z funkcji ekosystemu .NET, które umożliwiają rozbudowane biblioteki, takie jak Entity Framework, do wykonywania tych czynności.

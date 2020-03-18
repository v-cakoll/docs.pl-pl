---
title: Podsumowanie drzew wyrażeń
description: Recaps jak można użyć drzewa wyrażeń do tworzenia dynamicznych programów, które interpretują kod jako dane i tworzyć nowe funkcje na podstawie tego kodu.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 513244a987e295c81cfb5d00d9a0cfd6912074e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145894"
---
# <a name="expression-trees-summary"></a>Podsumowanie drzew wyrażeń

[Poprzedni -- Tłumaczenie wyrażeń](expression-trees-translating.md)

W tej serii widać, jak można użyć *drzewa wyrażeń* do tworzenia dynamicznych programów, które interpretują kod jako dane i tworzą nowe funkcje na podstawie tego kodu.

Można sprawdzić drzewa wyrażeń, aby zrozumieć intencji algorytmu. Możesz nie tylko sprawdzić ten kod. Można utworzyć nowe drzewa wyrażeń, które reprezentują zmodyfikowane wersje oryginalnego kodu.

Można również użyć drzewa wyrażeń, aby spojrzeć na algorytm i przetłumaczyć ten algorytm na inny język lub środowisko.

## <a name="limitations"></a>Ograniczenia

Istnieje kilka nowszych elementów języka Języka C#, które nie przekładają się dobrze na drzewa wyrażeń. Drzewa wyrażeń nie mogą zawierać `await` wyrażeń ani `async` wyrażeń lambda. Wiele funkcji dodanych w wersji C# 6 nie są wyświetlane dokładnie tak, jak napisane w drzewach wyrażeń. Zamiast tego nowsze funkcje będą widoczne w wyrażeniach drzew w równoważnej, wcześniejszej składni. Może to nie być tak duże ograniczenie, jak mogłoby się wydawać. W rzeczywistości oznacza to, że kod, który interpretuje drzewa wyrażeń prawdopodobnie nadal będzie działać tak samo po wprowadzeniu nowych funkcji języka.

Nawet przy tych ograniczeniach drzewa wyrażeń umożliwiają tworzenie dynamicznych algorytmów, które opierają się na interpretacji i modyfikowaniu kodu, który jest reprezentowany jako struktura danych. Jest to zaawansowane narzędzie i jest to jedna z funkcji ekosystemu .NET, która umożliwia bogatym bibliotekom, takim jak Entity Framework, osiągnięcie tego, co robią.

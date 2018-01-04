---
title: "Podsumowanie drzew wyrażeń"
description: "Recaps, jak używanie drzew wyrażeń do tworzenia dynamicznych programów, które interpretacji kodu jako danych i tworzenie nowych funkcji, na podstawie tego kodu."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: d2754493c782c2550a8b0bd0de274cb8100c78af
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="expression-trees-summary"></a>Podsumowanie drzew wyrażeń

[Poprzednie — Tłumaczenia wyrażenia](expression-trees-translating.md)

W tej serii przedstawiono sposób korzystania *drzew wyrażeń* do tworzenia dynamicznych programów, które interpretacji kodu jako danych i tworzenie nowych funkcji, na podstawie tego kodu.

Można sprawdzić drzew wyrażeń do zrozumienia celem algorytmu. Nie można tylko badanie tego kodu. Można utworzyć nowego drzew wyrażeń, które reprezentują zmodyfikowanej wersji oryginalnego kodu.

Można również używanie drzew wyrażeń do przyjrzeć się algorytm i tłumaczenie tego algorytmu inny język lub środowiska. 

## <a name="limitations"></a>Ograniczenia

Istnieją pewne nowszej C# języka elementy, które nie je łatwo przekształcić w drzewach wyrażeń. Drzewa wyrażeń nie może zawierać `await` wyrażenia, lub `async` wyrażenia lambda. Funkcje dodane w wersji języka C# 6 nie pojawiają się dokładnie, jak podano w drzewach wyrażeń. Zamiast tego nowsze funkcje mają być widoczne w drzewach wyrażeń w składni równorzędną, wcześniej. To nie może być jako część ograniczenia jak się wydaje. W rzeczywistości oznacza to, że swój kod, który interpretuje drzew wyrażeń będzie prawdopodobnie nadal działać w identyczny gdy wprowadzono nowe funkcje języka.

Nawet w przypadku tych ograniczeń drzew wyrażeń umożliwiają tworzenie dynamicznych algorytmy, które opierają się na interpretowanie i modyfikowania kodu, który jest reprezentowany jako struktury danych. Jest zaawansowanym narzędziem i jest jedną z funkcji ekosystemu .NET, który umożliwia sformatowanego biblioteki, takich jak Entity Framework w celu ich działania.


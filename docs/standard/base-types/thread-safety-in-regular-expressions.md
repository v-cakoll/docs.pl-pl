---
title: Bezpieczeństwo wątków w wyrażeniach regularnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
ms.openlocfilehash: db25028e10872cfca08d28518c795414d06c5d49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124799"
---
# <a name="thread-safety-in-regular-expressions"></a>Bezpieczeństwo wątków w wyrażeniach regularnych
Sama <xref:System.Text.RegularExpressions.Regex> klasa jest bezpieczna i niezmienna wątku (tylko do odczytu). Oznacza to, **że Regex** obiekty mogą być tworzone na dowolnym wątku i współużytkowane między wątkami; pasujące metody można wywołać z dowolnego wątku i nigdy nie zmieniać żadnego stanu globalnego.  
  
 Jednak obiekty wynik (**Match** i **MatchCollection**) zwracane przez **Regex** powinny być używane w jednym wątku. Mimo że wiele z tych obiektów są logicznie niezmienne, ich implementacje może opóźnić obliczenia niektórych wyników w celu zwiększenia wydajności, a w rezultacie obiekty wywołujące muszą serializować dostęp do nich.  
  
 Jeśli istnieje potrzeba udostępniania obiektów wyników **Regex** w wielu wątkach, obiekty te można przekonwertować na wystąpienia bezpieczne dla wątków, wywołując ich zsynchronizowane metody. Z wyjątkiem wyliczaczy wszystkie klasy wyrażeń regularnych są bezpieczne dla wątków lub mogą zostać przekształcone w obiekty bezpieczne dla wątków za pomocą metody zsynchronizowanej.  
  
 Wyliczacze są jedynym wyjątkiem. Aplikacja musi serializować wywołania modułów wyliczania kolekcji. Regułą jest, że jeśli kolekcja może być wyliczana na więcej niż jeden wątek jednocześnie, należy zsynchronizować metody wyliczania na obiekt główny kolekcji przechodzenie przez wyliczacza.  
  
## <a name="see-also"></a>Zobacz też

- [Wyrażenia regularne .NET](../../../docs/standard/base-types/regular-expressions.md)

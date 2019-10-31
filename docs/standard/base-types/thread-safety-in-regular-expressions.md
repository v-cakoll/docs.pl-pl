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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124799"
---
# <a name="thread-safety-in-regular-expressions"></a>Bezpieczeństwo wątków w wyrażeniach regularnych
Sama klasa <xref:System.Text.RegularExpressions.Regex> jest bezpieczna wątkowo i niezmienna (tylko do odczytu). Oznacza to, że obiekty **wyrażenia regularnego** można tworzyć w dowolnym wątku i współdzielonym przez wątki. Metody pasujące mogą być wywoływane z dowolnego wątku i nigdy nie zmieniają żadnego stanu globalnego.  
  
 Jednak obiekty wynikowe (**Match** i **MatchCollection**) zwracane przez **wyrażenie regularne** powinny być używane w pojedynczym wątku. Chociaż wiele z tych obiektów jest logicznie niezmienne, ich implementacje mogą opóźniać Obliczanie niektórych wyników w celu zwiększenia wydajności i w związku z tym wywołujący muszą serializować dostęp do nich.  
  
 Jeśli istnieje potrzeba udostępniania obiektów wynikowych **wyrażeń regularnych** w wielu wątkach, te obiekty mogą być konwertowane na wystąpienia z bezpiecznymi wątkami przez wywołanie ich zsynchronizowanych metod. Z wyjątkiem modułów wyliczających wszystkie klasy wyrażeń regularnych są bezpieczne wątkowo lub mogą być konwertowane na obiekty z bezpiecznymi wątkami przez zsynchronizowaną metodę.  
  
 Numeratory są jedynym wyjątkiem. Aplikacja musi serializować wywołania do modułów wyliczających kolekcje. Zasada polega na tym, że jeśli kolekcja może zostać wyliczona jednocześnie w więcej niż jednym wątku, należy synchronizować metody modułu wyliczającego w obiekcie głównym kolekcji przechodzącej przez moduł wyliczający.  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia regularne .NET](../../../docs/standard/base-types/regular-expressions.md)

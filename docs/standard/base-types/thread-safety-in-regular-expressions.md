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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c0bcab0757bc48f6a8216dd5878f0289e49a275
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45507092"
---
# <a name="thread-safety-in-regular-expressions"></a>Bezpieczeństwo wątków w wyrażeniach regularnych
<xref:System.Text.RegularExpressions.Regex> Samej klasy jest wątek, bezpieczne i niezmienne (tylko do odczytu). Oznacza to, że **wyrażenia regularnego** obiekty można tworzyć na żadnym z wątków i udostępniane między wątkami; metod dopasowania mogą być wywoływane z żadnym z wątków i nigdy nie zmienia żadnych stan globalny.  
  
 Jednak obiekty wynikowe (**dopasowanie** i **matchcollection —**) zwróciło **wyrażenia regularnego** powinny być używane w jednym wątku. Chociaż wiele z tych obiektów są logicznie niezmienne, ich implementacji może opóźnić obliczenie niektórych wyników, aby zwiększyć wydajność, a w rezultacie obiekty wywołujące muszą serializację do nich dostęp.  
  
 Jeśli zachodzi potrzeba udostępniania **wyrażenia regularnego** wynik obiektów w wielu wątkach, te obiekty mogą być konwertowane do wystąpień wątków przez wywołanie metody ich zsynchronizowane. Z wyjątkiem moduły wyliczające wszystkie klasy wyrażeń regularnych są bezpieczne dla wątków lub mogą być konwertowane na obiekty wątków przez metodę zsynchronizowane.  
  
 Jedynym wyjątkiem są wyliczenia. Aplikację należy serializować wywołania do kolekcji wyliczenia. Reguła jest, że jeśli kolekcji mogą być wyliczane w więcej niż jeden wątek jednocześnie, należy zsynchronizować modułu wyliczającego metod w głównym obiekcie kolekcji-przenoszone przez moduł wyliczający.  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażeń regularnych programu .NET](../../../docs/standard/base-types/regular-expressions.md)

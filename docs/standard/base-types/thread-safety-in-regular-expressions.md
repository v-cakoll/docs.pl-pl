---
title: "Bezpieczeństwo wątków w wyrażeniach regularnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4cfa24da8083eac01275ad76f5c2db974b39a25
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="thread-safety-in-regular-expressions"></a>Bezpieczeństwo wątków w wyrażeniach regularnych
<xref:System.Text.RegularExpressions.Regex> Samej klasy jest wątku bezpieczne i modyfikować (tylko do odczytu). Oznacza to **Regex** obiektów można tworzyć w którymkolwiek wątku i udostępniane między wątkami; metod może być wywołana z dowolnego wątku i nigdy nie zmienia żadnych stan globalny.  
  
 Jednak obiekty wynikowe (**dopasowania** i **matchcollection —**) zwrócone przez **Regex** powinien być używany w jednym wątku. Mimo że wiele z tych obiektów są logicznie niezmienne, ich implementacji można opóźnić obliczeń pewnych wyników, aby zwiększyć wydajność, a w związku z tym wywołującym musi serializować uzyskiwania do nich dostępu.  
  
 Jeśli trzeba udostępnić **Regex** wynik obiektów na wiele wątków, przez wywołanie jego metody zsynchronizowane można przekonwertować na wątkowo wystąpień tych obiektów. Z wyjątkiem moduły wyliczające wszystkie wyrażenia regularnego klasy są bezpieczne dla wątków lub można przekonwertować na obiekty wątkowo Metoda zsynchronizowana.  
  
 Jedynym wyjątkiem są wyliczenia. Aplikacja musi serializować wywołania wyliczenia kolekcji. Reguła jest, że jeśli kolekcja mogą być wyliczane w więcej niż jeden wątek jednocześnie, należy synchronizować modułu wyliczającego metody do obiektu głównego kolekcji przechodzić przez moduł wyliczający.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażeń regularnych programu .NET](../../../docs/standard/base-types/regular-expressions.md)

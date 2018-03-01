---
title: "remove (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 66647dee0c4cc728ae5e19457a4a5ef0e7f72248
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="remove-c-reference"></a>remove (odwołanie w C#)
`remove` Kontekstowe słowo kluczowe jest używane do definiowania akcesor zdarzenie niestandardowe, które jest wywoływane, gdy kod klienta cofnięć subskrypcji z Twojej [zdarzeń](../../../csharp/language-reference/keywords/event.md). Jeśli podasz niestandardowego `remove` dostępu, należy również podać [dodać](../../../csharp/language-reference/keywords/add.md) metody dostępu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono zdarzenia niestandardowe [dodać](../../../csharp/language-reference/keywords/add.md) i `remove` metody dostępu. Na przykład pełna, zobacz [porady: Implementowanie interfejsu zdarzenia](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/remove_1.cs)]  
  
 Zwykle nie trzeba podać własne niestandardowych metod dostępu zdarzeń. Metody dostępu, które są automatycznie generowane przez kompilator przy deklarowaniu zdarzenia są wystarczające dla większości scenariuszy.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia](../../../csharp/programming-guide/events/index.md)

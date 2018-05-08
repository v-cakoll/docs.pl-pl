---
title: add (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: c1fa8c130475a67ac175205fe3491a32654ea475
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="add-c-reference"></a>add (odwołanie w C#)
`add` Kontekstowe słowo kluczowe jest używane do definiowania akcesor zdarzenie niestandardowe, które jest wywoływane, gdy kod klienta subskrybuje Twojej [zdarzeń](../../../csharp/language-reference/keywords/event.md). Jeśli podasz niestandardowego `add` dostępu, należy również podać [Usuń](../../../csharp/language-reference/keywords/remove.md) metody dostępu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono zdarzenie, które ma niestandardowy `add` i [Usuń](../../../csharp/language-reference/keywords/remove.md) metody dostępu. Na przykład pełna, zobacz [porady: Implementowanie interfejsu zdarzenia](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/add_1.cs)]  
  
 Zwykle nie trzeba podać własne niestandardowych metod dostępu zdarzeń. Metody dostępu, które są automatycznie generowane przez kompilator przy deklarowaniu zdarzenia są wystarczające dla większości scenariuszy.  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia](../../../csharp/programming-guide/events/index.md)

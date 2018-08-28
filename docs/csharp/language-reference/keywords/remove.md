---
title: remove (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: 245ef0a16fd2cec2f36c86dd0ac3b8838a76b02e
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2018
ms.locfileid: "42999774"
---
# <a name="remove-c-reference"></a>remove (odwołanie w C#)
`remove` Kontekstowe słowo kluczowe jest używane do definiowania metody dostępu zdarzeń niestandardowych, które jest wywoływane, gdy kod klienta, który anuluje subskrypcje ze swojej [zdarzeń](../../../csharp/language-reference/keywords/event.md). Jeśli podasz niestandardowe `remove` dostępu, należy również podać [Dodaj](../../../csharp/language-reference/keywords/add.md) metody dostępu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano zdarzenia niestandardowe [Dodaj](../../../csharp/language-reference/keywords/add.md) i `remove` metod dostępu. Aby uzyskać pełny przykład, zobacz [porady: Implementowanie zdarzenia interfejsu](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
 [!code-csharp[csrefKeywordsContextual#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/remove_1.cs)]  
  
 Zazwyczaj nie trzeba podać własne niestandardowych metod dostępu zdarzeń. Metody dostępu, które są automatycznie generowane przez kompilator przy deklarowaniu zdarzenie są wystarczające dla większości scenariuszy.  
  
## <a name="see-also"></a>Zobacz też

- [Zdarzenia](../../../csharp/programming-guide/events/index.md)

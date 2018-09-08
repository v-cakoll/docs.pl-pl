---
title: add (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: b55827b60a89da2569fad9da135c84571a24b094
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201208"
---
# <a name="add-c-reference"></a>add (odwołanie w C#)
`add` Kontekstowe słowo kluczowe jest używane do definiowania metody dostępu zdarzeń niestandardowych, które jest wywoływane, gdy kod klienta subskrybuje Twoja [zdarzeń](../../../csharp/language-reference/keywords/event.md). Jeśli podasz niestandardowe `add` dostępu, należy również podać [Usuń](../../../csharp/language-reference/keywords/remove.md) metody dostępu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia zdarzenie, które zawiera niestandardowy `add` i [Usuń](../../../csharp/language-reference/keywords/remove.md) metod dostępu. Aby uzyskać pełny przykład, zobacz [porady: Implementowanie zdarzenia interfejsu](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Zazwyczaj nie trzeba podać własne niestandardowych metod dostępu zdarzeń. Metody dostępu, które są automatycznie generowane przez kompilator przy deklarowaniu zdarzenie są wystarczające dla większości scenariuszy.  
  
## <a name="see-also"></a>Zobacz też  
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)

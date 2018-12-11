---
title: Dodaj - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 6cc1b504de383ae63284ecb3ac7d0b1b47b36bfe
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244378"
---
# <a name="add-c-reference"></a>add (odwołanie w C#)
`add` Kontekstowe słowo kluczowe jest używane do definiowania metody dostępu zdarzeń niestandardowych, które jest wywoływane, gdy kod klienta subskrybuje Twoja [zdarzeń](../../../csharp/language-reference/keywords/event.md). Jeśli podasz niestandardowe `add` dostępu, należy również podać [Usuń](../../../csharp/language-reference/keywords/remove.md) metody dostępu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia zdarzenie, które zawiera niestandardowy `add` i [Usuń](../../../csharp/language-reference/keywords/remove.md) metod dostępu. Pełny przykład można znaleźć [jak:  Zdarzenia implementowania interfejsu](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Zazwyczaj nie trzeba podać własne niestandardowych metod dostępu zdarzeń. Metody dostępu, które są automatycznie generowane przez kompilator przy deklarowaniu zdarzenie są wystarczające dla większości scenariuszy.  
  
## <a name="see-also"></a>Zobacz też  
- [Zdarzenia](../../../csharp/programming-guide/events/index.md)

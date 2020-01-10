---
title: Dodaj C# odwołanie
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 323064dcbe7596b5f1d2f0f6aa566b07cee45789
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713806"
---
# <a name="add-c-reference"></a>add (odwołanie w C#)
`add` kontekstowe słowo kluczowe jest używane do definiowania niestandardowego akcesora zdarzeń, który jest wywoływany, gdy kod klienta subskrybuje [zdarzenie](./event.md). W przypadku podania niestandardowej metody dostępu `add` należy również podać metodę dostępu [Usuń](./remove.md) .  
  
## <a name="example"></a>Przykład  
Poniższy przykład pokazuje zdarzenie, które ma niestandardowe metody dostępu `add` i [usuwania](./remove.md) . Pełny przykład można znaleźć w temacie [jak zaimplementować zdarzenia interfejsu](../../programming-guide/events/how-to-implement-interface-events.md).
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Zazwyczaj nie trzeba podawać własnych niestandardowych metod dostępu do zdarzeń. Metody dostępu, które są generowane automatycznie przez kompilator podczas deklarowania zdarzenia, są wystarczające dla większości scenariuszy.  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia](../../programming-guide/events/index.md)

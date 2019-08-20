---
title: Dodaj C# odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 1cf82e3d048e465d533e87dc639a13071b41544a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606044"
---
# <a name="add-c-reference"></a>add (odwołanie w C#)
Kontekstowe słowo kluczowe jest używane do definiowania niestandardowego akcesora zdarzeń, który jest wywoływany, gdy kod klienta subskrybuje [zdarzenie.](./event.md) `add` W przypadku podania niestandardowej `add` metody dostępu należy również podać metodę dostępu [Usuń](./remove.md) .  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje zdarzenie, które ma metody dostępu `add` niestandardowe i [usuwania](./remove.md) . Pełny przykład można znaleźć w temacie [How to:  Implementuj zdarzenia](../../programming-guide/events/how-to-implement-interface-events.md)interfejsu.  
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Zazwyczaj nie trzeba podawać własnych niestandardowych metod dostępu do zdarzeń. Metody dostępu, które są generowane automatycznie przez kompilator podczas deklarowania zdarzenia, są wystarczające dla większości scenariuszy.  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia](../../programming-guide/events/index.md)

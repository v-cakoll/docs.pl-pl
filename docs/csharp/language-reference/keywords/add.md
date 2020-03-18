---
title: add - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 323064dcbe7596b5f1d2f0f6aa566b07cee45789
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713806"
---
# <a name="add-c-reference"></a>add (odwołanie w C#)
Kontekstowe `add` słowo kluczowe służy do definiowania niestandardowego akcesora zdarzeń, który jest wywoływany, gdy kod klienta subskrybuje [zdarzenie](./event.md). Jeśli podasz `add` niestandardowy akcesor, należy również podać [remove](./remove.md) akcesor.  
  
## <a name="example"></a>Przykład  
W poniższym przykładzie przedstawiono `add` zdarzenie, które ma niestandardowe i [usunąć](./remove.md) akcesory. Aby uzyskać pełny przykład, zobacz [Jak zaimplementować zdarzenia interfejsu](../../programming-guide/events/how-to-implement-interface-events.md).
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 Zazwyczaj nie trzeba podać własne niestandardowe akcesory zdarzeń. Akcesory, które są automatycznie generowane przez kompilator podczas deklarowania zdarzenia są wystarczające dla większości scenariuszy.  
  
## <a name="see-also"></a>Zobacz też

- [Zdarzenia](../../programming-guide/events/index.md)

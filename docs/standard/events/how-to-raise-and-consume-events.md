---
title: 'Porady: wywoływanie zdarzeń i korzystanie z nich'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
ms.openlocfilehash: 256b5ae9ac2145e339136985872dfa5423aca730
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131583"
---
# <a name="how-to-raise-and-consume-events"></a>Porady: wywoływanie zdarzeń i korzystanie z nich
Przykłady w tym temacie pokazują, jak pracować ze zdarzeniami. Obejmują one przykłady <xref:System.EventHandler> pełnomocnika, <xref:System.EventHandler%601> delegata i delegata niestandardowego, aby zilustrować zdarzenia z danymi i bez nich.  
  
 W przykładach są używane pojęcia opisane w [artykule Zdarzenia.](../../../docs/standard/events/index.md)  
  
## <a name="example"></a>Przykład  
 W pierwszym przykładzie pokazano, jak podnieść i zużywać zdarzenie, które nie ma danych. Zawiera klasę o `Counter` nazwie, która `ThresholdReached`ma zdarzenie o nazwie . To zdarzenie jest wywoływane, gdy wartość licznika jest równa lub przekracza wartość progową. Pełnomocnik <xref:System.EventHandler> jest skojarzony ze zdarzeniem, ponieważ nie podano żadnych danych zdarzenia.  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>Przykład  
 W następnym przykładzie pokazano, jak podnieść i zużywać zdarzenie, które zawiera dane. Delegat <xref:System.EventHandler%601> jest skojarzony ze zdarzeniem i podano wystąpienie niestandardowego obiektu danych zdarzenia.  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>Przykład  
 W następnym przykładzie pokazano, jak zadeklarować pełnomocnika dla zdarzenia. Pełnomocnik ma nazwę `ThresholdReachedEventHandler`. To tylko ilustracja. Zazwyczaj nie trzeba zadeklarować pełnomocnika dla zdarzenia, ponieważ można użyć <xref:System.EventHandler> lub <xref:System.EventHandler%601> pełnomocnika. Pełnomocnika należy zadeklarować tylko w rzadkich scenariuszach, takich jak udostępnianie klasy starszemu kodowi, który nie może używać typów ogólnych.  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>Zobacz też

- [Zdarzenia](../../../docs/standard/events/index.md)

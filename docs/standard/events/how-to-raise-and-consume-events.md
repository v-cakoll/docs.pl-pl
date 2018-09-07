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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa933e0fc589d0dbfec741e9db7fb11222cfdf38
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44065001"
---
# <a name="how-to-raise-and-consume-events"></a>Porady: wywoływanie zdarzeń i korzystanie z nich
Przykłady w tym temacie pokazują sposób pracy ze zdarzeniami. Obejmują one przykłady <xref:System.EventHandler> delegować, <xref:System.EventHandler%601> delegatów oraz niestandardową klasę delegatów, aby zilustrować wydarzenia z i bez danych.  
  
 W przykładach wykorzystano Koncepcje opisane w [zdarzenia](../../../docs/standard/events/index.md) artykułu.  
  
## <a name="example"></a>Przykład  
 Pierwszy przykład pokazuje jak podnieść i zużyć zdarzenie, które nie zawiera danych. Zawiera klasę o nazwie `Counter` która posiada zdarzenie o nazwie `ThresholdReached`. To zdarzenie jest wywoływane, gdy wartość licznika jest równa lub przekracza wartość progową. <xref:System.EventHandler> Delegat jest skojarzony ze zdarzeniem, ponieważ podano żadnych dane zdarzenia.  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>Przykład  
 Następny przykład pokazuje jak podnieść i zużyć zdarzenie, które zawierają dane. <xref:System.EventHandler%601> Delegat jest skojarzony ze zdarzeniem i znajduje się wystąpienie obiektu danych zdarzenia niestandardowego.  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>Przykład  
 Następny przykład pokazuje, jak zadeklarować obiektu delegowany dla zdarzenia. Pełnomocnik ma nazwę `ThresholdReachedEventHandler`. Jest to po prostu ilustracja. Zazwyczaj trzeba zadeklarować obiektu delegowany dla zdarzenia, ponieważ można użyć <xref:System.EventHandler> lub <xref:System.EventHandler%601> delegować. Należy zadeklarować delegata tylko w rzadkich scenariuszach, takich jak staje się dostępny dla starszego kodu, który nie może używać elementów Generic swojej klasy.  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia](../../../docs/standard/events/index.md)

---
title: "Porady: wywoływanie zdarzeń i korzystanie z nich"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d052c865a554977ce5c8b0a347337d9d9b92fc57
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-raise-and-consume-events"></a>Porady: wywoływanie zdarzeń i korzystanie z nich
Przykłady w tym temacie przedstawiają sposób pracy ze zdarzeniami. Obejmują one przykłady <xref:System.EventHandler> delegować, <xref:System.EventHandler%601> delegata i niestandardowych delegata, aby zilustrować zdarzenia z włączonymi i wyłączonymi danych.  
  
 W przykładach użyto pojęcia opisane w [zdarzenia](../../../docs/standard/events/index.md) artykułu.  
  
## <a name="example"></a>Przykład  
 W pierwszym przykładzie przedstawiono sposób pozyskiwania i zużywać zdarzenie, które nie ma danych. Zawiera klasy o nazwie `Counter` ma zdarzenia o nazwie `ThresholdReached`. To zdarzenie jest wywoływane, gdy wartość licznika jest równa lub większa niż wartość progu. <xref:System.EventHandler> Delegat jest skojarzone ze zdarzeniem, ponieważ nie jest podany żadnych danych zdarzenia.  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a>Przykład  
 Kolejnym przykładzie pokazano, jak pozyskiwania i zużywać zdarzenie, które zawierają dane. <xref:System.EventHandler%601> Delegat jest skojarzone ze zdarzeniem oraz podano wystąpienia obiektu danych niestandardowych zdarzeń.  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a>Przykład  
 Kolejnym przykładzie pokazano, jak można zadeklarować obiektu delegowanego zdarzenia. Delegat nosi nazwę `ThresholdReachedEventHandler`. Jest to po prostu zapoznać się z ilustracją. Zazwyczaj nie trzeba zadeklarować delegata zdarzenia, ponieważ można użyć <xref:System.EventHandler> lub <xref:System.EventHandler%601> delegowanie. Powinien deklarować delegata tylko w rzadkich scenariusze, takie jak udostępnianie klasy starszego kodu, który nie można używać typów ogólnych.  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia](../../../docs/standard/events/index.md)

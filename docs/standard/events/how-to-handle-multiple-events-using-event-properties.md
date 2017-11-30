---
title: "Porady: obsługa wielu zdarzeń przy użyciu właściwości zdarzenia"
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
- event properties [.NET Framework]
- multiple events [.NET Framework]
- event handling [.NET Framework], with multiple events
- events [.NET Framework], multiple
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c16918e715a93de8fdf164e75ce7be81511b71b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a>Porady: obsługa wielu zdarzeń przy użyciu właściwości zdarzenia
Aby użyć właściwości zdarzeń należy zdefiniować właściwości zdarzenia w klasie, która wywołuje zdarzenia, a następnie ustawić delegatów dla właściwości zdarzenia w klasach, które obsługują zdarzenia. Aby zaimplementować w klasie wiele właściwości zdarzeń, klasa musi wewnętrznie przechowywać i zachowywać zdefiniowanego delegata dla każdego zdarzenia. Typowym podejściem jest implementacja kolekcji delegata, która jest indeksowana przy użyciu klucza zdarzenia.  
  
 Aby przechowywać delegatów dla każdego zdarzenia, można użyć klasy <xref:System.ComponentModel.EventHandlerList> lub zaimplementować własną kolekcję. Klasa kolekcji musi dostarczać metody do ustawiania, uzyskiwania dostępu i pobierania delegata obsługi zdarzeń opartego na kluczu zdarzeń. Na przykład można użyć klasy <xref:System.Collections.Hashtable> lub pochodnej niestandardowej klasy na podstawie klasy <xref:System.Collections.DictionaryBase>. Szczegóły implementacji kolekcji delegata nie muszą być udostępniane poza klasą.  
  
 Każda właściwość zdarzenia w klasie definiuje metody dodawania i usuwania akcesora. Dodanie akcesora do właściwości zdarzenia dodaje wystąpienie delegata wejściowego do kolekcji delegata. Usunięcie akcesora właściwości zdarzenia usuwa wystąpienie delegata wejściowego z kolekcji delegata. Akcesory właściwości zdarzenia używają wstępnie zdefiniowanego klucza dla właściwości zdarzenia do dodawania i usuwania wystąpień z kolekcji delegata.  
  
### <a name="to-handle-multiple-events-using-event-properties"></a>Do obsługi wielu zdarzeń przy użyciu właściwości zdarzenia  
  
1.  Zdefiniuj kolekcje delegata w klasie, która wywołuje zdarzenia.  
  
2.  Zdefiniuj klucz dla każdego zdarzenia.  
  
3.  Zdefiniuj właściwości zdarzenia w klasie, która wywołuje zdarzenia.  
  
4.  Użyj kolekcji delegata do implementacji metod dodawania i usuwania akcesora dla właściwości zdarzenia.  
  
5.  Użyj publicznych zdarzeń właściwości, aby dodawać i usuwać delegatów obsługi zdarzeń w klasach, które obsługują zdarzenia.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład napisany w języku C# implementuje właściwości zdarzenia `MouseDown` i `MouseUp`, z wykorzystaniem <xref:System.ComponentModel.EventHandlerList> do przechowywania każdego zdarzenia delegata. Słowa kluczowe w konstrukcji właściwości zdarzenia są pogrubione.  
  
> [!NOTE]
>  Właściwości zdarzenia nie są obsługiwane w [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)].  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>  
 [Zdarzenia](../../../docs/standard/events/index.md)  
 <xref:System.Web.UI.Control.Events%2A>  
 [Porady: deklarowanie zdarzeń niestandardowych w celu zachowywania pamięci](~/docs/visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)

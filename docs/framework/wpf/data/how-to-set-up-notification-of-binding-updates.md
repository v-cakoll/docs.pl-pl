---
title: "Jak ustawić powiadomienie o łączeniu aktualizacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a07337e99e985bfbc0a5dbc5f2d231ee36cf1422
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-up-notification-of-binding-updates"></a>Jak ustawić powiadomienie o łączeniu aktualizacji
W tym przykładzie pokazano, jak można skonfigurować, aby otrzymać powiadomienie, gdy cel wiązania (docelowy) lub powiązanie właściwości source (źródło) powiązania został zaktualizowany.  
  
## <a name="example"></a>Przykład  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]zgłasza zdarzenie aktualizacji danych zawsze o zaktualizowaniu powiązanie źródłowa lub docelowa. To zdarzenie jest używana wewnętrznie, informują o tym [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] którego on należy zaktualizować, ponieważ zmienił się powiązana z danymi. Należy pamiętać, że te zdarzenia do pracy, a także do- lub dwukierunkowo powiązanie działało poprawnie, musisz wdrożyć swoją danych klasy przy użyciu <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Aby uzyskać więcej informacji, zobacz [powiadomienia o zmianie właściwości wdrożenie](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).  
  
 Ustaw <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> lub <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> właściwości (lub obie) do `true` w powiązaniu. Program obsługi podane przez użytkownika do nasłuchiwania dla tego zdarzenia musi być dołączony bezpośrednio do elementu, w którym ma być powiadamiane o zmianach lub ogólną kontekst danych Aby Pamiętaj, że w kontekście została zmieniona.  
  
 Oto przykład pokazujący sposób skonfigurować powiadomienia, gdy właściwość docelowa została zaktualizowana.  
  
 [!code-xaml[DirectionalBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 Następnie można przypisać obsługi oparte na EventHandler\<T > delegować, *OnTargetUpdated* w tym przykładzie Obsługa zdarzenia:  
  
 [!code-csharp[DirectionalBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 Parametry zdarzenia może służyć do określenia szczegółowe informacje o właściwości zmianie (na przykład typ lub konkretny element w przypadku tej procedury obsługi jest podłączony do więcej niż jeden element), które mogą być przydatne, jeśli istnieje wiele właściwości powiązanej na pojedynczy element.  
  
## <a name="see-also"></a>Zobacz też  
 [Powiązanie danych — omówienie](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)

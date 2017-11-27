---
title: "Jak implementować powiadomienie o zmianie właściwości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6674628acd4ea6b18f98a0ab5e20935220595de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-property-change-notification"></a>Jak implementować powiadomienie o zmianie właściwości
Do obsługi <xref:System.Windows.Data.BindingMode.OneWay> lub <xref:System.Windows.Data.BindingMode.TwoWay> powiązanie umożliwia powiązanie właściwości docelowej automatycznie zgodnie ze zmianami dynamiczne źródła powiązanie (na przykład okienko podglądu aktualizowane automatycznie, gdy użytkownik edytuje formularza), klasa należy podać powiadomienia odpowiednie zmiany właściwości. W tym przykładzie pokazano, jak utworzyć klasę, która implementuje <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
## <a name="example"></a>Przykład  
 Aby zaimplementować <xref:System.ComponentModel.INotifyPropertyChanged> należy zadeklarować <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenia i utworzyć `OnPropertyChanged` — metoda. Następnie dla każdej właściwości mają powiadomienia o zmianie dla wywołania `OnPropertyChanged` zawsze, gdy właściwość jest aktualizowana.  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 Aby wyświetlić przykład przedstawia sposób `Person` klasa może być używana do obsługi <xref:System.Windows.Data.BindingMode.TwoWay> powiązanie, zobacz [kontroli, gdy tekst pola tekstowego aktualizuje źródła](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd źródeł powiązania](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [Omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Tematy porad](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)

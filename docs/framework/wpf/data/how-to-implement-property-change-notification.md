---
title: 'Instrukcje: Implementuj powiadomienie o zmianie właściwości'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
ms.openlocfilehash: 93a291b6dd35f9cc13c3c6f88aca5dc376b8bc1b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352753"
---
# <a name="how-to-implement-property-change-notification"></a>Instrukcje: Implementuj powiadomienie o zmianie właściwości
Do obsługi <xref:System.Windows.Data.BindingMode.OneWay> lub <xref:System.Windows.Data.BindingMode.TwoWay> powiązanie umożliwiające powiązanie właściwości docelowej do automatycznie odzwierciedlają zmiany dynamicznej w źródle powiązania (na przykład, aby mieć okienko podglądu aktualizowane automatycznie, gdy użytkownik edytuje formularza), klasa wymaga do udostępniania powiadomień o odpowiednie zmiany właściwości. W tym przykładzie pokazano, jak utworzyć klasę, która implementuje <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
## <a name="example"></a>Przykład  
 Do zaimplementowania <xref:System.ComponentModel.INotifyPropertyChanged> trzeba zadeklarować <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzeń i utworzyć `OnPropertyChanged` metody. Następnie dla każdej właściwości mają powiadomienia o zmianie dla wywołania `OnPropertyChanged` zawsze, gdy właściwość jest aktualizowana.  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 Aby zobaczyć przykładowy sposób, w jaki `Person` klasa może być używana do obsługi <xref:System.Windows.Data.BindingMode.TwoWay> powiązań, zobacz [kontrolować kiedy tekst TextBox aktualizuje źródło](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## <a name="see-also"></a>Zobacz także
- [Wiązanie źródeł — omówienie](binding-sources-overview.md)
- [Powiązanie danych — omówienie](data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)

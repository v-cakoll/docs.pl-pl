---
title: Jak implementować powiadomienie o zmianie właściwości
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
ms.openlocfilehash: 4f9ff49a443577e119b0c1079abbe23bd7ede4c4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459747"
---
# <a name="how-to-implement-property-change-notification"></a>Jak implementować powiadomienie o zmianie właściwości
Aby obsłużyć <xref:System.Windows.Data.BindingMode.OneWay> lub <xref:System.Windows.Data.BindingMode.TwoWay> powiązania, aby właściwości celu powiązania automatycznie odzwierciedlały dynamiczne zmiany źródła powiązania (na przykład w celu automatycznego aktualizowania okienka podglądu podczas edytowania formularza przez użytkownika), Klasa musi podaj odpowiednie powiadomienia o zmianach właściwości. Ten przykład pokazuje, jak utworzyć klasę, która implementuje <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
## <a name="example"></a>Przykład  
 Aby zaimplementować <xref:System.ComponentModel.INotifyPropertyChanged> należy zadeklarować zdarzenie <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> i utworzyć metodę `OnPropertyChanged`. Następnie dla każdej właściwości, dla której chcesz zmienić powiadomienia, należy wywołać `OnPropertyChanged` przy każdej aktualizacji właściwości.  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 Aby zobaczyć przykład sposobu, w jaki Klasa `Person` może być używana do obsługi powiązań <xref:System.Windows.Data.BindingMode.TwoWay>, zobacz [kontrolowanie, kiedy tekst TextBox aktualizuje Źródło](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wiązanie źródeł — omówienie](binding-sources-overview.md)
- [Powiązanie danych — omówienie](../../../desktop-wpf/data/data-binding-overview.md)
- [Tematy z instrukcjami](data-binding-how-to-topics.md)

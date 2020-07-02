---
title: Jak implementować powiadomienie o zmianie właściwości
description: Włącz automatyczne powiadamianie źródła powiązania, gdy wartość właściwości zostanie zmieniona w Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: 6c298930b7b1f812e94ea6add8f53c67d3453530
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620784"
---
# <a name="how-to-implement-property-change-notification"></a>Jak implementować powiadomienie o zmianie właściwości
Aby <xref:System.Windows.Data.BindingMode.OneWay> umożliwić obsługę lub <xref:System.Windows.Data.BindingMode.TwoWay> wiązanie w celu włączenia właściwości celu powiązania, aby automatycznie odzwierciedlały dynamiczne zmiany źródła powiązania (na przykład w celu automatycznego aktualizowania okienka podglądu podczas edytowania formularza przez użytkownika), Klasa musi podać odpowiednie powiadomienia o zmianach właściwości. Ten przykład przedstawia sposób tworzenia klasy implementującej <xref:System.ComponentModel.INotifyPropertyChanged> .  
  
## <a name="example"></a>Przykład  
 Aby zaimplementować, należy <xref:System.ComponentModel.INotifyPropertyChanged> zadeklarować <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenie i utworzyć `OnPropertyChanged` metodę. Następnie dla każdej właściwości, dla której chcesz zmienić powiadomienia, `OnPropertyChanged` jest wywoływana za każdym razem, gdy właściwość zostanie zaktualizowana.  
  
 [!code-csharp[SimpleBinding#PersonClass](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 Aby zobaczyć przykład sposobu `Person` użycia klasy do obsługi <xref:System.Windows.Data.BindingMode.TwoWay> powiązań, zobacz [kontrolowanie, kiedy tekst TextBox aktualizuje Źródło](how-to-control-when-the-textbox-text-updates-the-source.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wiązanie źródeł — omówienie](binding-sources-overview.md)
- [Przegląd powiązań danych](../../../desktop-wpf/data/data-binding-overview.md)
- [— Tematy porad](data-binding-how-to-topics.md)

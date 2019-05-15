---
title: 'Instrukcje: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- change notifications [Windows Forms], raising
- BindingSource component [Windows Forms], and IPropertyChange
- data sources [Windows Forms], detecting changes
- examples [Windows Forms], BindingSource component
- change notifications
- INotifyPropertyChanged interface [Windows Forms], using with BindingSource
- BindingSource component [Windows Forms], examples
ms.assetid: 7fa2cf51-c09f-4375-adf0-e36c5617f099
ms.openlocfilehash: 6a622e64076d2ed2a073dc0f0e55204d1767cfd7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591824"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Instrukcje: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged
<xref:System.Windows.Forms.BindingSource> Składnika automatycznie wykryje zmiany w źródle danych, gdy typ zawarte w implementuje źródło danych <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu i zgłasza <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenia po zmianie wartości właściwości. Jest to przydatne, ponieważ formanty powiązane z <xref:System.Windows.Forms.BindingSource> następnie automatycznie aktualizuje jak zmiana wartości źródła danych.  
  
> [!NOTE]
>  Jeśli dane źródłowe implementuje <xref:System.ComponentModel.INotifyPropertyChanged> i wykonywania operacji asynchronicznych, nie powinna dokonywać zmian w źródle danych w wątku tła. Zamiast tego należy odczytać danych z wątku w tle i scalania danych na liście w wątku interfejsu użytkownika.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje proste wdrażanie <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Pokazuje także sposób, w jaki <xref:System.Windows.Forms.BindingSource> automatycznie przekazuje zmian źródła danych do granicy decyduje o <xref:System.Windows.Forms.BindingSource> jest powiązany z listy <xref:System.ComponentModel.INotifyPropertyChanged> typu.  
  
 Jeśli używasz `CallerMemberName` atrybutu wywołania `NotifyPropertyChanged` metody nie trzeba określić nazwę właściwości jako argument ciągu. Aby uzyskać więcej informacji, zobacz [informacje o wywołującym (C#)](../../../csharp/programming-guide/concepts/caller-information.md) lub [informacje o wywołującym (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [BindingSource, składnik](bindingsource-component.md)
- [Instrukcje: Wywoływanie powiadomień o zmianie za BindingSource Resetitem](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)

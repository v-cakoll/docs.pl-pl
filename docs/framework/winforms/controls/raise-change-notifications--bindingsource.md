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
ms.openlocfilehash: 7dc640f272226da650a63b1a3434822d21053b48
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968284"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Instrukcje: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged
Składnik automatycznie wykryje zmiany w źródle danych, gdy typ zawarty w źródle danych <xref:System.ComponentModel.INotifyPropertyChanged> implementuje interfejs i zgłasza <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenia, gdy wartość właściwości zostanie zmieniona. <xref:System.Windows.Forms.BindingSource> Jest to przydatne, ponieważ formanty powiązane z <xref:System.Windows.Forms.BindingSource> , zostaną następnie automatycznie zaktualizowane w miarę zmiany wartości źródła danych.  
  
> [!NOTE]
> Jeśli źródło danych implementuje <xref:System.ComponentModel.INotifyPropertyChanged> i wykonujesz operacje asynchroniczne, nie należy wprowadzać zmian w źródle danych w wątku w tle. Zamiast tego należy odczytywać dane w wątku w tle i scalać dane do listy w wątku interfejsu użytkownika.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje prostą implementację <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Pokazuje również, <xref:System.Windows.Forms.BindingSource> jak automatycznie przekazuje źródło danych do kontrolki powiązanej, <xref:System.Windows.Forms.BindingSource> gdy jest powiązany <xref:System.ComponentModel.INotifyPropertyChanged> z listą typu.  
  
 Jeśli używasz `CallerMemberName` atrybutu, wywołania `NotifyPropertyChanged` do metody nie muszą określać nazwy właściwości jako argumentu ciągu. Aby uzyskać więcej informacji, zobacz [Informacje oC#wywołującym ()](../../../csharp/programming-guide/concepts/caller-information.md) lub [Informacje o wywołującym (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [BindingSource, składnik](bindingsource-component.md)
- [Instrukcje: Zgłoś powiadomienia o zmianie za pomocą metody BindingSource ResetItem](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)

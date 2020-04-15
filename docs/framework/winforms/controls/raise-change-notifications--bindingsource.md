---
title: 'Porady: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged'
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
ms.openlocfilehash: 07248ec0b8ac4f2356d9c9915b6a904dfad30cb2
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388979"
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Porady: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged
Składnik <xref:System.Windows.Forms.BindingSource> automatycznie wykryje zmiany w źródle danych, gdy typ zawarty <xref:System.ComponentModel.INotifyPropertyChanged> w źródle <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> danych implementuje interfejs i wywołuje zdarzenia po zmianie wartości właściwości. Jest to przydatne, ponieważ <xref:System.Windows.Forms.BindingSource> formanty powiązane z będzie następnie automatycznie aktualizować w miarę zmiany wartości źródła danych.  
  
> [!NOTE]
> Jeśli źródło danych <xref:System.ComponentModel.INotifyPropertyChanged> implementuje i wykonujesz operacje asynchroniczne, nie należy wprowadzać zmian w źródle danych w wątku w tle. Zamiast tego należy odczytać dane w wątku w tle i scalić dane do listy w wątku interfejsu użytkownika.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje prostą <xref:System.ComponentModel.INotifyPropertyChanged> implementację interfejsu. Pokazuje również, <xref:System.Windows.Forms.BindingSource> jak automatycznie przekazuje zmiany źródła danych do <xref:System.Windows.Forms.BindingSource> kontroli powiązanej, <xref:System.ComponentModel.INotifyPropertyChanged> gdy jest powiązany z listą typu.  
  
 Jeśli używasz `CallerMemberName` atrybutu, wywołania `NotifyPropertyChanged` metody nie trzeba określać nazwę właściwości jako argument ciągu. Aby uzyskać więcej informacji, zobacz [Informacje o dzwoniącym (C#)](../../../csharp/language-reference/attributes/caller-information.md) lub [Informacje o dzwoniącym (Visual Basic)](../../../visual-basic/programming-guide/concepts/caller-information.md).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów System, System.Data, System.Drawing i System.Windows.Forms.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [BindingSource, składnik](bindingsource-component.md)
- [Instrukcje: wywoływanie powiadomień o zmianie za pomocą metody BindingSource ResetItem](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)

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
ms.openlocfilehash: 71fb0a09387c77dbc792180dac1b8594d11b3642
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119513"
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
  
-   Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu. Zobacz też [jak: Skompilować i uruchomić przykładowy kod pełną Windows Forms przy użyciu programu Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb129228(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ComponentModel.INotifyPropertyChanged>
- [BindingSource, składnik](bindingsource-component.md)
- [Instrukcje: Wywoływanie powiadomień o zmianie za BindingSource Resetitem](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)

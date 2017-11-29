---
title: "Porady: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 049d87799e4ef241de0647815470cc853a29ea31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-raise-change-notifications-using-a-bindingsource-and-the-inotifypropertychanged-interface"></a>Porady: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged
<xref:System.Windows.Forms.BindingSource> Składnika będzie automatycznie wykrywał zmiany w źródle danych typu znajdujące się w implementuje źródła danych <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu i zgłasza <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzeń, gdy wartość właściwości zostanie zmieniona. Jest to przydatne, ponieważ formanty powiązane z <xref:System.Windows.Forms.BindingSource> następnie automatycznie zaktualizuje jako zmiana wartości źródła danych.  
  
> [!NOTE]
>  Jeśli źródło danych implementuje <xref:System.ComponentModel.INotifyPropertyChanged> i wykonują operacje asynchroniczne, nie należy wprowadzać zmian do źródła danych na wątku w tle. Należy odczytać danych z wątku w tle i Scal dane na liście w wątku interfejsu użytkownika.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu pokazano prosty implementacja <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu. Zawiera także sposób <xref:System.Windows.Forms.BindingSource> automatycznie przekazuje zmian źródła danych do powiązanej decyduje o <xref:System.Windows.Forms.BindingSource> jest powiązany z listy <xref:System.ComponentModel.INotifyPropertyChanged> typu.  
  
 Jeśli używasz `CallerMemberName` atrybutu, wywołania `NotifyPropertyChanged` metody nie trzeba określać nazwę właściwości jako argument ciągu. Aby uzyskać więcej informacji, zobacz [informacje o wywołującym](http://msdn.microsoft.com/library/9cb2b8c0-c4f6-44b8-9c90-38948455b373).  
  
 [!code-csharp[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.IPropertyChangeExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.IPropertyChangeExample/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, dane systemowe, System.Drawing i System.Windows.Forms.  
  
 Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.  Zobacz też [HYPERLINK "http://msdn.microsoft.com/library/Bb129228 (v=vs.110)" porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 [BindingSource — składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Porady: wywoływanie powiadomień o zmianie za pomocą metody BindingSource Resetitem](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)

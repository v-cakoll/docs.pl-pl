---
title: Nawigowanie po danych przy użyciu kontrolki BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
ms.openlocfilehash: 10508cb447e70cc387f9d98effa3bc4b5ccbbaa9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735998"
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>Porady: nawigowanie w danych za pomocą kontrolki BindingNavigator formularzy systemu Windows
Pojawieniu formantu <xref:System.Windows.Forms.BindingNavigator> w Windows Forms umożliwiają deweloperom udostępnianie użytkownikom końcowym prostego interfejsu użytkownika do nawigacji i manipulowania danymi na tworzonych formularzach.  
  
 Formant <xref:System.Windows.Forms.BindingNavigator> jest formantem <xref:System.Windows.Forms.ToolStrip> z wstępnie skonfigurowanymi przyciskami do nawigacji do pierwszego, ostatniego, następnego i poprzedniego rekordu w zestawie danych, a także przycisków służących do dodawania i usuwania rekordów. Dodawanie przycisków do kontrolki <xref:System.Windows.Forms.BindingNavigator> jest proste, ponieważ jest to kontrolka <xref:System.Windows.Forms.ToolStrip>. Aby zapoznać się z przykładami, zobacz [jak: Dodawanie przycisków Load, Save i Cancel do Windows Forms BindingNavigator Control](load-save-and-cancel-bindingnavigator.md).  
  
 Dla każdego przycisku w kontrolce <xref:System.Windows.Forms.BindingNavigator> istnieje odpowiedni element członkowski składnika <xref:System.Windows.Forms.BindingSource>, który programowo umożliwia korzystanie z tych samych funkcji. Na przykład przycisk <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> odpowiada metodzie <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> składnika <xref:System.Windows.Forms.BindingSource>, przycisk <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> odpowiada metodzie <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> i tak dalej. W związku z tym włączenie kontrolki <xref:System.Windows.Forms.BindingNavigator> do nawigowania po rekordach danych jest proste jako ustawienie właściwości <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> na odpowiedni składnik <xref:System.Windows.Forms.BindingSource> w formularzu.  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>Aby skonfigurować formant BindingNavigator  
  
1. Dodaj składnik <xref:System.Windows.Forms.BindingSource> o nazwie `bindingSource1` i dwóch kontrolek <xref:System.Windows.Forms.TextBox> o nazwie `textBox1` i `textBox2`.  
  
2. Powiąż `bindingSource1` z danymi i kontrolki TextBox, aby `bindingSource1`. Aby to zrobić, wklej następujący kod do formularza i Wywołaj `LoadData` z konstruktora formularza lub <xref:System.Windows.Forms.Form.Load> metody obsługi zdarzeń.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3. Dodaj kontrolkę <xref:System.Windows.Forms.BindingNavigator> o nazwie `bindingNavigator1` do formularza.  
  
4. Ustaw właściwość <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> na `bindingNavigator1` na `bindingSource1`. Można to zrobić za pomocą projektanta lub kodu.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu jest kompletnym przykładem dla powyższych kroków.  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Data, system. Drawing, system. Windows. Forms i system. XML.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingNavigator>
- [BindingNavigator, kontrolka](bindingnavigator-control-windows-forms.md)
- [ToolStrip, kontrolka](toolstrip-control-windows-forms.md)

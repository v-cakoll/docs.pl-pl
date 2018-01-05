---
title: "Porady: nawigowanie w danych za pomocą kontrolki BindingNavigator formularzy systemu Windows"
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
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c5b49d84f98213e95c83c5476007297149adc16
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>Porady: nawigowanie w danych za pomocą kontrolki BindingNavigator formularzy systemu Windows
Pojawienie się <xref:System.Windows.Forms.BindingNavigator> formantu w formularzach systemu Windows umożliwia deweloperom zapewnić użytkownikom końcowym proste danych nawigacji i manipulacji interfejsu użytkownika w formularzach tworzenia.  
  
 <xref:System.Windows.Forms.BindingNavigator> Formant jest <xref:System.Windows.Forms.ToolStrip> kontrolki z przycisków wstępnie nawigacji jako pierwszy, ostatni, następny i poprzedni rekord w zestawie danych, jak również przyciski dodawania i usuwania rekordów. Dodawanie przycisków do <xref:System.Windows.Forms.BindingNavigator> formant jest łatwe, ponieważ jest on <xref:System.Windows.Forms.ToolStrip> formantu.  Zobacz też [porady: Dodawanie obciążenia, Zapisz i Anuluj przycisków do formantu BindingNavigator formularzy systemu Windows](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).  
  
 Dla każdego przycisku na <xref:System.Windows.Forms.BindingNavigator> kontrolować, jest elementem członkowskim odpowiedniego <xref:System.Windows.Forms.BindingSource> składnik, który umożliwia programowo te same funkcje. Na przykład <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> przycisk odpowiada <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> metody <xref:System.Windows.Forms.BindingSource> składnika <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> przycisk odpowiada <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> — metoda i tak dalej. W związku z tym włączenie <xref:System.Windows.Forms.BindingNavigator> formant do nawigacji rekordów danych jest prostą jako ustawienie jej <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> właściwości do odpowiedniego <xref:System.Windows.Forms.BindingSource> składnika w formularzu.  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>Aby skonfigurować BindingNavigator — formant  
  
1.  Dodaj <xref:System.Windows.Forms.BindingSource> składnika o nazwie `bindingSource1` i dwa <xref:System.Windows.Forms.TextBox> formantów `textBox1` i `textBox2`.  
  
2.  Powiąż `bindingSource1` do danych i formanty pole tekstowe `bindingSource1`. W tym celu Wklej następujący kod do formularza i wywołanie `LoadData` z konstruktora formularza lub <xref:System.Windows.Forms.Form.Load> metoda obsługi zdarzeń.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  Dodaj <xref:System.Windows.Forms.BindingNavigator> formantu o nazwie `bindingNavigator1` do formularza.  
  
4.  Ustaw <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> właściwość `bindingNavigator1` do `bindingSource1`. Można to zrobić przy użyciu projektanta lub w kodzie.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod jest pełny przykład dla wymienionymi wcześniej czynności.  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, dane systemowe, System.Drawing, System.Windows.Forms i zestawów System.Xml.  
  
 Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.BindingNavigator>  
 [BindingNavigator, kontrolka](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [ToolStrip, kontrolka](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)

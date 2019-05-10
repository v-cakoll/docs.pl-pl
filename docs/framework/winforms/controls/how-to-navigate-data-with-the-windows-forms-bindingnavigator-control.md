---
title: 'Instrukcje: nawigowanie w danych za pomocą kontrolki BindingNavigator formularzy systemu Windows'
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
ms.openlocfilehash: 0702532627fe4425a7c5e3ade5530939c8df5500
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649244"
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a>Instrukcje: nawigowanie w danych za pomocą kontrolki BindingNavigator formularzy systemu Windows
Pojawienie się <xref:System.Windows.Forms.BindingNavigator> kontroli w formularzach Windows Forms umożliwia deweloperom zapewni użytkownikom końcowym proste dane nawigacji i manipulowania interfejsu użytkownika w formularzach tworzą.  
  
 <xref:System.Windows.Forms.BindingNavigator> Formant jest <xref:System.Windows.Forms.ToolStrip> sterowania za pomocą przycisków wstępnie skonfigurować pod kątem nawigację do pierwszego, last, następnej i poprzedniej rekordu w zestawie danych, jak również przycisków, aby dodawać i usuwać rekordy. Dodawanie przycisków do <xref:System.Windows.Forms.BindingNavigator> kontroli jest łatwe, ponieważ jest on <xref:System.Windows.Forms.ToolStrip> kontroli. Aby uzyskać przykłady, zobacz [jak: Dodaj obciążenia, Zapisz i Anuluj przycisków Windows kontrolki BindingNavigator formularzy](load-save-and-cancel-bindingnavigator.md).  
  
 Dla każdego przycisku w <xref:System.Windows.Forms.BindingNavigator> sterowania, jest elementem członkowskim odpowiednie <xref:System.Windows.Forms.BindingSource> składnik, który programowo zezwala na taką samą funkcjonalność. Na przykład <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> przycisk odnosi się do <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> metody <xref:System.Windows.Forms.BindingSource> składnika <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> przycisk odnosi się do <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> metoda i tak dalej. W rezultacie, umożliwiając <xref:System.Windows.Forms.BindingNavigator> sterowania Przejdź rekordów danych to prosty jako ustawienie jego <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> właściwości do odpowiednich <xref:System.Windows.Forms.BindingSource> składnika w formularzu.  
  
### <a name="to-set-up-the-bindingnavigator-control"></a>Aby skonfigurować BindingNavigator — kontrolka  
  
1. Dodaj <xref:System.Windows.Forms.BindingSource> składnika o nazwie `bindingSource1` oraz dwóch <xref:System.Windows.Forms.TextBox> kontrolki o nazwie `textBox1` i `textBox2`.  
  
2. Powiąż `bindingSource1` do danych i kontrolki pola tekstowego do `bindingSource1`. Aby to zrobić, wklej następujący kod do formularza i wywołania `LoadData` z konstruktora formularza lub <xref:System.Windows.Forms.Form.Load> metody obsługi zdarzeń.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3. Dodaj <xref:System.Windows.Forms.BindingNavigator> formantu o nazwie `bindingNavigator1` do formularza.  
  
4. Ustaw <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> właściwość `bindingNavigator1` do `bindingSource1`. Można to zrobić za pomocą projektanta lub w kodzie.  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu jest kompletny przykład kroków wymienionych powyżej.  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów systemu, dane systemowe, System.Drawing, przestrzeń nazw System.Windows.Forms i System.Xml.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingNavigator>
- [BindingNavigator, kontrolka](bindingnavigator-control-windows-forms.md)
- [ToolStrip, kontrolka](toolstrip-control-windows-forms.md)

---
title: 'Porady: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: a0c68372301d984fc388f37a5ce798cbf99d802b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536595"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a>Porady: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource
Dane można łatwo udostępniać wielu formularzach za pomocą <xref:System.Windows.Forms.BindingSource> składnika. Na przykład można wyświetlić jeden formularz tylko do odczytu, który znajduje się podsumowanie danych źródła danych oraz innej formy można edytować, który zawiera szczegółowe informacje dotyczące aktualnie wybranego elementu w źródle danych. W tym przykładzie pokazano, w tym scenariuszu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak udostępnić <xref:System.Windows.Forms.BindingSource> i jego danych powiązanych w wielu formularzach. W tym przykładzie udostępnionego <xref:System.Windows.Forms.BindingSource> jest przekazany do konstruktora formularza podrzędnego. Formularz podrzędny umożliwia użytkownikowi edytowanie danych dla aktualnie wybranego elementu w formularzu głównym.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.BindingSource.BindingComplete> Zdarzenia dla <xref:System.Windows.Forms.BindingSource> składnika jest obsługiwany w tym przykładzie, aby upewnić się, że dwa formularze pozostają zsynchronizowane. Aby uzyskać więcej informacji na temat przyczyn jest to zrobić, zobacz [porady: Upewnij się, wiele formanty powiązane z tym samym dane źródła pozostają zsynchronizowane](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md).  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Windows.Forms System.Drawing, dane systemowe i zestawów System.Xml.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 [BindingSource, składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Wiązanie danych formularzy Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Instrukcje: obsługa błędów i wyjątków występujących za powodu powiązania danych](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)

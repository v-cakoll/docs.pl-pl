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
ms.openlocfilehash: 765bdb7ee75d7e0c6461311263afe9481830673f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44198767"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a>Porady: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource
Dane mogą łatwo udostępniać w wielu formularzach za <xref:System.Windows.Forms.BindingSource> składnika. Na przykład można wyświetlić jeden formularz tylko do odczytu, który podsumowuje dane źródło danych i innym edytowalnego formularza, który zawiera szczegółowe informacje dotyczące aktualnie wybranego elementu w źródle danych. Ten przykład pokazuje, w tym scenariuszu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób udostępniania <xref:System.Windows.Forms.BindingSource> i jego danych powiązanych w wielu formularzach. W tym przykładzie wspólnie <xref:System.Windows.Forms.BindingSource> jest przekazywany do konstruktora formularza podrzędnego. Formularz podrzędny umożliwia użytkownikowi edytowanie danych dla aktualnie wybranego elementu w formularzu głównym.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.BindingSource.BindingComplete> Zdarzenie <xref:System.Windows.Forms.BindingSource> składnika odbywa się w przykładzie, aby upewnić się, że dwie formy pozostają zsynchronizowane. Aby uzyskać więcej informacji na temat przyczyn jest to zrobić, zobacz [jak: Upewnij się, wiele formanty powiązane z tym samym dane źródła pozostają zsynchronizowane](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md).  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, przestrzeń nazw System.Windows.Forms, System.Drawing, dane systemowe i System.Xml.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 [BindingSource, składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Wiązanie danych formularzy Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Instrukcje: obsługa błędów i wyjątków występujących za powodu powiązania danych](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)

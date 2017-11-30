---
title: "Porady: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource"
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
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 95fd7583e6d86aa84c53f6cee7056f1d631e948b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
  
 Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 [BindingSource — składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Powiązanie danych formularzy systemu Windows](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Porady: obsługa błędów i wyjątków występujących za powodu powiązania danych](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)

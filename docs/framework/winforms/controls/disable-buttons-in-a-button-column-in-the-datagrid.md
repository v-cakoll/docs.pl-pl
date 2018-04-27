---
title: 'Porady: wyłączanie przycisków w kolumnie przycisków w formancie DataGridView formularzy systemu Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4511441e3d8350cd867133a87f34fcba3087f796
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a>Porady: wyłączanie przycisków w kolumnie przycisków w formancie DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Formant zawiera <xref:System.Windows.Forms.DataGridViewButtonCell> klasy do wyświetlania komórki z interfejsem użytkownika (UI), jak przycisk. Jednak <xref:System.Windows.Forms.DataGridViewButtonCell> nie zapewnia możliwość wyłączenia wygląd przycisku wyświetlany przez komórki.  
  
 Poniższy przykład kodu pokazuje sposób dostosowywania <xref:System.Windows.Forms.DataGridViewButtonCell> klasy do wyświetlenia przycisków, które mogą być wyświetlane wyłączone. W przykładzie zdefiniowano nowy typ komórki `DataGridViewDisableButtonCell`, która jest pochodną <xref:System.Windows.Forms.DataGridViewButtonCell>. Ten typ komórki zapewnia nowy `Enabled` właściwość, która może być ustawiony na `false` do rysowania wyłączony przycisk w komórce. W przykładzie zdefiniowano także nowy typ kolumny, `DataGridViewDisableButtonColumn`, który wyświetla `DataGridViewDisableButtonCell` obiektów. Aby zademonstrować tego nowych komórek i kolumn typ, bieżąca wartość <xref:System.Windows.Forms.DataGridViewCheckBoxCell> w obiekcie nadrzędnym <xref:System.Windows.Forms.DataGridView> Określa, czy `Enabled` właściwość `DataGridViewDisableButtonCell` w tym samym wierszu jest `true` lub `false`.  
  
> [!NOTE]
>  Jeśli pochodzi od <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodać nowe właściwości do klasy pochodnej, należy zastąpić `Clone` metodę, aby skopiować nowe właściwości podczas operacji klonowania. Należy także wywołać klasy podstawowej `Clone` metody, aby właściwości klasy podstawowej są kopiowane do nowej komórki lub kolumny.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing, System.Windows.Forms i System.Windows.Forms.VisualStyles.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [DataGridView, kontrolka — architektura](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)

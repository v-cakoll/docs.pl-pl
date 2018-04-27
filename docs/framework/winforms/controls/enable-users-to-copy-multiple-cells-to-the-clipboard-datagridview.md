---
title: 'Porady: umożliwianie użytkownikom kopiowania wielu komórek do schowka z formantu DataGridView formularzy systemu Windows'
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
- cells [Windows Forms], copying to Clipboard
- DataGridView control [Windows Forms], copying multiple cells
- data grids [Windows Forms], copying multiple cells
- Clipboard [Windows Forms], copying multiple cells
ms.assetid: fd0403b2-d0e3-4ae0-839c-0f737e1eb4a9
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 72f00ee548a042690ded57a4186f97de47781622
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-enable-users-to-copy-multiple-cells-to-the-clipboard-from-the-windows-forms-datagridview-control"></a>Porady: umożliwianie użytkownikom kopiowania wielu komórek do schowka z formantu DataGridView formularzy systemu Windows
Po włączeniu kopiowanie komórki wprowadzeniu danych w sieci <xref:System.Windows.Forms.DataGridView> łatwo dostępne dla innych aplikacji za pomocą formantu <xref:System.Windows.Forms.Clipboard>. Wartości zaznaczonych komórek są konwertowane na ciągi i dodane do Schowka jako wartości tekstowe tabulacji wklejania w aplikacjach, takich jak Notatnik, a program Excel, a w formacie HTML tabeli wklejania w aplikacjach, takich jak Word.  
  
 Można skonfigurować komórki kopiowanie skopiować tylko wartości komórek, zawierają tekst nagłówka wiersza i kolumny w danych ze Schowka lub zawierają tekst nagłówka, tylko wtedy, gdy użytkownicy wybierają całego wierszy lub kolumn.  
  
 W zależności od trybu wyboru użytkownicy mogą wybierać wielu grup odłączonego komórek. Gdy użytkownik kopiuje komórek do Schowka, wierszy i kolumn z nie zaznaczone komórki nie są kopiowane. Wszystkie inne wierszy lub kolumn stają się wierszy i kolumn w tabeli danych skopiowany do Schowka. Niezaznaczone komórek w tych wierszy lub kolumn są kopiowane jako puste elementy zastępcze do Schowka.  
  
### <a name="to-enable-cell-copying"></a>Aby umożliwić kopiowanie komórki  
  
-   Ustaw <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A?displayProperty=nameWithType> właściwości.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#15)]
     [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#15)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kompletny kod pokazano, jak komórki są kopiowane do Schowka. Ten przykład zawiera przycisk, który kopiuje zaznaczonych komórek do Schowka przy użyciu <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A?displayProperty=nameWithType> — metoda i wyświetla zawartość Schowka w polu tekstowym.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/CS/datagridviewclipboarddemo.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewClipboardDemo#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewClipboardDemo/VB/datagridviewclipboarddemo.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten kod wymaga:  
  
-   Odwołania do zestawów N:System i N:System.Windows.Forms.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ClipboardCopyMode%2A>  
 <xref:System.Windows.Forms.DataGridView.GetClipboardContent%2A>  
 [Wybór i używanie schowka za pomocą kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)

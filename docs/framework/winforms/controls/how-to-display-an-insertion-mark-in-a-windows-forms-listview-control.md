---
title: 'Instrukcje: Wyświetlanie znacznika wstawiania w formancie ListView formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
ms.openlocfilehash: 6c87a4cb68baa15b5f670a23fb4e8ef7ce16cf6f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710060"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a>Instrukcje: Wyświetlanie znacznika wstawiania w formancie ListView formularzy Windows
Znacznika wstawiania w <xref:System.Windows.Forms.ListView> kontrolka pokazuje użytkowników punktu, w którym zostanie wstawiony przeciąganych elementów. Gdy użytkownik przeciąga element do punktu między dwoma innymi elementami, znacznika wstawiania pokazuje oczekiwanych nową lokalizację elementu.  
  
> [!NOTE]
>  Funkcja znacznika wstawiania jest dostępna tylko na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] gdy Twoja aplikacja wywołuje <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody. W starszych systemach operacyjnych każdy kod odnoszących się do znacznika wstawiania nie ma wpływu i znacznika wstawiania nie będą widoczne. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListViewInsertionMark>.  
  
 Na poniższej ilustracji przedstawiono znacznika wstawiania:  
  
 ![Znacznika wstawiania ListView](./media/listviewinsertion.gif "ListViewInsertion")  
  
 Poniższy przykład kodu pokazuje, jak korzystać z tej funkcji.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [Kontrolka ListView](listview-control-windows-forms.md)
- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
- [Przewodnik: Wykonywanie operacji przeciągania i upuszczania w formularzach Windows Forms](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)

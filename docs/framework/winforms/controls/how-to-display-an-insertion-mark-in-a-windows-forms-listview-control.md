---
title: 'Porady: wyświetlanie znacznika wstawiania w formancie ListView formularzy systemu Windows'
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
ms.openlocfilehash: 62d105dc3c0b9aabc3699c12259e1624ac31a3a0
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960438"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a>Porady: wyświetlanie znacznika wstawiania w formancie ListView formularzy systemu Windows
Znacznik wstawiania w kontrolce <xref:System.Windows.Forms.ListView> pokazuje użytkownikom punkt, w którym zostaną wstawione przeciągane elementy. Gdy użytkownik przeciągnie element do punktu między dwoma innymi elementami, znacznik wstawiania pokazuje oczekiwaną nową lokalizację elementu.  
  
 Na poniższej ilustracji przedstawiono znacznik wstawiania:  
  
 ![Zrzut ekranu pokazujący znacznik wstawiania elementu ListView.](./media/how-to-display-an-insertion-mark-in-a-windows-forms-listview-control/listview-insertion-mark.gif "ListViewInsertion")  
  
 Poniższy przykład kodu demonstruje, jak używać tej funkcji.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ListViewInsertionMark>
- [ListView, kontrolka](listview-control-windows-forms.md)
- [ListView, kontrolka — omówienie](listview-control-overview-windows-forms.md)
- [Przewodnik: wykonywanie operacji przeciągania i upuszczania w formularzach Windows Forms](../advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)

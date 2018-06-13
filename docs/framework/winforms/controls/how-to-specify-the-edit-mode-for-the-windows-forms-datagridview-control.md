---
title: 'Porady: określanie trybu edycji dla formantu DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: 5117dfe2e017cf4af1d352fdbf23c6599c0e56a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536276"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a>Porady: określanie trybu edycji dla formantu DataGridView formularzy systemu Windows
Domyślnie użytkownicy mogą edytować zawartość bieżącego <xref:System.Windows.Forms.DataGridView> komórki pola tekstowego, wpisując w nim lub naciskając klawisz F2. Komórka to umieszcza w trybie edycji, jeśli są spełnione wszystkie następujące warunki:  
  
-   Źródła danych obsługuje edycję.  
  
-   <xref:System.Windows.Forms.DataGridView> Formant jest włączony.  
  
-   <xref:System.Windows.Forms.DataGridView.EditMode%2A> Wartość właściwości jest <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.  
  
-   `ReadOnly` Właściwości komórek, wierszy, kolumny i kontroli mają ustawione `false`.  
  
 W trybie edycji użytkownik może zmienić wartość komórki i naciśnij klawisz ENTER, aby zatwierdzić zmiany lub ESC, aby przywrócić komórki do wartości oryginalnej.  
  
 Można skonfigurować <xref:System.Windows.Forms.DataGridView> , aby komórki wprowadza tryb edycji, jak staje się bieżącą komórką. W takim przypadku zachowanie klawiszy ENTER i ESC pozostanie niezmieniona, ale komórki pozostaje w trybie edycji po zatwierdzenia lub przywrócono wartość. Można również skonfigurować formantu, aby komórek przejść do trybu edycji tylko wtedy, gdy użytkownicy wpisują w komórce lub tylko, gdy użytkowników klawisz F2. Na koniec można zapobiec komórek trybu edycji z wyjątkiem przypadków, gdy jest wywoływana <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> metody.  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a>Aby zmienić tryb edycji formantu DataGridView  
  
-   Ustaw <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> właściwości do odpowiedniego <xref:System.Windows.Forms.DataGridViewEditMode> wyliczenia.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   Odwołuje się do <xref:System> i <xref:System.Windows.Forms> zestawów.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 [Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)

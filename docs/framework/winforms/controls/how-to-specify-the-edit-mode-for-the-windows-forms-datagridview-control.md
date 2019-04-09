---
title: 'Instrukcje: określanie trybu edycji dla kontrolki DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: 7cb9278cd311d211ef95df238b930970ae472d05
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080400"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a>Instrukcje: określanie trybu edycji dla kontrolki DataGridView formularzy systemu Windows
Domyślnie użytkownicy mogą edytować zawartość bieżącego <xref:System.Windows.Forms.DataGridView> komórka pole tekstu, wpisując ją lub naciskając klawisz F2. Komórka to umieszczenie w trybie edycji, jeśli są spełnione wszystkie następujące warunki:  
  
-   Źródła danych obsługuje edycję.  
  
-   <xref:System.Windows.Forms.DataGridView> Kontrolka jest włączona.  
  
-   <xref:System.Windows.Forms.DataGridView.EditMode%2A> Wartość właściwości jest <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.  
  
-   `ReadOnly` Właściwości komórek, wierszy, kolumny i kontrolki są gotowi do `false`.  
  
 W trybie edycji użytkownik może zmienić wartość komórki i naciśnij klawisz ENTER, aby zatwierdzić zmiany lub ESC, aby przywrócić komórki do oryginalnej wartości.  
  
 Można skonfigurować <xref:System.Windows.Forms.DataGridView> kontrolki komórki przejdzie do trybu edycji tak szybko, jak staje się bieżącej komórki. W tym przypadku zachowanie klawisze ENTER i ESC jest bez zmian, ale komórki pozostaje w trybie edycji po wartość nie zostanie przekazana lub przywrócić. Można również skonfigurować kontrolkę tak, aby komórek trybu edycji tylko wtedy, gdy użytkownicy wpisują się w komórce lub tylko gdy użytkownicy naciśnij klawisz F2. Na koniec można zapobiec komórek do trybu edycji z wyjątkiem sytuacji, gdy zostanie wywołana <xref:System.Windows.Forms.DataGridView.BeginEdit%2A> metody.  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a>Aby zmienić tryb edycji kontrolki DataGridView  
  
-   Ustaw <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> właściwości do odpowiednich <xref:System.Windows.Forms.DataGridViewEditMode> wyliczenia.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.  
  
-   Odwołuje się do <xref:System> i <xref:System.Windows.Forms> zestawów.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [Wprowadzanie danych w formancie DataGridView formularzy systemu Windows](data-entry-in-the-windows-forms-datagridview-control.md)

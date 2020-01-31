---
title: Określ tryb edycji kontrolki DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], edit mode
- data grids [Windows Forms], edit mode
ms.assetid: 93e117e8-94c4-411b-ba31-645e475ed85c
ms.openlocfilehash: c0318202a80f9a43f1b656201732ef032f430b5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743764"
---
# <a name="how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control"></a>Porady: określanie trybu edycji dla formantu DataGridView formularzy systemu Windows
Domyślnie użytkownicy mogą edytować zawartość bieżącej <xref:System.Windows.Forms.DataGridView> komórce pola tekstowego, wpisując ją lub naciskając klawisz F2. Spowoduje to umieszczenie komórki w trybie edycji, jeśli spełnione są wszystkie z następujących warunków:  
  
- Bazowe źródło danych obsługuje edytowanie.  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> jest włączona.  
  
- Wartość właściwości <xref:System.Windows.Forms.DataGridView.EditMode%2A> nie jest <xref:System.Windows.Forms.DataGridViewEditMode.EditProgrammatically>.  
  
- Właściwości `ReadOnly` komórki, wiersza, kolumny i kontrolki są ustawione na `false`.  
  
 W trybie edycji użytkownik może zmienić wartość komórki i nacisnąć klawisz ENTER, aby zatwierdzić zmianę lub ESC, aby przywrócić oryginalną wartość komórki.  
  
 Można skonfigurować kontrolkę <xref:System.Windows.Forms.DataGridView> tak, aby komórka przejdzie do trybu edycji, gdy tylko stanie się bieżącą komórką. Zachowanie klawiszy ENTER i ESC jest niezmienione w tym przypadku, ale komórka pozostaje w trybie edycji po zatwierdzeniu lub wycofaniu wartości. Można również skonfigurować kontrolkę tak, aby komórki były w trybie edycji tylko wtedy, gdy użytkownik naciśnie w komórce lub tylko wtedy, gdy użytkownicy naciśnij F2. Na koniec można uniemożliwić komórkom wprowadzanie trybu edycji z wyjątkiem wywołania metody <xref:System.Windows.Forms.DataGridView.BeginEdit%2A>.  
  
### <a name="to-change-the-edit-mode-of-a-datagridview-control"></a>Aby zmienić tryb edycji kontrolki DataGridView  
  
- Ustaw właściwość <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType> na odpowiednie Wyliczenie <xref:System.Windows.Forms.DataGridViewEditMode>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#067)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#067](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#067)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Kontrolka <xref:System.Windows.Forms.DataGridView> o nazwie `dataGridView1`.  
  
- Odwołania do zestawów <xref:System> i <xref:System.Windows.Forms>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>
- [Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)

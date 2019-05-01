---
title: Tryb wirtualny w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
ms.openlocfilehash: f284835578221ad1fe859f260e37bb829cd64b2d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009139"
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Tryb wirtualny w formancie DataGridView formularzy systemu Windows
Tryb wirtualny, można zarządzać interakcji między <xref:System.Windows.Forms.DataGridView> kontroli i pamięć podręczna danych niestandardowych. Aby zaimplementować trybu wirtualnego, należy ustawić <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwość `true` i obsługi co najmniej jeden zdarzenia opisane w tym temacie. Zazwyczaj będziesz obsługiwać co najmniej `CellValueNeeded` zdarzenie, które umożliwia kontrolki odnośnika wartości w pamięci podręcznej danych.  
  
## <a name="bound-mode-and-virtual-mode"></a>Tryb powiązane i trybu wirtualnego  
 Tryb wirtualny jest konieczne tylko wtedy, gdy trzeba uzupełnić lub zastępowania powiązanej. W trybie powiązanej ustawisz <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwości kontrolki automatycznie ładuje dane z określonego źródła i przesyła zmiany powrotu do tego użytkownika. Można kontrolować, które powiązane kolumny są wyświetlone, a źródło danych zazwyczaj obsługuje operacje, takie jak sortowania.  
  
## <a name="supplementing-bound-mode"></a>Powiązane tryb uzupełniania  
 Można je jednak uzupełnić tryb powiązanych, wyświetlając niepowiązanych kolumn oraz powiązane kolumny. To jest czasami nazywane "trybie mieszanym" i jest przydatny do wyświetlania czynności, np. steruje obliczone wartości lub interfejsu użytkownika (UI).  
  
 Ponieważ niepowiązanych kolumn znajdują się poza źródłem danych, są one ignorowane przez operacje sortowania źródła danych. W związku z tym, po włączeniu sortowania w trybie mieszanym, należy zarządzać niepowiązanych danych w lokalnej pamięci podręcznej i implementowanie trybu wirtualnego, aby umożliwić <xref:System.Windows.Forms.DataGridView> kontroli korzystać z niego.  
  
 Aby uzyskać więcej informacji o używaniu trybu wirtualnego, aby zachować wartości w kolumnach niepowiązanych, zobacz przykłady w <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType> właściwości i <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType> klasy tematy referencyjne.  
  
## <a name="replacing-bound-mode"></a>Zastępowanie tryb powiązane  
 Jeśli tryb powiązanej nie spełnia potrzeby związane z wydajnością, możesz zarządzać wszystkie dane w pamięci podręcznej niestandardowych za pomocą programów obsługi zdarzeń trybu wirtualnego. Na przykład umożliwia trybu wirtualnego zaimplementować mechanizm, który pobiera tylko ładowania danych just-in-time tak dużej ilości danych, z sieciowych bazy danych, jak to konieczne, aby uzyskać optymalną wydajność. Ten scenariusz jest szczególnie przydatne podczas pracy z dużymi ilościami danych ciągu z wolnym połączeniem sieciowym lub z komputerów klienckich, które mają ograniczoną ilość pamięci RAM lub miejsce do magazynowania.  
  
 Aby uzyskać więcej informacji na temat korzystania z trybu wirtualnego w scenariuszu just-in-time, zobacz [Implementowanie trybu wirtualnego przy użyciu ładowanie danych just in time w formancie DataGridView formularzy Windows](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).  
  
## <a name="virtual-mode-events"></a>Tryb wirtualny zdarzenia  
 Jeśli dane są tylko do odczytu, `CellValueNeeded` zdarzenia mogą być tylko zdarzenia, konieczne będzie obsługiwać. Dodatkowe zdarzenia trybu wirtualnego pozwalają włączyć określonych funkcji, takich jak użytkownik dokona edycji, wierszy i usuwanie i transakcji na poziomie wiersza.  
  
 Niektóre standardowe <xref:System.Windows.Forms.DataGridView> zdarzenia (takie jak zdarzenia, które występują, gdy użytkownicy Dodawanie lub usuwanie wierszy lub gdy komórka wartości są edytowane, przeanalizować, sprawdzania poprawności lub sformatowany) są przydatne w trybie wirtualnym, jak również. Może również obsługiwać zdarzenia, które umożliwiają Obsługa wartości, które zazwyczaj nie są przechowywane w źródle powiązanych danych, takie jak tekst etykietki narzędzia komórki, komórki i tekst błędu wiersza, komórki i danych menu skrótów dla wiersza i danych wysokość wiersza.  
  
 Aby uzyskać więcej informacji na temat Implementowanie trybu wirtualnego do zarządzania danymi odczytu/zapisu o zakresie zatwierdzenia na poziomie wiersza, zobacz [instruktażu: Implementowanie trybu wirtualnego w Windows formantu DataGridView formularzy](implementing-virtual-mode-wf-datagridview-control.md).  
  
 Na przykład, który implementuje trybu wirtualnego przy użyciu zakresu zatwierdzenia na poziomie komórki, zobacz <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> temat referencyjny właściwości.  
  
 Występują następujące zdarzenia, tylko gdy <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwość jest ustawiona na `true`.  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|Używane przez kontrolkę, można pobrać wartość komórki z pamięci podręcznej danych do wyświetlenia. To zdarzenie występuje tylko w przypadku komórek w niepowiązanych kolumn.|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|Używane przez formant do zatwierdzenia danych wejściowych użytkownika dla komórki w pamięci podręcznej danych. To zdarzenie występuje tylko w przypadku komórek w niepowiązanych kolumn.<br /><br /> Wywołaj <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> metody, zmieniając wartość w pamięci podręcznej poza <xref:System.Windows.Forms.DataGridView.CellValuePushed> program obsługi zdarzeń, aby upewnić się, że aktualna wartość jest wyświetlany w kontrolce i zastosować wszystkie tryby automatycznej zmiany rozmiaru aktualnie w.|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|Używane przez kontrolkę, do wskazywania potrzebę nowy wiersz w pamięci podręcznej danych.|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|Używane przez formant do ustalania, czy wiersz ma wszystkie Niewprowadzone zmiany.|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|Używane przez formant, aby wskazać, że wiersz powinien przywrócić jego wartości z pamięci podręcznej.|  
  
 Następujące zdarzenia są przydatne w trybie wirtualnym, ale można użyć niezależnie od <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> ustawienie właściwości.  
  
|Zdarzenia|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|Używane przez formant, aby wskazać, kiedy wiersze zostaną usunięte lub dodane, dzięki czemu możesz odpowiednio zaktualizować pamięć podręczną danych.|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|Używane przez formant do formatowania wartości komórek do wyświetlenia, a także analizowanie i sprawdzanie poprawności danych wejściowych użytkownika.|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|Używane przez formant do pobrania tekstu etykietki narzędzia w komórce po <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwość jest ustawiona lub <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwość `true`.<br /><br /> Komórka etykietki narzędzi są wyświetlane tylko wtedy, gdy <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> wartość właściwości jest `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|Używane przez formant do pobierania wiersza lub komórki tekst błędu podczas <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwość jest ustawiona lub <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwość `true`.<br /><br /> Wywołaj <xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> metody lub <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A> metody, gdy zmienią się tekst błędu wiersza lub komórki, aby upewnić się, że aktualna wartość jest wyświetlany w formancie.<br /><br /> Symbole błąd wierszy i komórek są wyświetlane po <xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A> i <xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A> wartości właściwości są `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|Używane przez formant do pobierania komórki lub wiersza <xref:System.Windows.Forms.ContextMenuStrip> podczas kontroli <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwość jest ustawiona lub <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwość `true`.|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|Używane przez formant do pobierania i przechowywania informacji wysokość wiersza w pamięci podręcznej danych. Wywołaj <xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A> metody, gdy zmiana informacji wysokość wiersza pamięci podręcznej poza <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed> program obsługi zdarzeń, aby upewnić się, że aktualna wartość jest używane na wyświetlaczu formantu.|  
  
## <a name="best-practices-in-virtual-mode"></a>Najlepsze rozwiązania w trybie wirtualnym  
 Przed zaimplementowaniem trybu wirtualnego w celu efektywnej pracy z dużymi ilościami danych, również należy upewnić się, że pracujesz wydajnie <xref:System.Windows.Forms.DataGridView> samej kontrolki. Aby uzyskać więcej informacji o efektywne wykorzystanie style komórki, automatycznej zmiany rozmiaru, opcji i udostępnianie wierszy, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy Windows](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Przewodnik: Implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)
- [Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)

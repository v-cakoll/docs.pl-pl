---
title: Tryb wirtualny w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
ms.openlocfilehash: 2e5724da4442bbfcb0928c864f78744b946acc18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Tryb wirtualny w formancie DataGridView formularzy systemu Windows
Tryb wirtualny, można zarządzać interakcji między <xref:System.Windows.Forms.DataGridView> kontroli i pamięci podręcznej danych niestandardowych. Aby zaimplementować trybie wirtualnym, ustaw <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwości `true` i obsługiwać co najmniej jednego zdarzenia opisane w tym temacie. Zwykle obsłuży co najmniej `CellValueNeeded` zdarzeń, dzięki czemu formant wyszukiwania wartości w pamięci podręcznej danych.  
  
## <a name="bound-mode-and-virtual-mode"></a>Tryb powiązane i tryb wirtualny  
 Tryb wirtualny jest konieczne tylko wtedy, gdy musisz uzupełnić lub powiązane tryb zastępowania. W trybie powiązane, należy ustawić <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwości formantu automatycznie ładuje dane z określonego źródła i przesyła zmiany powrotu do tego użytkownika. Można kontrolować, które powiązane kolumny są wyświetlone, a źródło danych obsługuje zwykle operacji, takich jak sortowania.  
  
## <a name="supplementing-bound-mode"></a>Tryb związanych uzupełniania  
 Tryb powiązanej można uzupełnić wyświetlając niepowiązanych kolumn oraz powiązane kolumny. To jest czasami nazywany "Tryb mieszany" i jest przydatne w przypadku wyświetlania czynności, takie jak kontrolki obliczone wartości lub interfejsu użytkownika (UI).  
  
 Ponieważ niepowiązanych kolumn są poza źródła danych, są one ignorowane przez operacje sortowania źródła danych. W związku z tym po włączeniu sortowania w trybie mieszanym, należy zarządzać niepowiązane dane w lokalnej pamięci podręcznej i implementowanie trybu wirtualnego, aby umożliwić <xref:System.Windows.Forms.DataGridView> kontroli interakcję z nią.  
  
 Aby uzyskać więcej informacji o korzystaniu z trybu wirtualnego do obsługi wartości w kolumnach niezwiązany, zobacz przykłady w <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType> właściwości i <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType> klasy tematy dokumentacji.  
  
## <a name="replacing-bound-mode"></a>Zastępowanie tryb powiązane  
 Jeśli tryb powiązania nie spełnia potrzeby w zakresie wydajności, można zarządzać wszystkich danych w pamięci podręcznej niestandardowych za pomocą programów obsługi zdarzeń w trybie wirtualnym. Na przykład umożliwia tryb wirtualny zaimplementować danych w czasie ładowania mechanizm, który pobiera tylko tyle danych z bazy danych sieci niezbędnej do uzyskania optymalnej wydajności. Ten scenariusz jest szczególnie przydatne podczas pracy z dużą ilością danych za pośrednictwem wolnym połączeniem sieciowym lub z komputerów klienckich, które mają ograniczoną ilość pamięci RAM lub miejsce do magazynowania.  
  
 Aby uzyskać więcej informacji na temat korzystania z trybu wirtualnego w scenariuszu w czasie, zobacz [Implementowanie trybu wirtualnego przy użyciu just in time w formancie DataGridView formularzy systemu Windows podczas ładowania danych](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).  
  
## <a name="virtual-mode-events"></a>Zdarzenia trybu wirtualnego  
 Jeśli dane są tylko do odczytu, `CellValueNeeded` zdarzeń mogą być tylko zdarzenia, konieczne będzie obsługiwać. Dodatkowe zdarzenia trybu wirtualnego pozwalają włączyć określonych funkcji, takich jak użytkownika, wiersz dodawania i usuwania i transakcji na poziomie wiersza.  
  
 Niektóre standardowe <xref:System.Windows.Forms.DataGridView> zdarzenia (takie jak zdarzeń występujących podczas użytkowników dodawanie lub usuwanie wierszy lub gdy komórka wartości edytowane, przeanalizować, sprawdzania poprawności lub sformatowany) są przydatne w trybie wirtualnym, a także. Można również obsługiwać zdarzenia, które pozwalają Obsługa wartości zazwyczaj nie są przechowywane w źródle powiązana z danymi, takie jak tekst etykietki narzędzia komórki, komórki i wiersza tekst błędu komórki i danych menu skrótów wiersza i danych wysokość wiersza.  
  
 Aby uzyskać więcej informacji na temat Implementowanie trybu wirtualnego do zarządzania danymi odczytu/zapisu z zakresem zatwierdzania na poziomie wiersza, zobacz [wskazówki: Implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
 Na przykład implementujący trybu wirtualnego przy użyciu zakresu zatwierdzania poziomie komórki zobacz <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> temat referencyjny właściwości.  
  
 Występują następujące zdarzenia, tylko gdy <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwość jest ustawiona na `true`.  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|Używane przez formant do pobierania wartości komórki z pamięci podręcznej danych do wyświetlenia. To zdarzenie występuje tylko w przypadku komórek w niepowiązanych kolumn.|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|Używany przez formant można przekazać danych wejściowych użytkownika dla komórki do pamięci podręcznej danych. To zdarzenie występuje tylko w przypadku komórek w niepowiązanych kolumn.<br /><br /> Wywołanie <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> metody, zmieniając wartość w pamięci podręcznej poza <xref:System.Windows.Forms.DataGridView.CellValuePushed> obsługi zdarzeń, aby upewnić się, że bieżąca wartość jest wyświetlana w formancie i zastosować wszystkie tryby automatycznej zmiany rozmiaru aktualnie obowiązującą.|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|Użyty przez formant, aby wskazać konieczność nowego wiersza w pamięci podręcznej danych.|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|Używane do ustalania, czy wiersz ma wszystkie Niewprowadzone zmiany.|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|Używany przez formant, aby wskazać, że wiersz należy przywrócić wartości w jego pamięci podręcznej.|  
  
 Następujące zdarzenia są przydatne w trybie wirtualnym, ale można użyć niezależnie od tego <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> ustawienie właściwości.  
  
|Zdarzenia|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|Użyty przez formant, aby wskazać, jeśli wiersze są usuwane lub dodano, dzięki czemu można odpowiednio aktualizacji pamięci podręcznej danych.|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|Używany przez formant do formatowania wartości komórek do wyświetlenia, a także analizy i sprawdzanie poprawności danych wejściowych użytkownika.|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|Używany przez formant do pobrania tekstu etykietki narzędzia komórki podczas <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwość jest ustawiona lub <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> jest właściwość `true`.<br /><br /> Etykietki narzędzi komórki są wyświetlane tylko wtedy, gdy <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> wartość właściwości jest `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|Używany przez formant do pobierania tekst błędu komórki lub wiersza po <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwość jest ustawiona lub <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> jest właściwość `true`.<br /><br /> Wywołanie <xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> metody lub <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A> metody po zmianie tekst błędu komórki lub wiersza, aby upewnić się, że bieżąca wartość jest wyświetlana w formancie.<br /><br /> Ikony błędów wierszy i komórek są wyświetlane po <xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A> i <xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A> wartości właściwości są `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|Używany przez formant do pobierania komórki lub wiersza <xref:System.Windows.Forms.ContextMenuStrip> podczas kontroli <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwość jest ustawiona lub <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> jest właściwość `true`.|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|Używany przez formant do pobierania lub przechowywania informacji o wysokości wiersza w pamięci podręcznej danych. Wywołanie <xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A> metody podczas zmiany informacji wysokość wiersza pamięci podręcznej poza <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed> obsługi zdarzeń, aby upewnić się, że bieżąca wartość jest używana w wyświetlanie formantu.|  
  
## <a name="best-practices-in-virtual-mode"></a>Najlepsze rozwiązania w trybie wirtualnym  
 Tryb wirtualny w przypadku wdrażania w celu efektywnej pracy z dużą ilością danych, również można upewnij się, że użytkownik pracuje wydajnie z <xref:System.Windows.Forms.DataGridView> samą kontrolką. Aby uzyskać więcej informacji o efektywne wykorzystanie style komórki, Rozmiar automatyczny wybór i udostępnianie wierszy, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 [Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 [Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)

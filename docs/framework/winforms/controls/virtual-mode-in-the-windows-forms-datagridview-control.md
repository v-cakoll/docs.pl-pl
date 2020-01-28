---
title: Tryb wirtualny w formancie DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
ms.openlocfilehash: 0d82f0fc9946e5b61ea171f2f5d2ab5690db0c71
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745445"
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Tryb wirtualny w formancie DataGridView formularzy systemu Windows
Za pomocą trybu wirtualnego można zarządzać interakcją między kontrolką <xref:System.Windows.Forms.DataGridView> i niestandardową pamięcią podręczną danych. Aby zaimplementować tryb wirtualny, należy ustawić właściwość <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> na `true` i obsłużyć jedno lub więcej zdarzeń opisanych w tym temacie. Zwykle zostanie obświetlona co najmniej `CellValueNeeded` zdarzenie, co umożliwia kontrolowanie wartości w pamięci podręcznej danych.  
  
## <a name="bound-mode-and-virtual-mode"></a>Tryb powiązany i tryb wirtualny  
 Tryb wirtualny jest niezbędny tylko w przypadku konieczności uzupełniania lub zastępowania trybu powiązanego. W trybie związanym Właściwość <xref:System.Windows.Forms.DataGridView.DataSource%2A> i formant automatycznie ładuje dane z określonego źródła i przesyła do niego zmiany wprowadzone przez użytkownika. Można kontrolować, które kolumny powiązane są wyświetlane, a źródło danych zazwyczaj obsługuje operacje, takie jak sortowanie.  
  
## <a name="supplementing-bound-mode"></a>Tryb powiązania uzupełniania  
 Można uzupełnić tryb powiązania, wyświetlając kolumny niepowiązane wraz z kolumnami związanymi. Jest to czasami nazywane "trybem mieszanym" i jest przydatne do wyświetlania takich elementów jak wartości obliczeniowe lub kontrolki interfejsu użytkownika.  
  
 Ponieważ niepowiązane kolumny znajdują się poza źródłem danych, są one ignorowane przez operacje sortowania źródła danych. W związku z tym, po włączeniu sortowania w trybie mieszanym, należy zarządzać niepowiązanych danymi w lokalnej pamięci podręcznej i zaimplementować tryb wirtualny, aby umożliwić sterowanie <xref:System.Windows.Forms.DataGridView>ą.  
  
 Aby uzyskać więcej informacji na temat używania trybu wirtualnego do obsługi wartości w kolumnach niepowiązanych, zobacz przykłady w tematach właściwości <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType> i informacje dotyczące klasy <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>.  
  
## <a name="replacing-bound-mode"></a>Zastępowanie trybu powiązanego  
 Jeśli tryb powiązania nie spełnia wymagań dotyczących wydajności, można zarządzać wszystkimi danymi w niestandardowej pamięci podręcznej za pomocą obsługi zdarzeń w trybie wirtualnym. Na przykład można użyć trybu wirtualnego do zaimplementowania mechanizmu ładowania danych just-in-Time, który pobiera tylko tyle danych z sieciową bazy danych, ile jest to konieczne w celu zapewnienia optymalnej wydajności. Ten scenariusz jest szczególnie przydatny podczas pracy z dużymi ilościami danych przez wolne połączenie sieciowe lub z komputerami klienckimi z ograniczoną ilością pamięci RAM lub miejsca do magazynowania.  
  
 Aby uzyskać więcej informacji na temat używania trybu wirtualnego w scenariuszu just-in-Time, zobacz [implementowanie trybu wirtualnego przy użyciu ładowania danych just-in-Time w kontrolce DataGridView Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).  
  
## <a name="virtual-mode-events"></a>Zdarzenia trybu wirtualnego  
 Jeśli dane są tylko do odczytu, zdarzenie `CellValueNeeded` może być jedynym zdarzeniem, które należy obsłużyć. Dodatkowe zdarzenia trybu wirtualnego umożliwiają włączenie określonych funkcji, takich jak edycje użytkowników, Dodawanie i usuwanie wierszy oraz transakcje na poziomie wierszy.  
  
 Niektóre standardowe zdarzenia <xref:System.Windows.Forms.DataGridView> (takie jak zdarzenia, które pojawiają się, gdy użytkownicy dodają lub usuwają wiersze lub w przypadku, gdy wartości komórek są edytowane, przeanalizowane, zweryfikowane lub sformatowane) są przydatne również w trybie wirtualnym. Możesz również obsługiwać zdarzenia, które pozwalają zachować wartości, które nie są zwykle przechowywane w powiązanym źródle danych, takie jak tekst etykietki narzędzia komórki, tekst błędu komórki i wiersza, dane menu skrótów komórki i wiersza oraz dane wysokości wiersza.  
  
 Aby uzyskać więcej informacji na temat implementowania trybu wirtualnego do zarządzania danymi odczytu/zapisu z zakresem zatwierdzania na poziomie wiersza, zobacz [Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).  
  
 Aby zapoznać się z przykładem, który implementuje tryb wirtualny z zakresem zatwierdzania na poziomie komórki, zobacz temat informacje o <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> właściwości.  
  
 Poniższe zdarzenia występują tylko wtedy, gdy właściwość <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> jest ustawiona na `true`.  
  
|Zdarzenie|Opis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|Używane przez formant do pobierania wartości komórki z pamięci podręcznej danych do wyświetlenia. To zdarzenie występuje tylko w przypadku komórek w kolumnach niepowiązanych.|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|Używane przez formant do zatwierdzania danych wejściowych użytkownika dla komórki w pamięci podręcznej danych. To zdarzenie występuje tylko w przypadku komórek w kolumnach niepowiązanych.<br /><br /> Wywołaj metodę <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> w przypadku zmiany wartości buforowanej poza procedurę obsługi zdarzeń <xref:System.Windows.Forms.DataGridView.CellValuePushed>, aby upewnić się, że bieżąca wartość jest wyświetlana w kontrolce i że obecnie zastosowano wszystkie tryby automatycznego ustalania rozmiarów.|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|Używane przez formant, aby wskazać potrzebę nowego wiersza w pamięci podręcznej danych.|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|Używane przez formant do określenia, czy wiersz zawiera niezatwierdzone zmiany.|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|Używane przez formant, aby wskazać, że wiersz ma zostać przywrócony do jego wartości pamięci podręcznej.|  
  
 Poniższe zdarzenia są przydatne w trybie wirtualnym, ale mogą być używane niezależnie od ustawienia właściwości <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>.  
  
|Zdarzenia|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|Używane przez formant do wskazania, kiedy wiersze są usuwane lub dodawane, co pozwala odpowiednio aktualizować pamięć podręczną danych.|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|Używane przez formant do formatowania wartości komórek do wyświetlania oraz do analizowania i sprawdzania poprawności danych wejściowych użytkownika.|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|Używane przez formant do pobierania tekstu etykietki narzędzia komórki po ustawieniu właściwości <xref:System.Windows.Forms.DataGridView.DataSource%2A> lub właściwość <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> jest `true`.<br /><br /> Etykietki narzędzi komórek są wyświetlane tylko wtedy, gdy wartość właściwości <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> jest `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|Używane przez formant do pobierania tekstu błędu komórki lub wiersza po ustawieniu właściwości <xref:System.Windows.Forms.DataGridView.DataSource%2A> lub właściwość <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> jest `true`.<br /><br /> Wywołaj metodę <xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> lub metodę <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A>, gdy zmienisz tekst błędu komórki lub wiersza, aby upewnić się, że bieżąca wartość jest wyświetlana w formancie.<br /><br /> Symbole błędów komórek i wierszy są wyświetlane, gdy wartości właściwości <xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A> i <xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A> są `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|Używane przez formant do pobierania komórki lub wiersza <xref:System.Windows.Forms.ContextMenuStrip>, gdy właściwość <xref:System.Windows.Forms.DataGridView.DataSource%2A> formantu jest ustawiona lub właściwość <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> jest `true`.|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|Używane przez formant do pobierania lub przechowywania informacji o wysokości wiersza w pamięci podręcznej danych. Wywołaj metodę <xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A>, zmieniając informacje o wysokości wiersza w pamięci podręcznej poza procedurę obsługi zdarzeń <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>, aby upewnić się, że bieżąca wartość jest używana podczas wyświetlania formantu.|  
  
## <a name="best-practices-in-virtual-mode"></a>Najlepsze rozwiązania w trybie wirtualnym  
 W przypadku wdrażania trybu wirtualnego w celu wydajnej pracy z dużymi ilościami danych warto również upewnić się, że pracujesz efektywnie z samą kontrolką <xref:System.Windows.Forms.DataGridView>. Aby uzyskać więcej informacji na temat efektywnego wykorzystania stylów komórek, automatycznego ustalania rozmiarów, opcji i udostępniania wierszy, zobacz [najlepsze rozwiązania dotyczące skalowania Windows Forms formantu DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Najlepsze praktyki dotyczące skalowania kontrolki DataGridView formularzy Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)
- [Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)

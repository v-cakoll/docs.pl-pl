---
title: Tryby wyświetlania danych w formancie DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
ms.openlocfilehash: ad6be647e3a36904b055fd6771f539df28938fab
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744010"
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Tryby wyświetlania danych w formancie DataGridView formularzy systemu Windows
Formant <xref:System.Windows.Forms.DataGridView> może wyświetlać dane w trzech różnych trybach: powiązane, niepowiązane i wirtualne. Wybierz najbardziej odpowiedni tryb w zależności od wymagań.  
  
## <a name="unbound"></a>Niepowiązanych  
 Tryb niezwiązany jest odpowiedni do wyświetlania stosunkowo małych ilości danych, którymi można zarządzać programowo. Nie dołączysz kontrolki <xref:System.Windows.Forms.DataGridView> bezpośrednio do źródła danych w trybie związanym. Zamiast tego należy wypełnić formant samodzielnie, zazwyczaj przy użyciu metody <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType>.  
  
 Tryb niezwiązany może być szczególnie przydatny w przypadku danych statycznych, tylko do odczytu lub w przypadku, gdy chcesz dostarczyć własny kod, który współdziała z zewnętrznym magazynem danych. Jeśli chcesz, aby użytkownicy pracowali z zewnętrznym źródłem danych, zazwyczaj będziesz używać trybu powiązanego.  
  
 Aby zapoznać się z przykładem korzystającym z niepowiązanego <xref:System.Windows.Forms.DataGridView>tylko do odczytu, zobacz [How to: Create an unboundd Windows Forms DataGridView Control](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="bound"></a>Bound  
 Tryb powiązania jest odpowiedni do zarządzania danymi przy użyciu interakcji automatycznej z magazynem danych. Możesz dołączyć formant <xref:System.Windows.Forms.DataGridView> bezpośrednio do źródła danych, ustawiając właściwość <xref:System.Windows.Forms.DataGridView.DataSource%2A>. Gdy formant jest powiązany z danymi, wiersze danych są wypychane i ściągane bez konieczności jawnego zarządzania. Gdy właściwość <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> jest `true`, każda kolumna w źródle danych spowoduje, że odpowiednia kolumna zostanie utworzona w formancie. Jeśli wolisz utworzyć własne kolumny, możesz ustawić tę właściwość na `false` i użyć właściwości <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> do powiązania każdej kolumny podczas jej konfigurowania. Jest to przydatne, gdy chcesz użyć typu kolumny innego niż typy, które są generowane domyślnie. Aby uzyskać więcej informacji, zobacz [typy kolumn w kontrolce DataGridView Windows Forms](column-types-in-the-windows-forms-datagridview-control.md).  
  
 Aby zapoznać się z przykładem korzystającym z powiązanej kontrolki <xref:System.Windows.Forms.DataGridView>, zobacz [Przewodnik: sprawdzanie poprawności danych w kontrolce DataGridView Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
 Możesz również dodać niepowiązane kolumny do kontrolki <xref:System.Windows.Forms.DataGridView> w trybie związanym. Jest to przydatne, gdy chcesz wyświetlić kolumnę przycisków lub łączy, które umożliwiają użytkownikom wykonywanie akcji w określonych wierszach. Przydatne jest również wyświetlanie kolumn z wartościami obliczanymi z kolumn powiązanych. Możesz wypełnić wartości komórek dla kolumn obliczeniowych w programie obsługi dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellFormatting>. Jeśli jednak używasz <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> jako źródła danych, możesz użyć właściwości <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType>, aby zamiast tego utworzyć kolumnę obliczeniową. W takim przypadku formant <xref:System.Windows.Forms.DataGridView> będzie traktowany jako kolumna obliczeniowa, podobnie jak każda inna kolumna w źródle danych.  
  
 Sortowanie według niepowiązanych kolumn w trybie związanym nie jest obsługiwane. W przypadku utworzenia niepowiązanej kolumny w trybie związanym, który zawiera wartości edytowalne przez użytkownika, należy zaimplementować tryb wirtualny, aby zachować te wartości, gdy kontrolka jest posortowana według kolumny powiązanej.  
  
## <a name="virtual"></a>Wirtualnej  
 W trybie wirtualnym można zaimplementować własne operacje zarządzania danymi. Jest to niezbędne do utrzymania wartości kolumn niepowiązanych w trybie związanym, gdy formant jest sortowany według kolumn powiązanych. Jednak podstawowe użycie trybu wirtualnego polega na optymalizacji wydajności w przypadku współpracy z dużymi ilościami danych.  
  
 Możesz dołączyć formant <xref:System.Windows.Forms.DataGridView> do pamięci podręcznej, którą zarządzasz, i kontrolować kod podczas wypychania i ściągania wierszy danych. Aby zapewnić niewielki rozmiar pamięci, pamięć podręczna powinna być podobna do liczby aktualnie wyświetlanych wierszy. Gdy użytkownik przewija nowe wiersze do widoku, kod zażąda nowych danych z pamięci podręcznej i opcjonalnie opróżnia stare dane z pamięci.  
  
 Podczas wdrażania trybu wirtualnego należy śledzić, kiedy nowy wiersz jest potrzebny w modelu danych i kiedy wycofać dodanie nowego wiersza. Dokładna implementacja tej funkcji będzie zależeć od implementacji modelu danych i semantyki transakcji modelu danych. czy zakres zatwierdzania jest na poziomie komórki czy wiersza.  
  
 Aby uzyskać więcej informacji na temat trybu wirtualnego, zobacz [Tryb wirtualny w kontrolce DataGridView Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md). Aby zapoznać się z przykładem, który pokazuje, jak używać zdarzeń trybu wirtualnego, zobacz [Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
- [Przewodnik: tworzenie niepowiązanej kontrolki DataGridView formularzy Windows Forms](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [Instrukcje: wiązanie danych z kontrolką DataGridView formularzy Windows Forms](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
- [Tryb wirtualny w kontrolce DataGridView formularzy Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)

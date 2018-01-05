---
title: "Tryby wyświetlania danych w formancie DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92b66d27683fad4adf0ed2179a5bb29ef6220e3e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Tryby wyświetlania danych w formancie DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Formant może wyświetlać dane w trzech różnych trybach: powiązane, niezwiązanej i wirtualnych. Wybierz najbardziej odpowiedniego tryb, w zależności od wymagań.  
  
## <a name="unbound"></a>Anulowano powiązania  
 Tryb niepowiązany nadaje się do wyświetlania względnie niewielkich ilości danych, które można programowo zarządzać. Nie dołączaj <xref:System.Windows.Forms.DataGridView> kontroli bezpośrednio ze źródłem danych w trybie powiązane. Zamiast tego możesz musi wypełnić kontrolki samodzielnie, zwykle za pomocą <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> metody.  
  
 Tryb niepowiązany może być szczególnie przydatne dla danych statycznych, tylko do odczytu, lub gdy chcesz zapewnić swoim własnym kodem, który współdziała z magazynem danych zewnętrznych. Użytkownikom na interakcję z zewnętrznego źródła danych, należy jednak zwykle użyjesz trybu powiązania.  
  
 Na przykład, który używa tylko do odczytu niepowiązane <xref:System.Windows.Forms.DataGridView>, zobacz [jak: utworzyć niezwiązanego formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="bound"></a>Powiązany  
 Tryb powiązanej nadaje się do zarządzania danych przy użyciu automatycznego interakcji z magazynem danych. Możesz dołączyć <xref:System.Windows.Forms.DataGridView> kontroli bezpośrednio do źródła danych przez ustawienie <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwości. Kontrolka jest powiązana z danymi, wiersze danych są wypychana i pobierane bez konieczności jawnego zarządzania ze strony użytkownika. Gdy <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> właściwość jest `true`, każdej kolumny w źródle danych spowoduje przerwanie odpowiadającej mu kolumny, która ma zostać utworzony w formancie. Jeśli wolisz utworzyć własne kolumny tę właściwość można ustawić `false` i użyj <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> właściwości do powiązania każdej kolumny, gdy jest skonfigurowany. Jest to przydatne, jeśli chcesz użyć kolumny typu innego niż typów, generowanych przez domyślny. Aby uzyskać więcej informacji, zobacz [typy kolumn w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md).  
  
 Na przykład, który używa powiązanej <xref:System.Windows.Forms.DataGridView> sterowania, zobacz [wskazówki: Sprawdzanie poprawności danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
 Możesz także dodać niepowiązanych kolumn do <xref:System.Windows.Forms.DataGridView> formant w trybie powiązania. Jest to przydatne, jeśli chcesz wyświetlić kolumnę przyciski lub linki, które użytkownicy mogą wykonywać działania na określonych wierszy. Warto również wyświetlenie kolumn z wartościami obliczana na podstawie powiązane kolumny. Można go wypełnić wartości komórek w kolumnach obliczeniowych w procedurze obsługi dla <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzeń. Jeśli używasz <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> jako źródło danych, jednak warto użyć <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType> właściwość, aby zamiast tego utworzyć kolumnę obliczeniową. W takim przypadku <xref:System.Windows.Forms.DataGridView> formant będzie traktować kolumny obliczeniowej, podobnie jak inne kolumny w źródle danych.  
  
 Sortowanie według niepowiązanych kolumn w trybie powiązania nie jest obsługiwane. Jeśli tworzysz niepowiązanych kolumn w trybie powiązania, który zawiera wartości można edytować użytkownika, musi implementować trybu wirtualnego do obsługi tych wartości, gdy formant jest sortowana według powiązane kolumny.  
  
## <a name="virtual"></a>Wirtualny  
 Tryb wirtualny można zaimplementować własne operacje zarządzania danych. Jest to konieczne do zachowania wartości niepowiązanych kolumn w trybie powiązane, gdy formant jest sortowana według powiązane kolumny. Podstawowym zastosowaniem trybie wirtualnym, jest jednak aby zoptymalizować wydajność podczas interakcji z dużych ilości danych.  
  
 Możesz dołączyć <xref:System.Windows.Forms.DataGridView> kontroli do pamięci podręcznej, którą zarządzasz i formantów kodu podczas wypychana i pobierane wiersze danych. Aby zachować zużycie pamięci jest mała, pamięci podręcznej powinien być podobny rozmiar liczba aktualnie wyświetlanych wierszy. Gdy użytkownik przewija nowych wierszy w widoku, kod żądania nowych danych z pamięci podręcznej i opcjonalnie opróżnia stare dane z pamięci.  
  
 Są Implementowanie trybu wirtualnego, należy sprawdzić, kiedy nowy wiersz nie jest konieczna w modelu danych, a podczas wycofywania dodanie nowego wiersza. Dokładne stosowania tej funkcji zależy od implementacji modelu danych i semantyki transakcji modelu danych; Określa, czy zakres zatwierdzania jest na poziomie komórki lub wiersza.  
  
 Aby uzyskać więcej informacji o trybie wirtualnym, zobacz [tryb wirtualny w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md). Aby uzyskać przykład przedstawia sposób użycia zdarzeń w trybie wirtualnym, zobacz [wskazówki: Implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>  
 [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [Przewodnik: tworzenie niepowiązanej kontrolki DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 [Instrukcje: wiązanie danych z kontrolką DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 [Tryb wirtualny w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [Przewodnik: implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)

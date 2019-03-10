---
title: Tryby wyświetlania danych w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
ms.openlocfilehash: 86eda82cad778978711520bc2951a7a35d133753
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703082"
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Tryby wyświetlania danych w formancie DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Kontrolki mogą wyświetlać dane w trzech różnych trybach: powiązanej niepowiązanych i wirtualnych. Wybierz najbardziej odpowiedni tryb, w zależności od wymagań.  
  
## <a name="unbound"></a>Anulowano powiązanie  
 Tryb niepowiązany nadaje się do wyświetlania stosunkowo małe ilości danych, które można zarządzać programowo. Nie dołączaj <xref:System.Windows.Forms.DataGridView> kontroli bezpośrednio ze źródłem danych, tak jak w trybie powiązanej. Zamiast tego możesz musi wypełnić kontrolki samodzielnie, zazwyczaj przy użyciu <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> metody.  
  
 Tryb niepowiązany może być szczególnie przydatne w przypadku danych statycznych, tylko do odczytu lub gdy chcesz udostępnić własny kod, który wchodzi w interakcje przy użyciu magazynu danych zewnętrznych. Jeśli chcesz, aby użytkownicy mogli wchodzić w interakcje z zewnętrznego źródła danych, jednak zwykle użyjesz powiązanej trybu.  
  
 Aby uzyskać przykład, który używa tylko do odczytu niepowiązanych <xref:System.Windows.Forms.DataGridView>, zobacz [jak: Tworzenie formantu DataGridView formularzy Windows niepowiązanych](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="bound"></a>powiązane  
 Tryb powiązanej jest odpowiednie do zarządzania danymi przy użyciu automatycznego interakcji z magazynem danych. Możesz dołączyć <xref:System.Windows.Forms.DataGridView> kontroli bezpośrednio ze swoim źródłem danych, ustawiając <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwości. Gdy kontrolka jest powiązana z danymi, wiersze danych są wypychane i ściągane bez konieczności jawnego zarządzania ze strony użytkownika. Gdy <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> właściwość `true`, każdej kolumny w źródle danych spowoduje, że odpowiednia kolumna ma być utworzony w kontrolce. Jeśli wolisz utworzyć własne kolumny, możesz ustawić tę właściwość, `false` i użyj <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> właściwości powiązania każdej kolumny, gdy jest skonfigurowany. Jest to przydatne, gdy użytkownik chce użyć kolumny typu innego niż typy, które są generowane domyślnie. Aby uzyskać więcej informacji, zobacz [typy kolumn w formancie DataGridView formularzy Windows](column-types-in-the-windows-forms-datagridview-control.md).  
  
 Na przykład, który używa granicę <xref:System.Windows.Forms.DataGridView> sterowania, zobacz [instruktażu: Sprawdzanie poprawności danych w Windows formantu DataGridView formularzy](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
 Możesz również dodać niepowiązanych kolumn do <xref:System.Windows.Forms.DataGridView> w trybie powiązanej. Jest to przydatne, gdy mają być wyświetlane w kolumnie przycisków lub łączy, które umożliwiają użytkownikom do wykonywania akcji względem wybranych wierszy. Jest to również przydatne w celu wyświetlenia kolumn z wartościami obliczonym na podstawie powiązane kolumny. Możesz wypełnić wartości komórek kolumny obliczeniowe w obsłudze dla <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzeń. Jeśli używasz <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> jako źródło danych, jednak warto użyć <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType> właściwości, aby zamiast tego utworzyć kolumnę obliczeniową. W tym przypadku <xref:System.Windows.Forms.DataGridView> kontroli traktują kolumnę obliczeniową, podobnie jak dowolnej innej kolumny w źródle danych.  
  
 Sortowanie według niepowiązanych kolumn w powiązanej tryb nie jest obsługiwane. Jeśli tworzysz niepowiązanych kolumn w powiązanej trybie, który zawiera wartości użytkownika można edytować, należy zaimplementować trybu wirtualnego, aby zachować te wartości, gdy kontrolka jest posortowana według kolumny powiązanej.  
  
## <a name="virtual"></a>Wirtualny  
 Przy użyciu trybu wirtualnego można zaimplementować własną operacji zarządzania danymi. Jest to niezbędne w celu zachowania w trybie powiązanych wartości niepowiązanych kolumn, gdy kontrolka jest posortowana według kolumny powiązanej. Podstawowym zastosowaniem trybu wirtualnego jest jednak w celu zoptymalizowania wydajności podczas korzystania z dużych ilości danych.  
  
 Możesz dołączyć <xref:System.Windows.Forms.DataGridView> formantu do pamięci podręcznej, którą można zarządzać i kontrolkom kodu, gdy wiersze danych są wypychane i pobierane. Aby zachować zużycie pamięci jest mała, pamięci podręcznej powinien być podobny rozmiar liczby wierszy, które aktualnie wyświetlany. Gdy użytkownik przewija widok nowych wierszy w widoku, Twój kod żąda nowych danych z pamięci podręcznej i opcjonalnie opróżnia stare dane z pamięci.  
  
 Są Implementowanie trybu wirtualnego, należy sprawdzić, kiedy nowy wiersz nie jest konieczna w modelu danych, a podczas wycofywania dodanie nowego wiersza. Dokładna implementację tej funkcji zależy od implementacji modelu danych i semantyka transakcja modelu danych; czy zakres zatwierdzenia jest na poziomie wiersza lub komórki.  
  
 Aby uzyskać więcej informacji na temat trybu wirtualnego zobacz [trybu wirtualnego w formancie DataGridView formularzy Windows](virtual-mode-in-the-windows-forms-datagridview-control.md). Na przykład, który pokazuje, jak używać zdarzenia trybu wirtualnego, zobacz [instruktażu: Implementowanie trybu wirtualnego w Windows formantu DataGridView formularzy](implementing-virtual-mode-wf-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>
- [Wyświetlanie danych w kontrolce DataGridView formularzy Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Typy kolumn w kontrolce DataGridView formularzy Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
- [Przewodnik: Tworzenie Windows niezwiązanego formantu DataGridView formularzy](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [Instrukcje: Powiązanie danych w kontrolce DataGridView formularzy Windows Forms](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
- [Tryb wirtualny w kontrolce DataGridView formularzy Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Przewodnik: Implementowanie trybu wirtualnego w kontrolce DataGridView formularzy Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)

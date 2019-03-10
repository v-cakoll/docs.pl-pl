---
title: Używanie wiersza dla nowych rekordów w formancie DataGridView formularzy systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
ms.openlocfilehash: 041738ba375022be7c80526f25e5761314dffbf1
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703923"
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>Używanie wiersza dla nowych rekordów w formancie DataGridView formularzy systemu Windows
Kiedy używasz <xref:System.Windows.Forms.DataGridView> do edycji danych w aplikacji, często można zapewnić użytkownikom możliwość dodawania nowych wierszy danych w magazynie danych. <xref:System.Windows.Forms.DataGridView> Kontrolka obsługuje tę funkcję, zapewniając wiersza dla nowych rekordów, który jest zawsze wyświetlany jako ostatni wiersz. Jest ona oznaczona symbolem gwiazdki (*) w jej nagłówku wiersza. W poniższych sekcjach omówiono niektóre czynności, należy rozważyć, gdy program za pomocą wiersza dla nowych rekordów jest włączona.  
  
## <a name="displaying-the-row-for-new-records"></a>Wyświetlanie wiersza dla nowych rekordów  
 Użyj <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> właściwości, aby wskazać, czy wyświetlany jest wiersz dla nowych rekordów. Wartość domyślna tej właściwości to `true`.  
  
 Dla przypadku powiązany z danymi, wyświetlany jest wiersza dla nowych rekordów Jeśli <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> właściwości formantu i <xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType> właściwość źródła danych są `true`. Jeśli jest jeden `false` , a następnie wiersza nie będą wyświetlane.  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>Wypełnianie wiersza dla nowych rekordów z danymi domyślnymi  
 Gdy użytkownik wybierze wiersza dla nowych rekordów jako bieżący wiersz <xref:System.Windows.Forms.DataGridView> kontrolować zgłasza <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> zdarzeń.  
  
 To zdarzenie umożliwia dostęp do nowego <xref:System.Windows.Forms.DataGridViewRow> i umożliwia wypełnianie nowy wiersz z danymi domyślnymi. Aby uzyskać więcej informacji, zobacz [jak: Określanie wartości domyślnych dla nowych wierszy w kontrolce DataGridView formularzy Windows Forms](specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>Kolekcja wierszy  
 Wiersz dla nowych rekordów jest zawarty w <xref:System.Windows.Forms.DataGridView> kontrolki <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji ale zachowuje się inaczej w dwóch aspektach:  
  
-   Nie można usunąć wiersza dla nowych rekordów z <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji programowo. <xref:System.InvalidOperationException> Jest generowany, jeśli to jest podejmowana próba. Użytkownik nie może również usunąć wiersza dla nowych rekordów. <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType> Metoda nie powoduje usunięcia tego wiersza z <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji.  
  
-   Można dodać nie wiersz po wierszu dla nowych rekordów. <xref:System.InvalidOperationException> Jest wywoływane, jeśli ta próba zostanie podjęta. W rezultacie wiersza dla nowych rekordów jest zawsze ostatni wiersz w <xref:System.Windows.Forms.DataGridView> kontroli. Metody na <xref:System.Windows.Forms.DataGridViewRowCollection> , dodawanie wierszy —<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, i <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>— wszystkie wywołania metod wstawiania wewnętrznie po wiersza dla nowych rekordów jest obecny.  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>Dostosowywanie Visual wiersza dla nowych rekordów  
 Po utworzeniu wiersza dla nowych rekordów opiera się na wiersza określonego przez <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> właściwości. Wszystkie style komórki, które nie zostały określone dla tego wiersza są dziedziczone z innych właściwości. Aby uzyskać więcej informacji na temat dziedziczenie stylów komórki, zobacz [style komórki w formancie DataGridView formularzy Windows](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Wartości początkowe, są wyświetlane przez komórki w wierszu nowe rekordy są pobierane z każdej komórki <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> właściwości. Dla komórki typu <xref:System.Windows.Forms.DataGridViewImageCell>, właściwość ta zwraca obraz zastępczy. W przeciwnym razie ta właściwość zwraca `null`. Można zastąpić tę właściwość, aby zwrócić wartość niestandardową. Jednak te wartości początkowej może być zastąpiony <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> program obsługi zdarzeń, gdy zespół wprowadza wiersza dla nowych rekordów.  
  
 Standardowych ikon dla tego wiersza nagłówka, które znajdują się strzałki, lub gwiazdkę, nie są publicznie widoczne. Jeśli chcesz dostosować ikony, konieczne będzie utworzenie niestandardowego <xref:System.Windows.Forms.DataGridViewRowHeaderCell> klasy.  
  
 Użyj standardowych ikon <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellStyle> używany przez komórki nagłówka wiersza. Nie są renderowane standardowych ikon, jeśli nie ma wystarczającej ilości miejsca, aby wyświetlić je całkowicie.  
  
 Jeśli komórki nagłówka wiersza ma wartość ciągu, a jeśli nie ma wystarczającej ilości miejsca na tekst i ikona, ikona zostanie usunięte najpierw.  
  
## <a name="sorting"></a>Sortowanie  
 W trybie niepowiązanych nowe rekordy są zawsze dodawane do końca <xref:System.Windows.Forms.DataGridView> nawet wtedy, gdy użytkownik ma sortować zawartość <xref:System.Windows.Forms.DataGridView>. Użytkownik będzie musiał ponownie zastosować sortowania, aby posortować wiersza w odpowiednie miejsce; to zachowanie jest podobny do <xref:System.Windows.Forms.ListView> kontroli.  
  
 W danych tryby powiązane i wirtualnych zachowania wstawiania, po zastosowaniu sortowania są zależne od implementacji modelu danych. Aby uzyskać [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], wiersz jest natychmiast posortowane w prawidłowym położeniu.  
  
## <a name="other-notes-on-the-row-for-new-records"></a>Inne uwagi dotyczące wiersza dla nowych rekordów  
 Nie można ustawić <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> właściwość ten wiersz, aby `false`. <xref:System.InvalidOperationException> Jest wywoływane, jeśli ta próba zostanie podjęta.  
  
 Wiersz dla nowych rekordów zawsze jest tworzony w stanie niezaznaczone.  
  
## <a name="virtual-mode"></a>Tryb wirtualny  
 Jeśli są Implementowanie trybu wirtualnego, należy śledzić razie wiersza dla nowych rekordów w modelu danych i kiedy należy wycofać dodanie wiersza. Dokładna implementację tej funkcji zależy od implementacji modelu danych i jego semantyki transakcji na przykład, czy zakres zatwierdzenia znajduje się na poziomie wiersza lub komórki. Aby uzyskać więcej informacji, zobacz [trybu wirtualnego w formancie DataGridView formularzy Windows](virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: Określanie wartości domyślnych dla nowych wierszy w kontrolce DataGridView formularzy Windows Forms](specify-default-values-for-new-rows-in-the-datagrid.md)

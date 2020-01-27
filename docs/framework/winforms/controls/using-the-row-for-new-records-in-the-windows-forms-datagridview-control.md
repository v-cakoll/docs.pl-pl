---
title: Używanie wiersza dla nowych rekordów w formancie DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
ms.openlocfilehash: 2fcd35f8c4d04909cdbc26f6a4293fdd570385b8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728337"
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>Używanie wiersza dla nowych rekordów w formancie DataGridView formularzy systemu Windows
Gdy używasz <xref:System.Windows.Forms.DataGridView> do edytowania danych w aplikacji, często chcesz dać użytkownikom możliwość dodawania nowych wierszy danych do magazynu danych. Formant <xref:System.Windows.Forms.DataGridView> obsługuje tę funkcję, dostarczając wiersz dla nowych rekordów, który jest zawsze wyświetlany jako ostatni wiersz. Jest oznaczona symbolem gwiazdki (*) w nagłówku wiersza. W poniższych sekcjach omówiono niektóre zagadnienia, które należy wziąć pod uwagę podczas programu z wierszem dla nowych rekordów włączonych.  
  
## <a name="displaying-the-row-for-new-records"></a>Wyświetlanie wiersza dla nowych rekordów  
 Użyj właściwości <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>, aby wskazać, czy ma być wyświetlany wiersz dla nowych rekordów. Wartość domyślna tej właściwości jest `true`.  
  
 Dla przypadku powiązanego z danymi wiersz dla nowych rekordów będzie wyświetlany, jeśli właściwości <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> kontrolki i właściwości <xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType> źródła danych są `true`. Jeśli jest `false`, wiersz nie będzie wyświetlany.  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>Zapełnianie wiersza dla nowych rekordów danymi domyślnymi  
 Gdy użytkownik wybierze wiersz dla nowych rekordów jako bieżący wiersz, formant <xref:System.Windows.Forms.DataGridView> wywołuje zdarzenie <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.  
  
 To zdarzenie zapewnia dostęp do nowego <xref:System.Windows.Forms.DataGridViewRow> i umożliwia wypełnienie nowego wiersza danymi domyślnymi. Aby uzyskać więcej informacji, zobacz [How to: Określanie wartości domyślnych dla nowych wierszy w kontrolce DataGridView Windows Forms](specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>Kolekcja wierszy  
 Wiersz dla nowych rekordów jest zawarty w kolekcji <xref:System.Windows.Forms.DataGridView.Rows%2A> kontrolki <xref:System.Windows.Forms.DataGridView>, ale zachowuje się inaczej w dwóch aspektach:  
  
- Nie można programowo usunąć wiersza dla nowych rekordów z kolekcji <xref:System.Windows.Forms.DataGridView.Rows%2A>. Zostanie wygenerowany <xref:System.InvalidOperationException>, jeśli zostanie podjęta taka próba. Użytkownik nie może również usunąć wiersza dla nowych rekordów. Metoda <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType> nie usuwa tego wiersza z kolekcji <xref:System.Windows.Forms.DataGridView.Rows%2A>.  
  
- Nie można dodać wiersza po wierszu dla nowych rekordów. Jeśli zostanie podjęta próba, zostanie zgłoszone <xref:System.InvalidOperationException>. W efekcie wiersz dla nowych rekordów jest zawsze ostatnim wierszem formantu <xref:System.Windows.Forms.DataGridView>. Metody <xref:System.Windows.Forms.DataGridViewRowCollection>, które dodają wiersze —<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>i <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>— wszystkie metody wstawiania wywołań wewnętrznie w momencie obecności wiersza dla nowych rekordów.  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>Wizualne Dostosowywanie wiersza dla nowych rekordów  
 Po utworzeniu wiersza dla nowych rekordów jest on oparty na wierszu określonym przez właściwość <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>. Wszystkie style komórek, które nie są określone dla tego wiersza są dziedziczone z innych właściwości. Aby uzyskać więcej informacji na temat dziedziczenia stylu komórki, zobacz [style komórek w kontrolce DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Początkowe wartości wyświetlane przez komórki w wierszu dla nowych rekordów są pobierane z właściwości <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> każdej komórki. W przypadku komórek typu <xref:System.Windows.Forms.DataGridViewImageCell>ta właściwość zwraca obraz zastępczy. W przeciwnym razie ta właściwość zwraca `null`. Można zastąpić tę właściwość, aby zwracała wartość niestandardową. Jednak te początkowe wartości mogą zostać zastąpione przez program obsługi zdarzeń <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>, gdy fokus przejdzie do wiersza dla nowych rekordów.  
  
 Standardowe ikony dla nagłówka tego wiersza, które są strzałką lub gwiazdką, nie są ujawniane publicznie. Jeśli chcesz dostosować ikony, musisz utworzyć niestandardową klasę <xref:System.Windows.Forms.DataGridViewRowHeaderCell>.  
  
 Standardowe ikony używają właściwości <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> <xref:System.Windows.Forms.DataGridViewCellStyle> używanej przez komórkę nagłówka wiersza. Standardowe ikony nie są renderowane, jeśli nie ma wystarczającej ilości miejsca, aby wyświetlić je w całości.  
  
 Jeśli komórka nagłówka wiersza ma ustawioną wartość ciągu i jeśli nie ma wystarczającej ilości miejsca dla tekstu i ikony, ikona zostanie porzucona jako pierwsza.  
  
## <a name="sorting"></a>Sortowanie  
 W trybie niezwiązanym nowe rekordy są zawsze dodawane do końca <xref:System.Windows.Forms.DataGridView>, nawet jeśli Użytkownik pobrał zawartość <xref:System.Windows.Forms.DataGridView>. Użytkownik będzie musiał ponownie zastosować sortowanie, aby posortować wiersz w odpowiedniej pozycji; to zachowanie działa podobnie jak w przypadku kontrolki <xref:System.Windows.Forms.ListView>.  
  
 W przypadku związanych z danymi i trybami wirtualnymi zachowanie podczas wstawiania w przypadku zastosowania sortowania będzie zależne od implementacji modelu danych. W przypadku ADO.NET wiersz jest natychmiast sortowany do poprawnej pozycji.  
  
## <a name="other-notes-on-the-row-for-new-records"></a>Inne notatki w wierszu dla nowych rekordów  
 Nie można ustawić właściwości <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> tego wiersza, aby `false`. Jeśli zostanie podjęta próba, zostanie zgłoszone <xref:System.InvalidOperationException>.  
  
 Wiersz dla nowych rekordów jest zawsze tworzony w stanie niezaznaczonym.  
  
## <a name="virtual-mode"></a>Tryb wirtualny  
 W przypadku wdrażania trybu wirtualnego należy śledzić, kiedy wiersz dla nowych rekordów jest potrzebny w modelu danych i kiedy wycofać Dodawanie wiersza. Dokładna implementacja tej funkcji zależy od implementacji modelu danych i jego semantyki transakcji, na przykład czy zakres zatwierdzania jest na poziomie komórki czy wiersza. Aby uzyskać więcej informacji, zobacz [Tryb wirtualny w kontrolce DataGridView Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Instrukcje: określanie wartości domyślnych dla nowych wierszy w kontrolce DataGridView formularzy Windows Forms](specify-default-values-for-new-rows-in-the-datagrid.md)

---
title: "Używanie wiersza dla nowych rekordów w formancie DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4633a70f6c3d010e6cc75236778cf2fd59c0e05
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>Używanie wiersza dla nowych rekordów w formancie DataGridView formularzy systemu Windows
Jeśli używasz <xref:System.Windows.Forms.DataGridView> do edycji danych w aplikacji, często można zapewnić użytkownikom możliwość dodawania nowych wierszy danych w magazynie danych. <xref:System.Windows.Forms.DataGridView> Formantu obsługuje tę funkcję, zapewniając wiersz dla nowych rekordów, który jest zawsze wyświetlany jako ostatni wiersz. Jest ona oznaczona symbolem gwiazdki (*) w nagłówku wiersza. W poniższych sekcjach omówiono niektóre czynności, należy rozważyć, gdy program wiersza dla nowych rekordów jest włączona.  
  
## <a name="displaying-the-row-for-new-records"></a>Wyświetlanie wiersz dla nowych rekordów  
 Użyj <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> Właściwość wskazująca, czy wiersz dla nowych rekordów jest wyświetlany. Wartość domyślna tej właściwości to `true`.  
  
 Dla przypadku powiązany z danymi, pojawi się wiersz dla nowych rekordów Jeśli <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> właściwości formantu i <xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType> właściwości źródła danych są `true`. Jeśli spełniony jest `false` wiersz nie zostanie wyświetlona.  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>Wypełnianie wiersz dla nowych rekordów z domyślnych danych  
 Gdy użytkownik wybierze wiersz dla nowych rekordów jako bieżący wiersz <xref:System.Windows.Forms.DataGridView> kontrolować zgłasza <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> zdarzeń.  
  
 To zdarzenie umożliwia dostęp do nowego <xref:System.Windows.Forms.DataGridViewRow> i umożliwia do wypełnienia nowego wiersza z domyślnych danych. Aby uzyskać więcej informacji, zobacz [porady: Określanie wartości domyślnych dla nowych wierszy w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>Kolekcji wierszy  
 Wiersz dla nowych rekordów znajduje się w <xref:System.Windows.Forms.DataGridView> formantu <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji ale zachowuje się inaczej w dwóch aspektach:  
  
-   Nie można usunąć wiersza dla nowych rekordów z <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji programowo. <xref:System.InvalidOperationException> Jest generowany, jeśli ta próba zostanie podjęta. Użytkownik nie może również usunąć wiersz dla nowych rekordów. <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType> — Metoda nie powoduje usunięcia tego wiersza z <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekcji.  
  
-   Można dodać nie wiersz po wierszu dla nowych rekordów. <xref:System.InvalidOperationException> Jest wywoływane, jeśli ta próba zostanie podjęta. W związku z tym wiersz dla nowych rekordów jest zawsze ostatni wiersz w <xref:System.Windows.Forms.DataGridView> formantu. Metody w <xref:System.Windows.Forms.DataGridViewRowCollection> dodaje wierszy —<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, i <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>— wszystkie wywołania metod wstawiania wewnętrznie, gdy wiersz dla nowych rekordów jest obecna.  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>Dostosowywanie Visual wiersza dla nowych rekordów  
 Podczas tworzenia wiersza dla nowych rekordów jest oparty na wiersz, określony przez <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> właściwości. Wszystkie style komórki, które nie są określone dla tego wiersza są dziedziczone z innych właściwości. Aby uzyskać więcej informacji na temat dziedziczenia stylu komórki, zobacz [style komórki w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Oryginalne wartości wyświetlane przez komórki w wierszu dla nowych rekordów są pobierane z każdej komórki <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> właściwości. Dla komórki typu <xref:System.Windows.Forms.DataGridViewImageCell>, ta właściwość zwraca obrazu symbolu zastępczego. W przeciwnym razie ta właściwość zwraca `null`. Można zastąpić tę właściwość, aby zwrócić wartość niestandardową. Jednak te wartości początkowej mogą zostać zastąpione przez <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> obsługi zdarzeń, gdy fokus wprowadzi wiersz dla nowych rekordów.  
  
 Standardowe ikony dla tego wiersza nagłówka, będące Strzałka lub gwiazdki, nie są widoczne publicznie. Jeśli chcesz dostosować ikony, konieczne będzie utworzenie niestandardowego <xref:System.Windows.Forms.DataGridViewRowHeaderCell> klasy.  
  
 Użyj standardowych ikony <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> właściwość <xref:System.Windows.Forms.DataGridViewCellStyle> używany przez komórki nagłówka wiersza. Standardowe ikony nie są renderowane, jeśli nie ma wystarczającej ilości miejsca, aby wyświetlić je całkowicie.  
  
 Jeśli komórki nagłówka wiersza ma wartość ciągu, a nie ma wystarczającej ilości miejsca dla tekstu i ikony, najpierw porzucone ikony.  
  
## <a name="sorting"></a>Sortowanie  
 W trybie niezwiązanego nowych rekordów są zawsze dodawane na końcu <xref:System.Windows.Forms.DataGridView> nawet wtedy, gdy użytkownik ma sortowane zawartość <xref:System.Windows.Forms.DataGridView>. Użytkownik będzie musiał ponownie zastosować sortowanie, aby posortować wiersza do poprawnej pozycji; to zachowanie jest podobne do <xref:System.Windows.Forms.ListView> formantu.  
  
 W danych tryby powiązane i wirtualnych zachowania wstawiania, po zastosowaniu sortowania będą zależne od implementacji modelu danych. Aby uzyskać [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], wiersz jest natychmiast sortowane na poprawnej pozycji.  
  
## <a name="other-notes-on-the-row-for-new-records"></a>Inne wybrane uwagi dotyczące wiersz dla nowych rekordów  
 Nie można ustawić <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> właściwości tego wiersza, aby `false`. <xref:System.InvalidOperationException> Jest wywoływane, jeśli ta próba zostanie podjęta.  
  
 Wiersz dla nowych rekordów zawsze jest tworzony w stanie niezaznaczone.  
  
## <a name="virtual-mode"></a>Tryb wirtualny  
 Jeśli są Implementowanie trybu wirtualnego, konieczne będzie śledzić, gdy potrzebny jest wiersz dla nowych rekordów w modelu danych i kiedy należy wycofać dodanie wiersza. Dokładne stosowania tej funkcji zależy od implementacji modelu danych i jego semantyki transakcji na przykład czy zakres zatwierdzania na poziomie komórki lub wiersza. Aby uzyskać więcej informacji, zobacz [tryb wirtualny w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 [Formantu DataGridView formularzy wprowadzania danych w systemie Windows](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Porady: Określanie wartości domyślnych dla nowych wierszy w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)

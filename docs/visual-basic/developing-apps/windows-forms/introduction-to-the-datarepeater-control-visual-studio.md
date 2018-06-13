---
title: Wprowadzenie do formantu DataRepeater (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- repeating data
- DataRepeater, overview
- DataRepeater
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
ms.openlocfilehash: fc0cf9c358faf3e738eb3b24ec61577b88dbce4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591953"
---
# <a name="introduction-to-the-datarepeater-control-visual-studio"></a>Wprowadzenie do formantu DataRepeater (Visual Studio)
Powerpack Visual Basic <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formant jest kontenerem przewijanego do wielokrotnego formantów, które zawierają dane, na przykład wierszy w tabeli bazy danych. Może służyć jako alternatywę do <xref:System.Windows.Forms.DataGridView> kontrolować, jeśli wymagane jest większa kontrola nad układ danych. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> "Powtarza" grupy powiązanych formantów przez utworzenie wielu wystąpień w przewijania widoku. Dzięki temu użytkownicy wyświetlić kilka rekordów jednocześnie.  
  
## <a name="overview"></a>Omówienie  
 W czasie projektowania <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrola składa się z dwóch części. Sekcja zewnętrznych jest *okienka ekranu*, gdzie zostaną wyświetlone dane przewijania w czasie wykonywania. Wewnętrzny sekcji (z góry), znany jako *szablon elementu*, jest, gdzie umieścić kontrolek, które powtarza się w czasie wykonywania, zwykle jeden formant dla każdego pola w źródle danych. Właściwości i formantów w szablonie elementu znajdują się w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> właściwości.  
  
 W czasie wykonywania <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> jest kopiowany do wirtualnej <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> obiekt, który służy do wyświetlania danych w przypadku każdego rekordu jest wyświetlony w wyniku przewijania. Można dostosować wyświetlanie poszczególnych rekordów w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> zdarzeń, na przykład wyróżnianie oparta na wartości, która zawiera pola. Aby uzyskać więcej informacji, zobacz [porady: Zmienianie wyglądu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 Najbardziej popularnym zastosowaniem <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formant jest do wyświetlania danych z tabeli bazy danych lub inne źródła danych powiązania. Oprócz [!INCLUDE[vstecado](~/includes/vstecado-md.md)] obiektów danych <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu można powiązać każda klasa implementująca <xref:System.Collections.IList> interfejsu (w tym tablic), każda klasa implementująca <xref:System.ComponentModel.IListSource> interfejsu, każda klasa implementująca <xref:System.ComponentModel.IBindingList> interfejs lub każda klasa implementująca <xref:System.ComponentModel.IBindingListView> interfejsu.  
  
### <a name="data-binding"></a>Powiązanie danych  
 Zwykle wykonać wiązania danych przeciągając pola z **źródeł danych** okna na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie powiązanych danych w formancie Datarepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
 Podczas pracy z dużą ilością danych, można ustawić <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> właściwości `True` wyświetlania podzbioru dostępnych danych. Tryb wirtualny wymaga wykonania pamięci podręcznej danych, z którego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> zostanie wypełnione, i musi sterowania wszystkie interakcje z pamięci podręcznej danych w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [tryb wirtualny w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
 Można również wyświetlić niepowiązanych formantów na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu. Na przykład można wyświetlać obrazu, który jest powtarzany na każdej pozycji. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie formantów niepowiązanych w formancie Datarepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
### <a name="events"></a>Zdarzenia  
 Najważniejsze zdarzenia <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> sterowania stanowią <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> zdarzenie, które jest wywoływane, gdy nowe elementy są wyświetlony w wyniku przewijania, i <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> zdarzenie, które jest wywoływane, gdy element jest zaznaczony. Można użyć <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> zdarzeń, aby zmienić wygląd elementu. Na przykład można wyróżnić wartości ujemnych. Użyj <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> zdarzenie, aby uzyskać dostęp do wartości kontrolki, gdy element jest zaznaczony.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Kontroli przedstawia wszystkie formantu standardowego zdarzenia w edytorze kodu. Jednak niektóre zdarzenia nie można używać. Klawiatura i mysz zdarzenia, takie jak `KeyDown`, `Click`, i `MouseDown` nie zostanie wygenerowany w czasie wykonywania, ponieważ <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolki nigdy nie ma fokusu.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Nie ujawnia zdarzenia w czasie projektowania, ponieważ jest tworzony tylko w czasie wykonywania. Jeśli chcesz obsługiwać zdarzenia klawiatury i myszy, można dodać <xref:System.Windows.Forms.Panel> formant <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> w czasie projektowania, a następnie obsługi zdarzeń dla <xref:System.Windows.Forms.Panel>. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z formantem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md).  
  
### <a name="customizations"></a>Dostosowania  
 Istnieje wiele sposobów, aby dostosować wygląd i zachowanie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolować, zarówno w czasie wykonywania, jak i w czasie projektowania. Aby zmienić kolory, Ukryj lub zmodyfikować nagłówków elementów, zmień orientację z pionowego na poziome i wiele innych można ustawić właściwości. Aby uzyskać więcej informacji, zobacz [porady: Zmienianie wyglądu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md), [porady: wyświetlanie nagłówków elementów w formancie Datarepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md), i [porady: Zmienianie układu DataRepeater formant](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md).  
  
 Należy pamiętać, że niektóre właściwości dotyczą <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> samą kontrolką, podczas gdy inne dotyczą tylko <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>. Upewnij się, że sekcji wybrana, aby ustawić właściwości formantu. Aby uzyskać więcej informacji, zobacz [porady: Zmienianie wyglądu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 Inne dostosowania obejmują kontrolowanie możliwość dodawania i usuwania rekordów, dodawanie funkcji wyszukiwania i wyświetlanie powiązanych danych w formacie głównego i szczegółów. Aby uzyskać więcej informacji, zobacz [porady: wyłączanie dodawania i usuwania elementów DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md), [porady: wyszukiwanie danych w formancie Datarepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md), i [porady: Tworzenie formularza wzorzec/szczegół za pomocą dwóch Formantów DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolka DataRepeater](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)  
 [Przewodnik: wyświetlanie danych w kontrolce DataRepeater](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)  
 [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)

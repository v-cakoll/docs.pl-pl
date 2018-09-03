---
title: Wprowadzenie do formantu DataRepeater (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- repeating data
- DataRepeater, overview
- DataRepeater
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
ms.openlocfilehash: fc0cf9c358faf3e738eb3b24ec61577b88dbce4a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43485719"
---
# <a name="introduction-to-the-datarepeater-control-visual-studio"></a>Wprowadzenie do formantu DataRepeater (Visual Studio)
Visual Basic Power Packs <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli jest kontenerem przewijany do formantów, które wyświetlają wielokrotnego danych, na przykład wiersze w tabeli bazy danych. Może służyć jako alternatywa <xref:System.Windows.Forms.DataGridView> kontroli, gdy będziesz potrzebować większa kontrola nad układ danych. <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> "Powtarza się" grupy pokrewnych formantów przez utworzenie wielu wystąpień w widoku przewijania. Dzięki temu użytkownicy wyświetlić wiele rekordów w tym samym czasie.  
  
## <a name="overview"></a>Omówienie  
 W czasie projektowania <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrola składa się z dwóch części. Sekcja zewnętrznych jest *okienka ekranu*, gdzie zostaną wyświetlone dane przewijania w czasie wykonywania. Wewnętrzny sekcji (z góry), nazywany *szablon elementu*, to, gdzie umieścić formanty, które zostanie powtórzona w czasie wykonywania, zwykle jeden formant dla każdego pola w źródle danych. Właściwości i kontrolki w szablonie elementu są hermetyzowane w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> właściwości.  
  
 W czasie wykonywania <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> jest kopiowany do wirtualnej <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> obiekt, który służy do wyświetlania danych, jeśli każdy rekord jest przewijane do widoku. Można dostosować wyświetlanie poszczególnych rekordów w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> zdarzenie, na przykład, wyróżnianie pola na podstawie wartości, które zawiera. Aby uzyskać więcej informacji, zobacz [porady: Zmienianie wyglądu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 Najczęściej używane dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formant jest wyświetlenie danych z tabeli bazy danych lub innego źródła powiązane dane. Oprócz [!INCLUDE[vstecado](~/includes/vstecado-md.md)] obiektów danych <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli można powiązać z dowolnej klasy, która implementuje <xref:System.Collections.IList> interfejsu (w tym tablice), każda klasa implementująca <xref:System.ComponentModel.IListSource> interfejsu każdej klasy, która implementuje <xref:System.ComponentModel.IBindingList> interfejs lub dowolnej klasy, która implementuje <xref:System.ComponentModel.IBindingListView> interfejsu.  
  
### <a name="data-binding"></a>Powiązanie danych  
 Zazwyczaj można wykonać wiązania danych przeciągając pola z **źródeł danych** okna na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie danych powiązane w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
 Podczas pracy z dużymi ilościami danych, można ustawić <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> właściwości `True` do wyświetlenia podzbiór dostępnych danych. Tryb wirtualny wymaga wykonania pamięci podręcznej danych, z którego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> została wypełniona, i musi kontrolować wszystkie interakcje z pamięci podręcznej danych w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [tryb wirtualny w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
 Można również wyświetlić niepowiązanych formantów na <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli. Na przykład możesz wyświetlić obraz, który jest powtarzane dla każdego elementu. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie formantów niepowiązanych w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
### <a name="events"></a>Zdarzenia  
 Najważniejsze zdarzenia dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> sterowania stanowią <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> zdarzenie, które jest wywoływane, gdy nowe elementy są przewijane do widoku, a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> zdarzenie, które jest wywoływane, gdy element jest wybrany. Możesz użyć <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> zdarzenie, aby zmienić wygląd elementu. Na przykład można wyróżnić wartości ujemnych. Użyj <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged> zdarzenie, aby uzyskać dostęp do wartości kontrolki, gdy element jest wybrany.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> Kontroli udostępnia wszystkie formantu standardowego zdarzenia w edytorze kodu. Jednak niektóre zdarzenia nie można używać. Klawiatury i myszy zdarzenia, takie jak `KeyDown`, `Click`, i `MouseDown` nie będą zgłaszane w czasie wykonywania, ponieważ <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolkę nigdy nie jest ustawiony fokus.  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> Nie uwidacznia zdarzenia w czasie projektowania, ponieważ jest tworzony tylko w czasie wykonywania. Jeśli chcesz obsługiwać zdarzenia klawiatury i myszy, można dodać <xref:System.Windows.Forms.Panel> kontrolę <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A> w czasie projektowania, a następnie obsługi zdarzeń dla <xref:System.Windows.Forms.Panel>. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z formantem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md).  
  
### <a name="customizations"></a>Dostosowania  
 Istnieje wiele sposobów, aby dostosować wygląd i zachowanie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolować, zarówno w czasie wykonywania, jak i w czasie projektowania. Zmienianie kolorów, ukrywania lub modyfikowanie nagłówków elementu, zmiana orientacji pionowej na poziomą i wiele innych, można ustawić właściwości. Aby uzyskać więcej informacji, zobacz [porady: Zmienianie wyglądu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md), [instrukcje: wyświetlanie nagłówków elementów w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md), i [jak: zmienić układ Kontrolka DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md).  
  
 Należy zauważyć, że niektóre właściwości mają zastosowanie do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> samej kontrolki, podczas gdy inne dotyczą tylko programu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>. Upewnij się, że masz prawidłowe części formant zaznaczony przed ustawieniem właściwości. Aby uzyskać więcej informacji, zobacz [porady: Zmienianie wyglądu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md).  
  
 Inne modyfikacje obejmują kontrolowanie możliwość dodawania i usuwania rekordów, dodawanie funkcji wyszukiwania i wyświetlanie powiązanych danych w formacie głównego i szczegółów. Aby uzyskać więcej informacji, zobacz [porady: wyłączanie dodawania i usuwania elementów DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md), [porady: wyszukiwanie danych w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md), i [jak: Tworzenie formularza wzorzec/szczegół za pomocą dwóch Formantów DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolka DataRepeater](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)  
 [Przewodnik: wyświetlanie danych w kontrolce DataRepeater](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)  
 [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)

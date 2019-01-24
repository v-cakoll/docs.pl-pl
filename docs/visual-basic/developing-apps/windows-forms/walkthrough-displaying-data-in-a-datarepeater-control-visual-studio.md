---
title: 'Przewodnik: Wyświetlanie danych w formancie DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
ms.openlocfilehash: 4153fecaecc80fc4c40fb6dd9026b07c49ec0fb7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729252"
---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a>Przewodnik: Wyświetlanie danych w formancie DataRepeater (Visual Studio)
Ten przewodnik zawiera podstawowy scenariusz rozpoczęcia do zakończenia do wyświetlania powiązanych danych w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
## <a name="prerequisite"></a>Wymaganie wstępne  
 Ten poradnik wymaga przykładowej bazy danych Northwind.  
  
 Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z Microsoft Download Center. Aby uzyskać instrukcje, zobacz [Downloading Sample Databases](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
## <a name="overview"></a>Omówienie  
 Pierwsza część w tym przewodniku składa się z czterech głównych zadań:  
  
-   Tworzenie rozwiązania.  
  
-   Dodawanie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
-   Dodawanie źródła danych.  
  
-   Dodawanie formantów powiązanych z danymi.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a>Tworzenie rozwiązania DataRepeater  
 W pierwszym kroku utworzysz projekt i rozwiązanie.  
  
#### <a name="to-create-a-datarepeater-solution"></a>Aby utworzyć rozwiązanie DataRepeater  
  
1.  W programie Visual Studio **pliku** menu, kliknij przycisk **nowy projekt**.  
  
2.  W **typów projektów** okienka **nowy projekt** okna dialogowego rozwiń **języka Visual Basic**, a następnie kliknij przycisk **Windows**.  
  
3.  W **szablony** okienku kliknij **aplikacja interfejsu Windows Forms**.  
  
4.  W **nazwa** wpisz `DataRepeaterApp`.  
  
5.  Kliknij przycisk **OK**.  
  
     Zostanie otwarty projektant formularzy Windows.  
  
6.  Wybierz formularz w programie Windows Forms Designer. W **właściwości** oknie **rozmiar** właściwość `800, 700`.  
  
## <a name="adding-a-datarepeater-control"></a>Dodawanie kontrolki DataRepeater  
 W tym kroku dodasz <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu do formularza.  
  
#### <a name="to-add-a-datarepeater-control"></a>Aby dodać kontrolki DataRepeater  
  
1.  Na **widoku** menu, kliknij przycisk **przybornika**.  
  
     **Przybornika** zostanie otwarty.  
  
2.  Wybierz **Visual Basic PowerPacks** kartę.  
  
3.  Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolować na **Form1**.  
  
4.  W oknie właściwości ustaw **lokalizacji** właściwość `0, 25`.  
  
5.  Ustaw **rozmiar** właściwość `460, 600`.  
  
## <a name="adding-a-data-source"></a>Dodawanie źródła danych  
 W tym kroku należy dodać źródła danych dla <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
#### <a name="to-add-a-data-source"></a>Aby dodać źródło danych  
  
1.  Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.  
  
2.  W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych**.  
  
3.  Wybierz **bazy danych** na **wybierz typ źródła danych** strony, a następnie kliknij przycisk **dalej**.  
  
4.  Na **wybierz połączenie danych** strony, wykonaj jedną z następujących czynności:  
  
    -   Jeśli połączenie danych z przykładowej bazy danych Northwind jest dostępne na liście rozwijanej, kliknij go.  
  
         —lub—  
  
    -   Kliknij przycisk **nowe połączenie** Aby skonfigurować nowe połączenie danych. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](/visualstudio/data-tools/add-new-connections).  
  
5.  Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.  
  
    > [!NOTE]
    >  Jeśli pojawi się okno dialogowe, kliknij przycisk **tak** można zapisać pliku do projektu.  
  
6.  Kliknij przycisk **dalej** na **Zapisz parametry połączenia do pliku konfiguracyjnego aplikacji** strony.  
  
7.  Rozwiń **tabel** węzeł **wybierz obiekty bazy danych** strony.  
  
8.  Zaznacz pole wyboru obok pozycji **klientów** i **zamówienia** tabel, a następnie kliknij **Zakończ**.  
  
     **NorthwindDataSet** zostanie dodany do projektu i **klientów** i **zamówienia** tabele są wyświetlane w **źródeł danych** okna.  
  
## <a name="adding-data-bound-controls"></a>Dodawanie formantów powiązanych z danymi  
 W tym kroku dodaj formanty powiązane z danymi do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.  
  
#### <a name="to-add-data-bound-controls"></a>Aby dodać formanty powiązane z danymi  
  
1.  W **źródeł danych** okna, wybierz węzeł najwyższego poziomu dla **klientów** tabeli.  
  
2.  Zmień upuszczany typ tabeli, aby **szczegóły** , klikając **szczegóły** w węźle tabeli na liście rozwijanej.  
  
3.  Wybierz **klientów** tabeli węzła i przeciągnij element szablonu region (górnego regionu) <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
     A <xref:System.Windows.Forms.BindingNavigator> formant jest dodawany do formularza i **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**,  **TableAdapterManager**, i **CustomersBindingNavigator** składniki są dodawane do zasobnika składnika.  
  
4.  Zaznacz wszystkie pola i ich etykiet skojarzonych i umieść je w pobliżu lewej krawędzi region szablonu elementu.  
  
5.  Wybierz pola pięć ostatnich (**Region**, **kod pocztowy**, **kraju**, **Phone**, i **faks**) i ich etykiet skojarzonych i przenieść je w górę i w prawo pierwszych sześciu pól.  
  
6.  Wybierz szablon elementu (górnej kontrolki).  
  
7.  W oknie właściwości ustaw **rozmiar** właściwość `427, 170`.  
  
 W tym momencie masz działającą aplikację, która będzie wyświetlana lista powtarzające się klientów. Można nacisnąć klawisz F5, aby uruchomić aplikację, zmieniać dane i dodawanie lub usuwanie rekordów klientów.  
  
 W następnych kroków opcjonalnych, będzie dowiesz się, jak dostosować <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
## <a name="next-steps-optional"></a>Następne kroki (opcjonalnie)  
 Ta część przewodnika obejmuje cztery opcjonalnych zadań:  
  
-   Zmiana wyglądu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
-   Uniemożliwia użytkownikom dodawanie i usuwanie rekordów.  
  
-   Dodawanie możliwości wyszukiwania do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
-   Dodawanie tabeli do wzorca i szczegółów <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a>Zmienianie wyglądu formantu DataRepeater  
 W tym kroku Opcjonalnie możesz zmienić `BackColor` z <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu w czasie projektowania. Możesz również dodać kod, aby wyświetlać tylko wiersze w naprzemiennych kolorów i aby zmienić etykietę `ForeColor` warunkowo.  
  
#### <a name="to-change-the-appearance-of-the-control"></a>Aby zmienić wygląd formantu  
  
1.  W programie Windows Forms Designer wybierz główny region (niższe) <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
2.  W oknie właściwości ustaw `BackColor` właściwości na biały.  
  
3.  Kliknij dwukrotnie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> można otworzyć edytora kodu.  
  
4.  W edytorze kodu, w przypadku menu rozwijanego, kliknij przycisk **drawitem —**.  
  
5.  W <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> procedura obsługi zdarzeń, Dodaj następujący kod do alternatywnego `BackColor`:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  W <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> procedura obsługi zdarzeń, Dodaj następujący kod, aby zmienić `ForeColor` etykiety w zależności od warunku:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  Naciśnij klawisz F5, aby uruchomić aplikację i wyświetlić dostosowań.  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a>Uniemożliwia użytkownikom dodawanie i usuwanie rekordów  
 W tym kroku opcjonalnie Dodaj kod, który uniemożliwia użytkownikom dodawanie i usuwanie rekordów w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a>Aby uniemożliwić użytkownikom dodawanie i usuwanie rekordów  
  
1.  W Windows Forms Designer kliknij dwukrotnie formularza, aby otworzyć Edytor kodu.  
  
2.  Dodaj następujący kod do `Form_Load` zdarzeń:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  Na liście rozwijanej nazwy klasy kliknij **BindingNavigatorDeleteItem**. Na liście rozwijanej nazwy metody kliknij **EnabledChanged**.  
  
4.  Dodaj następujący kod do `BindingNavigatorDeleteItem_EnabledChanged` program obsługi zdarzeń:  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  Ten krok jest niezbędny, ponieważ <xref:System.Windows.Forms.BindingSource> umożliwi **DeleteItem** przycisk ilekroć dany zmiany bieżącego rekordu.  
  
5.  Naciśnij klawisz F5, aby uruchomić aplikację. Należy zauważyć, że **DeleteItem** przycisk jest wyłączony i że nie można usunąć elementów, naciskając klawisz DELETE.  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a>Dodawanie możliwości wyszukiwania do formantu DataRepeater  
 W tym kroku opcjonalnie zaimplementować możliwość wyszukiwania wartości w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli. Jeśli zostanie znaleziony ciąg wyszukiwania, formant wybiera element, który zawiera wartość się i przewija elementu w widoku.  
  
#### <a name="to-add-search-capability"></a>Aby dodać możliwości wyszukiwania  
  
1.  Przeciągnij <xref:System.Windows.Forms.TextBox> z kontrolować **przybornika** na formularz, który zawiera <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
     Umieść ją w obszarze <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
2.  W oknie Właściwości zmień **nazwa** właściwości **SearchTextBox**.  
  
3.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** na formularz, który zawiera <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli. Umieść ją w obszarze <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
4.  W oknie Właściwości zmień **nazwa** właściwości **SearchButton**. Zmiana **tekstu** właściwości **wyszukiwania**.  
  
5.  Kliknij dwukrotnie <xref:System.Windows.Forms.Button> sterowania, aby otworzyć Edytor kodu i Dodaj następujący kod do `SearchButton_Click` programu obsługi zdarzeń.  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  Naciśnij klawisz F5, aby uruchomić aplikację. Wpisz identyfikator klienta w **SearchTextBox** i kliknij przycisk **wyszukiwania** przycisku.  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a>Dodawanie głównego i tabelę szczegółów do DataRepeater  
 W tym kroku opcjonalnie Dodaj sekundy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu, aby wyświetlić powiązane zamówienia dla każdego klienta.  
  
#### <a name="to-add-a-master-and-detail-table"></a>Aby dodać tabelę głównego i szczegółów  
  
1.  Przeciągnij sekundy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> z kontrolować **Visual Basic PowerPacks** karcie **przybornika** na formularz.  
  
2.  W oknie właściwości ustaw **lokalizacji** właściwość `465, 25`.  
  
3.  Ustaw **rozmiar** właściwość `315, 600`.  
  
4.  W **źródeł danych** okna, rozwiń węzeł **klientów** tabeli węzła, a następnie wybierz węzeł szczegółów **zamówienia** tabeli.  
  
5.  Zmień upuszczany typ to **zamówienia** tabeli, aby uzyskać szczegółowe informacje, klikając **szczegóły** w węźle tabeli na liście rozwijanej.  
  
6.  Przeciągnij to **zamówienia** węzeł tabeli na region szablonu elementu (górnego regionu) drugiego <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
     **OrdersBindingSource** składnika i **OrdersTableAdapter** składników są dodawane do zasobnika składnika.  
  
7.  Naciśnij klawisz F5, aby uruchomić aplikację. Po wybraniu każdego klienta w pierwszym <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolować zamówień dla tego klienta są wyświetlane w ciągu sekundy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
## <a name="see-also"></a>Zobacz także
- [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Instrukcje: Wyświetlanie powiązanych danych w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [Instrukcje: Wyświetlanie formantów niepowiązanych w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)
- [Instrukcje: Zmienianie układu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)
- [Instrukcje: Wyświetlanie nagłówków elementów w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
- [Instrukcje: Wyszukiwanie danych w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)
- [Instrukcje: Tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
- [Instrukcje: Zmienianie wyglądu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
- [Instrukcje: Wyłączanie dodawania i usuwania elementów DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)
- [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)

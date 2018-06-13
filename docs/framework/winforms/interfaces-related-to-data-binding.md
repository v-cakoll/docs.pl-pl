---
title: Interfejsy dotyczące powiązania danych
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], data-binding interfaces
- INotifyPropertyChanged interface
- IBindingListView interface
- IList interface [Windows Forms], Windows Forms data binding
- IBindingList interface [Windows Forms], Windows Forms data binding
- interfaces [Windows Forms], Windows Forms data binding
- IEditableObject interface [Windows Forms], Windows Forms data binding
- data binding [Windows Forms], interfaces
- IDataErrorInfo interface [Windows Forms], Windows Forms data binding
ms.assetid: 14e49a2e-3e46-47ca-b491-70d546333277
ms.openlocfilehash: 6c4470b33977408fa4429d187dafd76241d0d9d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541849"
---
# <a name="interfaces-related-to-data-binding"></a>Interfejsy dotyczące powiązania danych
Z [!INCLUDE[vstecado](../../../includes/vstecado-md.md)], możesz utworzyć wiele struktur danych różnych potrzeb powiązanie aplikacji i danych, użytkownik pracuje z. Możesz utworzyć własne klasy, które dostarczyć lub użyć danych w formularzach systemu Windows. Te obiekty może oferować różne poziomy funkcjonalności i złożoność, z powiązania danych podstawowych zapewnienie obsługi w czasie projektowania, sprawdzanie błędów, powiadomienia o zmianie lub nawet pomocy technicznej dla strukturalnych wycofania zmian wprowadzonych w samych danych.  
  
## <a name="consumers-of-data-binding-interfaces"></a>Konsumenci interfejsy wiązania danych  
 Poniżej opisano dwie grupy obiektów interfejsu. Pierwsza grupa zawiera listę interfejsów, które są wdrażane w źródłach danych przez autorów źródła danych. Te interfejsy mają być używane przez konsumentów źródła danych, które są w większości przypadków, które formanty formularzy systemu Windows lub składników. Drugiej grupy Wyświetla interfejsy przeznaczony do użytku przez autorów składnika. Autorzy składnika użycia tych interfejsów tworzenia składnika, który obsługuje powiązanie danych do użycia przez aparat powiązanie danych formularzy systemu Windows. Można zaimplementować te interfejsy w obrębie klasy skojarzone z formularza do włączenia możliwości wiązania danych; każdej sprawy przedstawia klasy, która implementuje interfejs umożliwiający interakcję z danymi. Visual Studio szybkie (RAD) danych projektu obsługi narzędzi do tworzenia aplikacji już korzystać z tej funkcji.  
  
### <a name="interfaces-for-implementation-by-data-source-authors"></a>Interfejsy do implementacji przez autorów źródła danych  
 Następujące interfejsy mają być używane przez formanty formularzy systemu Windows:  
  
-   <xref:System.Collections.IList> Interfejs  
  
     Klasa, która implementuje <xref:System.Collections.IList> interfejsu może być <xref:System.Array>, <xref:System.Collections.ArrayList>, lub <xref:System.Collections.CollectionBase>. Są to indeksowanego listę elementów typu <xref:System.Object>. Te listy musi zawierać jednorodnego typów, ponieważ pierwszy element indeks Określa typ. <xref:System.Collections.IList> będzie dostępna dla powiązania tylko w czasie wykonywania.  
  
    > [!NOTE]
    >  Jeśli chcesz utworzyć listę obiektów biznesowych dla powiązania z formularzy systemu Windows, należy rozważyć użycie <xref:System.ComponentModel.BindingList%601>. <xref:System.ComponentModel.BindingList%601> Jest klasą rozszerzonego, która implementuje interfejsów podstawowego, wymaganych do dwukierunkowe wiązanie danych formularzy systemu Windows.  
  
-   <xref:System.ComponentModel.IBindingList> Interfejs  
  
     Klasa, która implementuje <xref:System.ComponentModel.IBindingList> interfejs zapewnia dużo wyższy poziom funkcjonalności powiązania danych. Ta implementacja udostępnia podstawowe funkcje sortowania i powiadomienia o zmianie, zarówno dla po liście elementów zmiany (na przykład trzeci element na liście klientów zawiera zmiany do pola adresu), a także podczas zmiany samej listy (na przykład Liczba elementów na liście zwiększa lub zmniejsza). Powiadomienie o zmianie jest ważne, jeśli planowane jest wiele formantów związanych z tych samych danych, i chcesz zmiany danych w formantów obejmie inne formanty powiązane.  
  
    > [!NOTE]
    >  Powiadomienie o zmianie jest włączona dla <xref:System.ComponentModel.IBindingList> interfejsu za pomocą <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A> właściwości które, gdy `true`, zgłasza <xref:System.ComponentModel.IBindingList.ListChanged> zdarzeń, wskazujący listy zmienione lub element listy zmienione.  
  
     Typ zmiany jest opisane przez <xref:System.ComponentModel.ListChangedType> właściwość <xref:System.ComponentModel.ListChangedEventArgs> parametru. W związku z tym przy każdej aktualizacji modelu danych, wszelkie widoki zależne, takie jak inne formanty powiązane z tym samym źródłem danych, również zostaną zaktualizowane. Jednak obiektów znajdujących się na liście będzie miał powiadomiono listy po zmianie tak, aby podnieść listy <xref:System.ComponentModel.IBindingList.ListChanged> zdarzeń.  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BindingList%601> Zawiera ogólną implementację <xref:System.ComponentModel.IBindingList> interfejsu.  
  
-   <xref:System.ComponentModel.IBindingListView> Interfejs  
  
     Klasa, która implementuje <xref:System.ComponentModel.IBindingListView> interfejs zapewnia wszystkie funkcje implementacja <xref:System.ComponentModel.IBindingList>, a także jako filtrowania i zaawansowane sortowanie funkcji. Ta implementacja oferuje oparte na ciągach filtrowania i sortowania wielokolumnowe z parami kierunek deskryptora właściwości.  
  
-   <xref:System.ComponentModel.IEditableObject> Interfejs  
  
     Klasa, która implementuje <xref:System.ComponentModel.IEditableObject> interfejs umożliwiający obiektu w celu kontrolowania, kiedy dany obiekt zmiany stałe. Ta implementacja zapewnia możesz <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, i <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metody, które umożliwiają wycofać zmiany wprowadzone do tego obiektu. Poniżej znajduje się krótki opis działania <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, i <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metod i jak działają w połączeniu ze sobą, aby włączyć możliwości wycofania zmian wprowadzonych w danych:  
  
    -   <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> Metody sygnalizuje początek edycji obiektu. Obiekt, który implementuje ten interfejs musi przechowywać żadnych aktualizacji po <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> wywołania metody w taki sposób, odrzucone aktualizacje Jeśli <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metoda jest wywoływana. W danych powiązanie formularzy systemu Windows, można wywołać <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> wiele razy w zakresie pojedynczy Edytuj transakcji (na przykład <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>). Implementacje <xref:System.ComponentModel.IEditableObject> należy śledzić czy <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> została już wywołana i Ignoruj kolejnych wywołań <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>. Ponieważ ta metoda może być wywołana wiele razy, jest ważne, czy wezwań do niego są bezpieczne; oznacza to, że kolejne <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> wywołania nie można zniszczyć aktualizacje, które zostały wprowadzone lub zmiany danych, który został zapisany w pierwszym <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> wywołania.  
  
    -   <xref:System.ComponentModel.IEditableObject.EndEdit%2A> Metody wypchnięcia wszelkie zmiany od momentu <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> została wywołana w obiekcie źródłowym, jeśli obiekt jest obecnie w trybie edycji.  
  
    -   <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> Metody Anuluje zmiany wprowadzone do tego obiektu.  
  
     Aby uzyskać więcej informacji na temat sposobu <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, i <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metody pracy, zobacz [zapisać danych w bazie danych](/visualstudio/data-tools/save-data-back-to-the-database).  
  
     To pojęcie transakcyjnych funkcji danych jest używany przez <xref:System.Windows.Forms.DataGridView> formantu.  
  
-   <xref:System.ComponentModel.ICancelAddNew> Interfejs  
  
     Klasa, która implementuje <xref:System.ComponentModel.ICancelAddNew> zwykle implementuje interfejs <xref:System.ComponentModel.IBindingList> interfejsu i pozwala wycofać wprowadzone do źródła danych z dodatku <xref:System.ComponentModel.IBindingList.AddNew%2A> metody. Jeśli źródło danych implementuje <xref:System.ComponentModel.IBindingList> interfejsu, powinny również trzeba zaimplementować <xref:System.ComponentModel.ICancelAddNew> interfejsu.  
  
-   <xref:System.ComponentModel.IDataErrorInfo> Interfejs  
  
     Klasa, która implementuje <xref:System.ComponentModel.IDataErrorInfo> interfejs umożliwiający obiektów oferowanie błędów niestandardowych informacji do kontrolki powiązane:  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Error%2A> Właściwość zwraca błąd ogólny tekst komunikatu (na przykład "Wystąpił błąd").  
  
    -   <xref:System.ComponentModel.IDataErrorInfo.Item%2A> Właściwość zwraca ciąg zawierający komunikat o błędzie z kolumny (na przykład "wartość `State` kolumny jest nieprawidłowe").  
  
-   <xref:System.Collections.IEnumerable> Interfejs  
  
     Klasa, która implementuje <xref:System.Collections.IEnumerable> interfejs jest zwykle używany przez [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]. Obsługa formularzy systemu Windows dla tego interfejsu jest dostępna za pośrednictwem tylko <xref:System.Windows.Forms.BindingSource> składnika.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.BindingSource> Składnika kopiuje wszystkie <xref:System.Collections.IEnumerable> elementy na listę osobne dla powiązania celów.  
  
-   <xref:System.ComponentModel.ITypedList> Interfejs  
  
     Klasy kolekcji, która implementuje <xref:System.ComponentModel.ITypedList> interfejs zapewnia możliwość kontrolowania kolejność oraz zbiór właściwości narażonych na powiązanej kontrolki.  
  
    > [!NOTE]
    >  Po zaimplementowaniu <xref:System.ComponentModel.ITypedList.GetItemProperties%2A> metody i <xref:System.ComponentModel.PropertyDescriptor> tablicy nie jest równa null, ostatni wpis w tablicy będzie deskryptora właściwości, który zawiera opis właściwości listy innej listy elementów.  
  
-   <xref:System.ComponentModel.ICustomTypeDescriptor> Interfejs  
  
     Klasa, która implementuje <xref:System.ComponentModel.ICustomTypeDescriptor> interfejs umożliwia dynamiczne informacje o sobie samym. Ten interfejs jest podobny do <xref:System.ComponentModel.ITypedList> , ale jest używana dla obiektów, a nie listy. Ten interfejs jest używany przez <xref:System.Data.DataRowView> do projektu schematu podstawowej wierszy. Proste implementacja <xref:System.ComponentModel.ICustomTypeDescriptor> są dostarczane przez <xref:System.ComponentModel.CustomTypeDescriptor> klasy.  
  
    > [!NOTE]
    >  Do obsługi powiązania czasu projektowania typy które implementują <xref:System.ComponentModel.ICustomTypeDescriptor>, typ musi implementować też <xref:System.ComponentModel.IComponent> i istnieć jako wystąpienia w formularzu.  
  
-   <xref:System.ComponentModel.IListSource> Interfejs  
  
     Klasa, która implementuje <xref:System.ComponentModel.IListSource> interfejs umożliwia powiązanie oparte na liście obiektów-list. <xref:System.ComponentModel.IListSource.GetList%2A> Metody <xref:System.ComponentModel.IListSource> służy do zwracania listy można powiązać z obiektu, który nie dziedziczy z <xref:System.Collections.IList>. <xref:System.ComponentModel.IListSource> jest używany przez <xref:System.Data.DataSet> klasy.  
  
-   <xref:System.ComponentModel.IRaiseItemChangedEvents> Interfejs  
  
     Klasa, która implementuje <xref:System.ComponentModel.IRaiseItemChangedEvents> interfejsu jest listą powiązania, który też implementuje <xref:System.ComponentModel.IBindingList> interfejsu. Ten interfejs jest używany do wskazania, jeśli z danym typem zgłasza <xref:System.ComponentModel.IBindingList.ListChanged> zdarzeń typu <xref:System.ComponentModel.ListChangedType.ItemChanged> za pośrednictwem jego <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A> właściwości.  
  
    > [!NOTE]
    >  Należy zaimplementować <xref:System.ComponentModel.IRaiseItemChangedEvents> Jeśli źródło danych zawiera właściwości do konwersji zdarzenia listy opisanych powyżej i prowadzi interakcję z <xref:System.Windows.Forms.BindingSource> składnika. W przeciwnym razie <xref:System.Windows.Forms.BindingSource> przeprowadzenia właściwości do konwersji zdarzenia listy powodujące niższej wydajności.  
  
-   <xref:System.ComponentModel.ISupportInitialize> Interfejs  
  
     Składnik, który implementuje <xref:System.ComponentModel.ISupportInitialize> ma zalety usługi partia zadań optymalizacji dla właściwości i Inicjowanie zależne od wspólnej właściwości. <xref:System.ComponentModel.ISupportInitialize> Zawiera dwóch metod:  
  
    -   <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> sygnalizuje, że rozpoczyna inicjowanie tego obiektu.  
  
    -   <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> sygnalizuje, że dobiega inicjowanie tego obiektu.  
  
-   <xref:System.ComponentModel.ISupportInitializeNotification> Interfejs  
  
     Składnik, który implementuje <xref:System.ComponentModel.ISupportInitializeNotification> również interfejs implementuje <xref:System.ComponentModel.ISupportInitialize> interfejsu. Ten interfejs umożliwia powiadomić innych <xref:System.ComponentModel.ISupportInitialize> składników tego Inicjowanie zostało zakończone. <xref:System.ComponentModel.ISupportInitializeNotification> Interfejs zawiera dwa składniki:  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A> Zwraca `boolean` wartość wskazującą, czy składnik jest zainicjowany.  
  
    -   <xref:System.ComponentModel.ISupportInitializeNotification.Initialized> występuje, gdy <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> jest wywoływana.  
  
-   <xref:System.ComponentModel.INotifyPropertyChanged> Interfejs  
  
     Klasa, która implementuje ten interfejs jest typem, który wywołuje zdarzenie po zmianie jego wartości właściwości. Ten interfejs jest przeznaczona do Zastąp wzorzec wystąpienia zdarzenia zmiany, dla każdej właściwości formantu. W przypadku używania w <xref:System.ComponentModel.BindingList%601>, powinien implementować obiekt biznesowy <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu i BindingList\`przekonwertuje 1 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenia <xref:System.ComponentModel.BindingList%601.ListChanged> zdarzeń typu <xref:System.ComponentModel.ListChangedType.ItemChanged>.  
  
    > [!NOTE]
    >  Zmiany powiadomienia w powiązanie między powiązania klienta i dane użytkownika powiązanego źródła danych typ źródła powinny albo implementować <xref:System.ComponentModel.INotifyPropertyChanged> zapewniają interfejs (preferowane) lub *propertyName* `Changed` zdarzenia dla typu powiązania, ale nie należy wykonać obie czynności.  
  
### <a name="interfaces-for-implementation-by-component-authors"></a>Interfejsy do implementacji przez autorów składnika  
 Następujące interfejsy są przeznaczone do użycia przez aparat powiązanie danych formularzy systemu Windows:  
  
-   <xref:System.Windows.Forms.IBindableComponent> Interfejs  
  
     Klasa, która implementuje ten interfejs jest składnikiem-control, który obsługuje powiązanie danych. Ta klasa zwraca powiązania danych i kontekstu powiązania składnika za pomocą <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> i <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> właściwości tego interfejsu.  
  
    > [!NOTE]
    >  Jeśli składnik dziedziczy <xref:System.Windows.Forms.Control>, nie musisz wdrożyć <xref:System.Windows.Forms.IBindableComponent> interfejsu.  
  
-   <xref:System.Windows.Forms.ICurrencyManagerProvider> Interfejs  
  
     Klasa, która implementuje <xref:System.Windows.Forms.ICurrencyManagerProvider> interfejs jest składnikiem, który udostępnia własny <xref:System.Windows.Forms.CurrencyManager> do zarządzania powiązania skojarzonego z tym konkretnym składnikiem. Dostęp do niestandardowego <xref:System.Windows.Forms.CurrencyManager> są dostarczane przez <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> właściwości.  
  
    > [!NOTE]
    >  Klasa, która dziedziczy <xref:System.Windows.Forms.Control> zarządza powiązania automatycznie za pomocą jego <xref:System.Windows.Forms.Control.BindingContext%2A> właściwości, tak przypadków, w których należy wdrożyć <xref:System.Windows.Forms.ICurrencyManagerProvider> są stosunkowo rzadko.  
  
## <a name="see-also"></a>Zobacz też  
 [Wiązanie danych i formularzy Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Instrukcje: tworzenie prostej kontrolki powiązanej na formularzu systemu Windows](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)  
 [Wiązanie danych formularzy Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)

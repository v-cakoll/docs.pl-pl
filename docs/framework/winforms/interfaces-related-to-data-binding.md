---
title: Interfejsy dotyczące wiązania danych
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
ms.openlocfilehash: 1609fbd8cbb24d6f2c10fbc3a235f01a451eb0fa
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754080"
---
# <a name="interfaces-related-to-data-binding"></a>Interfejsy dotyczące wiązania danych

Za pomocą [!INCLUDE[vstecado](../../../includes/vstecado-md.md)], możesz utworzyć wiele różnymi strukturami danych zgodnie z potrzebami powiązania aplikacji i danych, w którym pracujesz. Można tworzyć własnych klas, które zapewniają lub zużywają danych w formularzach Windows Forms. Te obiekty można udostępniają różne poziomy funkcjonalności i poziomie złożoności, z powiązania danych podstawowych do zapewniania obsługi w czasie projektowania, sprawdzanie błędów, powiadomienia o zmianie lub nawet pomocy technicznej ze strukturą wycofywania zmian wprowadzonych w samych danych.

## <a name="consumers-of-data-binding-interfaces"></a>Konsumenci interfejsy powiązania danych

W poniższych sekcjach opisano dwie grupy obiektów interfejsu. Pierwsza grupa zawiera listę interfejsów, które są implementowane w źródłach danych przez autorów źródła danych. Te interfejsy są przeznaczone do użycia przez konsumentów źródła danych, które są w większości przypadków kontrolek formularzy Windows lub składników. Druga grupa zawiera listę interfejsów przeznaczone do użytku przez autorów składnika. Autorzy składnika użycia tych interfejsów, tworząc składnik, który obsługuje powiązanie danych do użycia przez aparat powiązanie danych formularzy Windows. Można zaimplementować te interfejsów wewnątrz klasy skojarzone z formularza w taki sposób, w celu włączenia możliwości wiązania danych; Każdy przypadek przedstawia klasę, która implementuje interfejs, który umożliwia interakcję z danymi. Narzędzia Visual Studio rapid application development (RAD) dane projektu środowisko już korzystać z tej funkcji.

### <a name="interfaces-for-implementation-by-data-source-authors"></a>Interfejsy do implementacji przez autorów źródła danych

Następujące interfejsy są przeznaczone do użycia przez kontrolek formularzy Windows Forms:

- <xref:System.Collections.IList> Interfejs

  Klasa, która implementuje <xref:System.Collections.IList> interfejsu może być <xref:System.Array>, <xref:System.Collections.ArrayList>, lub <xref:System.Collections.CollectionBase>. Są indeksowane listę elementów typu <xref:System.Object>. Te listy musi zawierać jednorodnego typów, ponieważ pierwszy element indeks Określa typ. <xref:System.Collections.IList> będą dostępne dla powiązania tylko w czasie wykonywania.

  > [!NOTE]
  >  Jeśli chcesz utworzyć listę obiektów biznesowych dla powiązania za pomocą interfejsu Windows Forms, należy rozważyć użycie <xref:System.ComponentModel.BindingList%601>. <xref:System.ComponentModel.BindingList%601> Jest klasą rozszerzonego, która implementuje interfejsy podstawowe wymagane dla dwukierunkowego powiązanie danych formularzy Windows.

- <xref:System.ComponentModel.IBindingList> Interfejs

  Klasa, która implementuje <xref:System.ComponentModel.IBindingList> interfejs zapewnia znacznie wyższy poziom funkcji wiązania danych. Ta implementacja oferuje podstawowe funkcje sortowania i powiadomienia o zmianie, zarówno dla aplikacji po liście elementów zmiany (na przykład, trzeci element na liście klientów zawiera zmiany do pola adres), a także podczas zmiany samej listy (na przykład Liczba elementów na liście zwiększa lub zmniejsza). Powiadomienie o zmianie jest ważne, jeśli planowane jest powiązany z tych samych danych jest kilka formantów i chcesz, aby zmiany danych w jednej z kontrolek propagowane do innych formantów powiązanych.

  > [!NOTE]
  > Powiadomienie o zmianie jest włączona dla <xref:System.ComponentModel.IBindingList> interfejs za pomocą <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A> właściwość które, gdy `true`, zgłasza <xref:System.ComponentModel.IBindingList.ListChanged> zdarzeń, wskazujący, listy, zmienić lub element na liście zmienione.

  Typ zmiany jest opisana przez <xref:System.ComponentModel.ListChangedType> właściwość <xref:System.ComponentModel.ListChangedEventArgs> parametru. Dzięki temu przy każdej aktualizacji modelu danych wszelkie zależne widoków, takich jak inne formanty związane z tego samego źródła danych zostaną również zaktualizowane. Obiektów zawartych w liście będzie jednak być powiadamiana listy, które zmieniają się tak, aby umieszczać listy <xref:System.ComponentModel.IBindingList.ListChanged> zdarzeń.

  > [!NOTE]
  > <xref:System.ComponentModel.BindingList%601> Udostępnia ogólną implementację <xref:System.ComponentModel.IBindingList> interfejsu.

- <xref:System.ComponentModel.IBindingListView> Interfejs

  Klasę, która implementuje <xref:System.ComponentModel.IBindingListView> interfejs zapewnia wszystkie funkcje programu implementację <xref:System.ComponentModel.IBindingList>, jak również jako filtrowania i zaawansowane funkcje sortowania. Ta implementacja oferuje filtrowania na podstawie ciągu i wielokolumnowe sortowanie za pomocą właściwości deskryptora kierunku rozmieszczania zawartości śródwierszowej pary.

- <xref:System.ComponentModel.IEditableObject> Interfejs

  Klasa, która implementuje <xref:System.ComponentModel.IEditableObject> interfejs umożliwia obiektu do kontrolowania, kiedy zmiany do tego obiektu są trwałe. Ta implementacja zapewnia <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, i <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metody, które umożliwiają wycofać zmiany wprowadzone do obiektu. Poniżej przedstawiono krótki opis działania <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, i <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metody i jak działają w połączeniu ze sobą, aby włączyć możliwości wycofania zmian wprowadzonych do danych:

  - <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> Metoda sygnalizuje rozpoczęcia edycji obiektu. Obiekt, który implementuje ten interfejs należy przechowywać wszelkie aktualizacje po <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> wywołania metody w taki sposób, odrzucone aktualizacje Jeśli <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metoda jest wywoływana. W danych powiązania Windows Forms, można wywołać <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> wiele razy w zakresie jednej Edytowanie transakcji (na przykład <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>). Implementacje <xref:System.ComponentModel.IEditableObject> należy śledzić czy <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> została już wywołana i Ignoruj kolejnych wywołań <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>. Ponieważ ta metoda może być wywoływana wiele razy, ważne jest, że kolejne wywołania do niego były bezpieczne; oznacza to, że kolejne <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> wywołania nie można zniszczyć aktualizacji, które zostały wprowadzone, lub zmiany danych, który został zapisany w pierwszym <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> wywołania.

  - <xref:System.ComponentModel.IEditableObject.EndEdit%2A> Metoda wypycha wszelkie zmiany wprowadzone od <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> zostało wywołane w odniesieniu do obiektu źródłowego, jeśli obiekt znajduje się obecnie w trybie edycji.

  - <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> Metoda odrzuca zmiany wprowadzone do obiektu.

  Aby uzyskać więcej informacji o tym, jak <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>, i <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metody pracy, zobacz [zapisać dane w bazie danych](/visualstudio/data-tools/save-data-back-to-the-database).

  Pojęcie to transakcyjnych funkcji danych jest używany przez <xref:System.Windows.Forms.DataGridView> kontroli.

- <xref:System.ComponentModel.ICancelAddNew> Interfejs

  Klasa, która implementuje <xref:System.ComponentModel.ICancelAddNew> zwykle implementuje interfejs <xref:System.ComponentModel.IBindingList> interfejs i umożliwia przywracanie dodawania wprowadzone do źródła danych za pomocą <xref:System.ComponentModel.IBindingList.AddNew%2A> metody. Jeśli dane źródłowe implementuje <xref:System.ComponentModel.IBindingList> interfejsu, również należy ją zaimplementować <xref:System.ComponentModel.ICancelAddNew> interfejsu.

- <xref:System.ComponentModel.IDataErrorInfo> Interfejs

  Klasa, która implementuje <xref:System.ComponentModel.IDataErrorInfo> interfejs umożliwia obiekty do zaoferowania błędów niestandardowych informacji do kontrolki powiązania:

  - <xref:System.ComponentModel.IDataErrorInfo.Error%2A> Właściwość zwraca tekst komunikatu o błędzie ogólne (na przykład "Wystąpił błąd").

  - <xref:System.ComponentModel.IDataErrorInfo.Item%2A> Właściwość zwraca ciąg zawierający komunikat o błędzie z kolumny (na przykład "wartości w `State` kolumny jest nieprawidłowa").

- <xref:System.Collections.IEnumerable> Interfejs

  Klasa, która implementuje <xref:System.Collections.IEnumerable> interfejs jest zwykle używany przez [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]. Obsługa formularzy Windows dla tego interfejsu jest dostępna tylko <xref:System.Windows.Forms.BindingSource> składnika.

  > [!NOTE]
  > <xref:System.Windows.Forms.BindingSource> Składnika kopiuje wszystkie <xref:System.Collections.IEnumerable> elementy do osobną listę dla powiązania celów.

- <xref:System.ComponentModel.ITypedList> Interfejs

  Klasy kolekcji, która implementuje <xref:System.ComponentModel.ITypedList> interfejs zapewnia możliwość kontrolowania kolejności i zestaw właściwości, połączenie z powiązanej kontrolki.

  > [!NOTE]
  > Podczas implementacji <xref:System.ComponentModel.ITypedList.GetItemProperties%2A> metody i <xref:System.ComponentModel.PropertyDescriptor> tablicy nie ma wartości null, ostatni wpis w tablicy będzie deskryptora właściwości, która opisuje właściwość listy, który jest inny listę elementów.

- <xref:System.ComponentModel.ICustomTypeDescriptor> Interfejs

  Klasa, która implementuje <xref:System.ComponentModel.ICustomTypeDescriptor> interfejs umożliwia dynamiczne informacje o sobie samym. Ten interfejs jest podobne do <xref:System.ComponentModel.ITypedList> , ale jest używana dla obiektów, a nie listy. Ten interfejs jest wykorzystywany przez <xref:System.Data.DataRowView> do projektu schematu źródłowe wiersze. Proste wdrażanie <xref:System.ComponentModel.ICustomTypeDescriptor> są dostarczane przez <xref:System.ComponentModel.CustomTypeDescriptor> klasy.

  > [!NOTE]
  > Do pomocy technicznej czasu projektowania powiązanie z typami, które implementują <xref:System.ComponentModel.ICustomTypeDescriptor>, typ musi implementować też <xref:System.ComponentModel.IComponent> i istnieje jako wystąpienie w formularzu.

- <xref:System.ComponentModel.IListSource> Interfejs

  Klasa, która implementuje <xref:System.ComponentModel.IListSource> interfejs umożliwia oparte na liście powiązań-list obiektów. <xref:System.ComponentModel.IListSource.GetList%2A> Metody <xref:System.ComponentModel.IListSource> służy do zwracania listy może być powiązana z obiektu, który nie dziedziczy <xref:System.Collections.IList>. <xref:System.ComponentModel.IListSource> jest używany przez <xref:System.Data.DataSet> klasy.

- <xref:System.ComponentModel.IRaiseItemChangedEvents> Interfejs

  Klasa, która implementuje <xref:System.ComponentModel.IRaiseItemChangedEvents> interfejs jest lista może być powiązana, który także implementuje <xref:System.ComponentModel.IBindingList> interfejsu. Ten interfejs jest używany do wskazania, jeśli danego typu wywołuje <xref:System.ComponentModel.IBindingList.ListChanged> zdarzeń typu <xref:System.ComponentModel.ListChangedType.ItemChanged> za pośrednictwem jego <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A> właściwości.

  > [!NOTE]
  > Należy zaimplementować <xref:System.ComponentModel.IRaiseItemChangedEvents> Jeśli źródło danych zawiera właściwości do konwersji zdarzenia listy opisanych powyżej i prowadzi interakcję z <xref:System.Windows.Forms.BindingSource> składnika. W przeciwnym razie <xref:System.Windows.Forms.BindingSource> przeprowadzi również właściwość do konwersji zdarzenia listy skutkuje niższej wydajności.

- <xref:System.ComponentModel.ISupportInitialize> Interfejs

  Składnik, który implementuje <xref:System.ComponentModel.ISupportInitialize> ma zalety optymalizacje usługi batch do ustawiania właściwości i zależnych od wspólnej właściwości inicjalizacji. <xref:System.ComponentModel.ISupportInitialize> Zawiera dwie metody:

  - <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> sygnalizuje, że inicjowanie tego obiektu jest uruchamiana.

  - <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> sygnalizuje, że dobiega inicjowanie tego obiektu.

- <xref:System.ComponentModel.ISupportInitializeNotification> Interfejs

  Składnik, który implementuje <xref:System.ComponentModel.ISupportInitializeNotification> również interfejs implementuje <xref:System.ComponentModel.ISupportInitialize> interfejsu. Ten interfejs umożliwia powiadomić inne <xref:System.ComponentModel.ISupportInitialize> składniki tej Inicjowanie zostało zakończone. <xref:System.ComponentModel.ISupportInitializeNotification> Interfejs zawiera dwa elementy członkowskie:

  - <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A> Zwraca `boolean` wartość wskazującą, czy składnik jest zainicjowany.

  - <xref:System.ComponentModel.ISupportInitializeNotification.Initialized> występuje, gdy <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> jest wywoływana.

- <xref:System.ComponentModel.INotifyPropertyChanged> Interfejs

  Klasa, która implementuje ten interfejs jest typem, który wywołuje zdarzenie, gdy zmienią się dowolnej wartości właściwości. Ten interfejs jest przeznaczony do Zastąp wzorzec o zdarzenia zmiany, dla każdej właściwości formantu. Gdy są używane w <xref:System.ComponentModel.BindingList%601>, powinny implementować obiektem biznesowym <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu i BindingList\`przekonwertuje 1 <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenia <xref:System.ComponentModel.BindingList%601.ListChanged> zdarzeń typu <xref:System.ComponentModel.ListChangedType.ItemChanged>.

  > [!NOTE]
  > Zmiany powiadomienia w powiązania między klientem powiązanych danych źródła typu powiązanego źródła danych albo zaimplementować <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu (preferowany) lub może zapewnić *propertyName* `Changed` zdarzenia powiązane, ale nie należy wykonać obie czynności.

### <a name="interfaces-for-implementation-by-component-authors"></a>Interfejsy do implementacji przez autorów składnika

Następujące interfejsy są przeznaczone do użycia przez aparat powiązanie danych formularzy Windows:

- <xref:System.Windows.Forms.IBindableComponent> Interfejs

  Klasa, która implementuje ten interfejs jest składnikiem innej kontrolki obsługującej powiązanie danych. Ta klasa zwraca powiązań danych i kontekstu powiązania składnika za pomocą <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> i <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> właściwości tego interfejsu.

  > [!NOTE]
  > Jeśli składnik dziedziczy z <xref:System.Windows.Forms.Control>, nie trzeba do zaimplementowania <xref:System.Windows.Forms.IBindableComponent> interfejsu.

- <xref:System.Windows.Forms.ICurrencyManagerProvider> Interfejs

  Klasa, która implementuje <xref:System.Windows.Forms.ICurrencyManagerProvider> interfejs jest składnikiem, który udostępnia swoje własne <xref:System.Windows.Forms.CurrencyManager> Zarządzanie powiązań skojarzone z tym konkretnym składnikiem. Dostęp do niestandardowej <xref:System.Windows.Forms.CurrencyManager> są dostarczane przez <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> właściwości.

  > [!NOTE]
  > Klasa, która dziedziczy <xref:System.Windows.Forms.Control> zarządza automatycznie za pomocą powiązania jej <xref:System.Windows.Forms.Control.BindingContext%2A> właściwości, więc przypadki, w których należy zaimplementować <xref:System.Windows.Forms.ICurrencyManagerProvider> są stosunkowo rzadkie.

## <a name="see-also"></a>Zobacz także

- [Wiązanie danych i formularzy Windows Forms](data-binding-and-windows-forms.md)
- [Instrukcje: Tworzenie prostego formantu powiązanego na formularzu Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Wiązanie danych formularzy Windows Forms](windows-forms-data-binding.md)

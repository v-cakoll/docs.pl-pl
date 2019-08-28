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
ms.openlocfilehash: 9f102b584d2ed0b5a9d2bbb0e7ce3f7871ec40b2
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046371"
---
# <a name="interfaces-related-to-data-binding"></a>Interfejsy dotyczące wiązania danych

Za pomocą ADO.NET można utworzyć wiele różnych struktur danych, aby odpowiadały potrzebom związanym z wiązaniem aplikacji i danymi, z którymi pracujesz. Możesz chcieć utworzyć własne klasy, które udostępniają lub zużywają dane w Windows Forms. Te obiekty mogą oferować różne poziomy funkcjonalności i złożoności, od podstawowego powiązania danych, zapewniające wsparcie w czasie projektowania, sprawdzanie błędów, powiadamianie o zmianach, a nawet obsługę strukturalnego wycofywania zmian wprowadzonych w samych danych.

## <a name="consumers-of-data-binding-interfaces"></a>Odbiorcy interfejsów powiązań danych

W poniższych sekcjach opisano dwie grupy obiektów interfejsu. Pierwsza grupa zawiera listę interfejsów, które są zaimplementowane dla źródeł danych przez autorów źródła danych. Te interfejsy zostały zaprojektowane tak, aby były używane przez konsumentów ze źródłami danych, które w większości przypadków Windows Formsą kontrolki lub składniki. Druga grupa zawiera listę interfejsów przeznaczonych do użycia przez autorów składników. Autorzy składników używają tych interfejsów podczas tworzenia składnika, który obsługuje powiązanie danych, aby można go było wykorzystać przez aparat powiązań danych Windows Forms. Te interfejsy można zaimplementować w ramach klas skojarzonych z formularzem w celu włączenia wiązania danych; Każdy przypadek przedstawia klasę, która implementuje interfejs, który umożliwia interakcję z danymi. Narzędzia do projektowania danych programu Visual Studio Rapid Application Development (RAD) korzystają już z tych funkcji.

### <a name="interfaces-for-implementation-by-data-source-authors"></a>Interfejsy dla implementacji przez autorów źródła danych

Następujące interfejsy zostały zaprojektowane tak, aby były używane przez Windows Forms formanty:

- <xref:System.Collections.IList>interfejsu

  Klasa implementująca <xref:System.Collections.IList> interfejs może <xref:System.Array>być, <xref:System.Collections.ArrayList>, lub <xref:System.Collections.CollectionBase>. Są to indeksowane listy elementów typu <xref:System.Object>. Te listy muszą zawierać typy jednorodne, ponieważ pierwszy element indeksu określa typ. <xref:System.Collections.IList>będzie dostępna do powiązania tylko w czasie wykonywania.

  > [!NOTE]
  > Jeśli chcesz utworzyć listę obiektów biznesowych do powiązania z Windows Forms, należy rozważyć użycie <xref:System.ComponentModel.BindingList%601>. <xref:System.ComponentModel.BindingList%601> Jest rozszerzalną klasą implementującą interfejsy podstawowe wymagane do dwukierunkowego wiązania danych Windows Forms.

- <xref:System.ComponentModel.IBindingList>interfejsu

  Klasa implementująca <xref:System.ComponentModel.IBindingList> interfejs zapewnia znacznie wyższy poziom funkcjonalności dotyczącej powiązań danych. Ta implementacja oferuje podstawowe możliwości sortowania i powiadomienia o zmianach, zarówno w przypadku zmiany elementów listy (na przykład trzeci element na liście klientów ma zmianę w polu adres), a także kiedy zmienia się sama lista (na przykład Liczba elementów na liście wzrasta lub maleje. Powiadamianie o zmianach jest ważne, jeśli planujesz posiadanie wielu kontrolek powiązanych z tymi samymi danymi, a zmiany danych w jednej z formantów mają być propagowane do innych kontrolek powiązanych.

  > [!NOTE]
  > Powiadomienie o zmianie jest włączone dla <xref:System.ComponentModel.IBindingList> interfejsu <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A> za pomocą właściwości <xref:System.ComponentModel.IBindingList.ListChanged> , która, `true`gdy wywołuje zdarzenie, wskazujące na zmianę listy lub zmianę elementu na liście.

  Typ zmiany jest opisany przez <xref:System.ComponentModel.ListChangedType> Właściwość <xref:System.ComponentModel.ListChangedEventArgs> parametru. W związku z tym zawsze, gdy model danych zostanie zaktualizowany, wszystkie widoki zależne, takie jak inne kontrolki powiązane z tym samym źródłem danych, również zostaną zaktualizowane. Jednak obiekty zawarte na liście będą musiały powiadomić listę, gdy się zmienią, tak aby lista mogła zgłosić <xref:System.ComponentModel.IBindingList.ListChanged> zdarzenie.

  > [!NOTE]
  > Zapewnia ogólną implementację <xref:System.ComponentModel.IBindingList>interfejsu. <xref:System.ComponentModel.BindingList%601>

- <xref:System.ComponentModel.IBindingListView>interfejsu

  Klasa implementująca <xref:System.ComponentModel.IBindingListView> interfejs zapewnia wszystkie funkcje <xref:System.ComponentModel.IBindingList>implementacji, a także filtrowanie i zaawansowane funkcje sortowania. Ta implementacja oferuje filtrowanie na podstawie ciągów oraz sortowanie wielokolumnowe z parami właściwości.

- <xref:System.ComponentModel.IEditableObject>interfejsu

  Klasa implementująca <xref:System.ComponentModel.IEditableObject> interfejs pozwala obiektowi kontrolować, kiedy zmiany w tym obiekcie są trwałe. Ta implementacja zapewnia <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> <xref:System.ComponentModel.IEditableObject.EndEdit%2A>metody, i <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> , które umożliwiają wycofywanie zmian wprowadzonych w obiekcie. Poniżej przedstawiono krótkie wyjaśnienie działania <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>metod,, i <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> sposób ich <xref:System.ComponentModel.IEditableObject.EndEdit%2A>współdziałania ze sobą, aby umożliwić możliwość wycofania zmian wprowadzonych w danych:

  - <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> Metoda sygnalizuje początek edycji obiektu. Obiekt, który implementuje ten interfejs, będzie musiał przechowywać wszelkie aktualizacje po <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> wywołaniu metody w taki sposób, aby można było odrzucić aktualizacje, <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> Jeśli metoda zostanie wywołana. W Windows Forms powiązań danych można wywoływać <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> wiele razy w zakresie pojedynczej transakcji edycji (na <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>przykład <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> <xref:System.ComponentModel.IEditableObject.EndEdit%2A>,,). Implementacje <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>powinny śledzić, czy zostały już wywołane i ignorować kolejne wywołania do. <xref:System.ComponentModel.IEditableObject> Ponieważ ta metoda może być wywoływana wiele razy, ważne jest, aby kolejne wywołania były niebezpieczne. oznacza to, że <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> kolejne wywołania nie mogą zniszczyć aktualizacji, które zostały wprowadzone, lub zmienić danych, które zostały zapisane podczas <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> pierwszego wywołania.

  - Metoda wypycha wszystkie zmiany od momentu <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> wywołania do obiektu bazowego, jeśli obiekt jest obecnie w trybie edycji. <xref:System.ComponentModel.IEditableObject.EndEdit%2A>

  - <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> Metoda odrzuca wszystkie zmiany wprowadzone do obiektu.

  Aby uzyskać więcej informacji o tym <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> <xref:System.ComponentModel.IEditableObject.EndEdit%2A> <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> , jak działają metody,, zobacz [Zapisywanie danych z powrotem do bazy danych](/visualstudio/data-tools/save-data-back-to-the-database).

  Ta transakcyjna funkcja danych jest używana przez <xref:System.Windows.Forms.DataGridView> formant.

- <xref:System.ComponentModel.ICancelAddNew>interfejsu

  Klasa implementująca <xref:System.ComponentModel.ICancelAddNew> interfejs zazwyczaj <xref:System.ComponentModel.IBindingList> implementuje interfejs i umożliwia wycofanie dodania dokonanego do źródła danych za pomocą <xref:System.ComponentModel.IBindingList.AddNew%2A> metody. Jeśli źródło danych implementuje <xref:System.ComponentModel.IBindingList> interfejs, należy również <xref:System.ComponentModel.ICancelAddNew> zaimplementować interfejs.

- <xref:System.ComponentModel.IDataErrorInfo>interfejsu

  Klasa implementująca <xref:System.ComponentModel.IDataErrorInfo> interfejs umożliwia obiektom oferowanie niestandardowych informacji o błędach w formantach powiązanych:

  - Ta <xref:System.ComponentModel.IDataErrorInfo.Error%2A> Właściwość zwraca ogólny tekst komunikatu o błędzie (na przykład "Wystąpił błąd").

  - Właściwość zwraca ciąg z określonym komunikatem o błędzie z kolumny (na przykład "wartość `State` w kolumnie jest nieprawidłowa"). <xref:System.ComponentModel.IDataErrorInfo.Item%2A>

- <xref:System.Collections.IEnumerable>interfejsu

  Klasa implementująca <xref:System.Collections.IEnumerable> interfejs jest zwykle używana przez ASP.NET. Obsługa Windows Forms dla tego interfejsu jest dostępna tylko za pomocą <xref:System.Windows.Forms.BindingSource> składnika.

  > [!NOTE]
  > Składnik kopiuje wszystkie <xref:System.Collections.IEnumerable> elementy do osobnej listy w celu powiązania. <xref:System.Windows.Forms.BindingSource>

- <xref:System.ComponentModel.ITypedList>interfejsu

  Klasa kolekcji implementująca <xref:System.ComponentModel.ITypedList> interfejs umożliwia sterowanie kolejnością i zestawem właściwości dostępnych dla kontrolki powiązanej.

  > [!NOTE]
  > Podczas implementowania <xref:System.ComponentModel.ITypedList.GetItemProperties%2A> metody, <xref:System.ComponentModel.PropertyDescriptor> a tablica nie ma wartości null, ostatni wpis w tablicy będzie deskryptorem właściwości opisującym Właściwość list, która jest kolejną listą elementów.

- <xref:System.ComponentModel.ICustomTypeDescriptor>interfejsu

  Klasa implementująca <xref:System.ComponentModel.ICustomTypeDescriptor> interfejs zapewnia dynamiczne informacje o sobie. Ten interfejs jest podobny do <xref:System.ComponentModel.ITypedList> , ale jest używany w przypadku obiektów zamiast list. Ten interfejs jest używany przez <xref:System.Data.DataRowView> program do zaprojektowania schematu wierszy bazowych. Prosta implementacja <xref:System.ComponentModel.ICustomTypeDescriptor> jest dostarczana <xref:System.ComponentModel.CustomTypeDescriptor> przez klasę.

  > [!NOTE]
  > Aby zapewnić obsługę powiązania czasu projektowania do typów, które <xref:System.ComponentModel.ICustomTypeDescriptor>implementują, typ musi również <xref:System.ComponentModel.IComponent> implementować i istnieć jako wystąpienie w formularzu.

- <xref:System.ComponentModel.IListSource>interfejsu

  Klasa implementująca <xref:System.ComponentModel.IListSource> interfejs włącza powiązanie oparte na liście dla obiektów niebędących listą. Metoda jest używana do zwrócenia listy możliwej do powiązania z obiektu, który nie dziedziczy z <xref:System.Collections.IList>. <xref:System.ComponentModel.IListSource.GetList%2A> <xref:System.ComponentModel.IListSource> <xref:System.ComponentModel.IListSource>jest używany przez <xref:System.Data.DataSet> klasę.

- <xref:System.ComponentModel.IRaiseItemChangedEvents>interfejsu

  Klasa implementująca <xref:System.ComponentModel.IRaiseItemChangedEvents> interfejs jest listą z powiązaniem, która również <xref:System.ComponentModel.IBindingList> implementuje interfejs. Ten interfejs służy do wskazywania, czy typ wywołuje <xref:System.ComponentModel.IBindingList.ListChanged> zdarzenia typu <xref:System.ComponentModel.ListChangedType.ItemChanged> za za poorednictwem <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A> jego właściwości.

  > [!NOTE]
  > Należy zaimplementować, <xref:System.ComponentModel.IRaiseItemChangedEvents> Jeśli źródło danych zawiera właściwość zawierającą poprzednio opisaną konwersję zdarzeń i działa <xref:System.Windows.Forms.BindingSource> ze składnikiem. W przeciwnym razie <xref:System.Windows.Forms.BindingSource> zostanie również wykonana właściwość, aby wyświetlić listę konwersji zdarzeń powodującą wolniejszą wydajność.

- <xref:System.ComponentModel.ISupportInitialize>interfejsu

  Składnik implementujący <xref:System.ComponentModel.ISupportInitialize> interfejs ma zalety optymalizacji partii, aby ustawić właściwości i inicjować właściwości współzależne. <xref:System.ComponentModel.ISupportInitialize> Zawiera dwie metody:

  - <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A>sygnalizuje, że Inicjalizacja obiektu jest uruchamiana.

  - <xref:System.ComponentModel.ISupportInitialize.EndInit%2A>sygnalizuje zakończenie inicjowania obiektu.

- <xref:System.ComponentModel.ISupportInitializeNotification>interfejsu

  Składnik <xref:System.ComponentModel.ISupportInitializeNotification> implementujący interfejs również <xref:System.ComponentModel.ISupportInitialize> implementuje interfejs. Ten interfejs umożliwia powiadomienie innych <xref:System.ComponentModel.ISupportInitialize> składników, które zakończyły się inicjalizacją. <xref:System.ComponentModel.ISupportInitializeNotification> Interfejs zawiera dwa elementy członkowskie:

  - <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A>`boolean` zwraca wartość wskazującą, czy składnik jest zainicjowany.

  - <xref:System.ComponentModel.ISupportInitializeNotification.Initialized>występuje, <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> gdy jest wywoływana.

- <xref:System.ComponentModel.INotifyPropertyChanged>interfejsu

  Klasa implementująca ten interfejs jest typem, który wywołuje zdarzenie, gdy dowolna z jego wartości właściwości zostanie zmieniona. Ten interfejs jest przeznaczony do zastępowania wzorca mającego zdarzenie zmiany dla każdej właściwości formantu. W przypadku użycia w <xref:System.ComponentModel.BindingList%601>, obiekt biznesowy powinien <xref:System.ComponentModel.INotifyPropertyChanged> implementować interfejs, a BindingList\`1 przekonwertuje <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenia na <xref:System.ComponentModel.BindingList%601.ListChanged> zdarzenia typu <xref:System.ComponentModel.ListChangedType.ItemChanged>.

  > [!NOTE]
  > Aby powiadomienie o zmianie miało miejsce w powiązaniu między klientem związanym a źródłem danych, dla którego powiązany Typ źródła danych powinien implementować <xref:System.ComponentModel.INotifyPropertyChanged> interfejs (preferowany) lub można dostarczyć zdarzenia *PropertyName* `Changed` dla powiązanego typu, ale nie należy tego robić jednocześnie.

### <a name="interfaces-for-implementation-by-component-authors"></a>Interfejsy dla implementacji przez autorów składników

Następujące interfejsy zostały zaprojektowane do użytku przez aparat powiązań danych Windows Forms:

- <xref:System.Windows.Forms.IBindableComponent>interfejsu

  Klasa implementująca ten interfejs to składnik niebędący kontrolką, który obsługuje powiązanie danych. Ta klasa zwraca powiązania danych i kontekst powiązania składnika za pomocą <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> właściwości i <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> tego interfejsu.

  > [!NOTE]
  > Jeśli składnik dziedziczy z <xref:System.Windows.Forms.Control>, nie trzeba <xref:System.Windows.Forms.IBindableComponent> implementować interfejsu.

- <xref:System.Windows.Forms.ICurrencyManagerProvider>interfejsu

  Klasa implementująca <xref:System.Windows.Forms.ICurrencyManagerProvider> interfejs jest składnikiem, który udostępnia własne <xref:System.Windows.Forms.CurrencyManager> powiązania skojarzone z tym konkretnym składnikiem. Dostęp do niestandardowego <xref:System.Windows.Forms.CurrencyManager> jest udostępniany <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> przez właściwość.

  > [!NOTE]
  > Klasa, która dziedziczy z <xref:System.Windows.Forms.Control> zarządzanych powiązań automatycznie za pośrednictwem swojej <xref:System.Windows.Forms.Control.BindingContext%2A> właściwości, więc przypadki, w których należy zaimplementować <xref:System.Windows.Forms.ICurrencyManagerProvider> , są dość rzadki.

## <a name="see-also"></a>Zobacz także

- [Wiązanie danych i formularzy Windows Forms](data-binding-and-windows-forms.md)
- [Instrukcje: Tworzenie prostego formantu powiązanego w formularzu systemu Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Wiązanie danych formularzy Windows Forms](windows-forms-data-binding.md)

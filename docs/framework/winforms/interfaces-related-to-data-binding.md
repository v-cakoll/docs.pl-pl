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
ms.openlocfilehash: 4e40f7ec1922cdf43e6a0b8f5734acaaeefbc514
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834591"
---
# <a name="interfaces-related-to-data-binding"></a>Interfejsy dotyczące wiązania danych

Za pomocą ADO.NET można utworzyć wiele różnych struktur danych, aby odpowiadały potrzebom związanym z wiązaniem aplikacji i danymi, z którymi pracujesz. Możesz chcieć utworzyć własne klasy, które udostępniają lub zużywają dane w Windows Forms. Te obiekty mogą oferować różne poziomy funkcjonalności i złożoności, od podstawowego powiązania danych, zapewniające wsparcie w czasie projektowania, sprawdzanie błędów, powiadamianie o zmianach, a nawet obsługę strukturalnego wycofywania zmian wprowadzonych w samych danych.

## <a name="consumers-of-data-binding-interfaces"></a>Odbiorcy interfejsów powiązań danych

W poniższych sekcjach opisano dwie grupy obiektów interfejsu. Pierwsza grupa zawiera listę interfejsów, które są zaimplementowane dla źródeł danych przez autorów źródła danych. Te interfejsy zostały zaprojektowane tak, aby były używane przez konsumentów ze źródłami danych, które w większości przypadków Windows Formsą kontrolki lub składniki. Druga grupa zawiera listę interfejsów przeznaczonych do użycia przez autorów składników. Autorzy składników używają tych interfejsów podczas tworzenia składnika, który obsługuje powiązanie danych, aby można go było wykorzystać przez aparat powiązań danych Windows Forms. Te interfejsy można zaimplementować w ramach klas skojarzonych z formularzem w celu włączenia wiązania danych; Każdy przypadek przedstawia klasę, która implementuje interfejs, który umożliwia interakcję z danymi. Narzędzia do projektowania danych programu Visual Studio Rapid Application Development (RAD) korzystają już z tych funkcji.

### <a name="interfaces-for-implementation-by-data-source-authors"></a>Interfejsy dla implementacji przez autorów źródła danych

Następujące interfejsy zostały zaprojektowane tak, aby były używane przez Windows Forms formanty:

- Interfejs <xref:System.Collections.IList>

  Klasa implementująca interfejs <xref:System.Collections.IList> może być <xref:System.Array>, <xref:System.Collections.ArrayList>lub <xref:System.Collections.CollectionBase>. Są to indeksowane listy elementów typu <xref:System.Object>. Te listy muszą zawierać typy jednorodne, ponieważ pierwszy element indeksu określa typ. <xref:System.Collections.IList> byłyby dostępne do powiązania tylko w czasie wykonywania.

  > [!NOTE]
  > Jeśli chcesz utworzyć listę obiektów biznesowych do powiązania z Windows Forms, należy rozważyć użycie <xref:System.ComponentModel.BindingList%601>. <xref:System.ComponentModel.BindingList%601> jest rozszerzalną klasą implementującą interfejsy podstawowe wymagane dla dwuWindows Forms kierunkowego powiązania danych.

- Interfejs <xref:System.ComponentModel.IBindingList>

  Klasa implementująca interfejs <xref:System.ComponentModel.IBindingList> zapewnia znacznie wyższy poziom funkcjonalności dotyczącej powiązań danych. Ta implementacja oferuje podstawowe możliwości sortowania i powiadomienia o zmianach, zarówno w przypadku zmiany elementów listy (na przykład trzeci element na liście klientów ma zmianę w polu adres), a także kiedy zmienia się sama lista (na przykład Liczba elementów na liście wzrasta lub maleje. Powiadamianie o zmianach jest ważne, jeśli planujesz posiadanie wielu kontrolek powiązanych z tymi samymi danymi, a zmiany danych w jednej z formantów mają być propagowane do innych kontrolek powiązanych.

  > [!NOTE]
  > Powiadomienie o zmianie jest włączone dla interfejsu <xref:System.ComponentModel.IBindingList> za pomocą właściwości <xref:System.ComponentModel.IBindingList.SupportsChangeNotification%2A>, która w przypadku `true`wywołuje zdarzenie <xref:System.ComponentModel.IBindingList.ListChanged>, wskazując na zmianę listy lub zmianę elementu na liście.

  Typ zmiany jest opisany przez właściwość <xref:System.ComponentModel.ListChangedType> parametru <xref:System.ComponentModel.ListChangedEventArgs>. W związku z tym zawsze, gdy model danych zostanie zaktualizowany, wszystkie widoki zależne, takie jak inne kontrolki powiązane z tym samym źródłem danych, również zostaną zaktualizowane. Jednak obiekty zawarte na liście będą musiały powiadomić listę, gdy zmienią się tak, aby lista mogła zgłosić zdarzenie <xref:System.ComponentModel.IBindingList.ListChanged>.

  > [!NOTE]
  > <xref:System.ComponentModel.BindingList%601> zapewnia ogólną implementację interfejsu <xref:System.ComponentModel.IBindingList>.

- Interfejs <xref:System.ComponentModel.IBindingListView>

  Klasa implementująca interfejs <xref:System.ComponentModel.IBindingListView> zapewnia wszystkie funkcje implementacji <xref:System.ComponentModel.IBindingList>, a także filtrowanie i zaawansowane funkcje sortowania. Ta implementacja oferuje filtrowanie na podstawie ciągów oraz sortowanie wielokolumnowe z parami właściwości.

- Interfejs <xref:System.ComponentModel.IEditableObject>

  Klasa implementująca interfejs <xref:System.ComponentModel.IEditableObject> pozwala obiektowi kontrolować, kiedy zmiany w tym obiekcie są trwałe. Ta implementacja zapewnia <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>i <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> metody, które umożliwiają wycofanie zmian wprowadzonych do obiektu. Poniżej znajduje się krótki opis działania metod <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>i <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> oraz sposób ich współdziałania ze sobą, aby umożliwić możliwość wycofania zmian wprowadzonych w danych:

  - Metoda <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> sygnalizuje początek edycji obiektu. Obiekt, który implementuje ten interfejs, będzie musiał przechowywać wszelkie aktualizacje po wywołaniu metody <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> w taki sposób, aby można było odrzucić aktualizacje, jeśli metoda <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> zostanie wywołana. W Windows Forms powiązań danych można wywoływać <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> wiele razy w zakresie pojedynczej transakcji edycji (na przykład <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>). Implementacje <xref:System.ComponentModel.IEditableObject> powinny śledzić czy <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> zostały już wywołane i ignorować kolejne wywołania do <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>. Ponieważ ta metoda może być wywoływana wiele razy, ważne jest, aby kolejne wywołania były niebezpieczne. oznacza to, że kolejne wywołania <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> nie mogą zniszczyć aktualizacji, które zostały wprowadzone, lub zmienić danych, które zostały zapisane podczas pierwszego wywołania <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>.

  - Metoda <xref:System.ComponentModel.IEditableObject.EndEdit%2A> wypycha wszystkie zmiany od momentu, gdy <xref:System.ComponentModel.IEditableObject.BeginEdit%2A> został wywołany w obiekcie źródłowym, jeśli obiekt jest obecnie w trybie edycji.

  - Metoda <xref:System.ComponentModel.IEditableObject.CancelEdit%2A> odrzuca wszelkie zmiany wprowadzone do obiektu.

  Aby uzyskać więcej informacji na temat działania metod <xref:System.ComponentModel.IEditableObject.BeginEdit%2A>, <xref:System.ComponentModel.IEditableObject.EndEdit%2A>i <xref:System.ComponentModel.IEditableObject.CancelEdit%2A>, zobacz [Zapisywanie danych z powrotem w bazie danych](/visualstudio/data-tools/save-data-back-to-the-database).

  Ta transakcyjna funkcja danych jest używana przez formant <xref:System.Windows.Forms.DataGridView>.

- Interfejs <xref:System.ComponentModel.ICancelAddNew>

  Klasa implementująca interfejs <xref:System.ComponentModel.ICancelAddNew> zwykle implementuje interfejs <xref:System.ComponentModel.IBindingList> i umożliwia wycofanie dodania dokonanego do źródła danych za pomocą metody <xref:System.ComponentModel.IBindingList.AddNew%2A>. Jeśli źródło danych implementuje interfejs <xref:System.ComponentModel.IBindingList>, należy również zaimplementować interfejs <xref:System.ComponentModel.ICancelAddNew>.

- Interfejs <xref:System.ComponentModel.IDataErrorInfo>

  Klasa implementująca interfejs <xref:System.ComponentModel.IDataErrorInfo> umożliwia obiektom oferowanie niestandardowych informacji o błędach w formantach powiązanych:

  - Właściwość <xref:System.ComponentModel.IDataErrorInfo.Error%2A> zwraca ogólny tekst komunikatu o błędzie (na przykład "Wystąpił błąd").

  - Właściwość <xref:System.ComponentModel.IDataErrorInfo.Item%2A> zwraca ciąg z określonym komunikatem o błędzie z kolumny (na przykład "wartość w kolumnie `State` jest nieprawidłowa").

- Interfejs <xref:System.Collections.IEnumerable>

  Klasa implementująca interfejs <xref:System.Collections.IEnumerable> jest zwykle używana przez ASP.NET. Obsługa Windows Forms dla tego interfejsu jest dostępna tylko za pomocą składnika <xref:System.Windows.Forms.BindingSource>.

  > [!NOTE]
  > Składnik <xref:System.Windows.Forms.BindingSource> kopiuje wszystkie elementy <xref:System.Collections.IEnumerable> do osobnej listy w celu powiązania.

- Interfejs <xref:System.ComponentModel.ITypedList>

  Klasa kolekcji implementująca interfejs <xref:System.ComponentModel.ITypedList> zapewnia możliwość sterowania kolejnością i zestawem właściwości dostępnych dla kontrolki powiązanej.

  > [!NOTE]
  > Podczas implementowania metody <xref:System.ComponentModel.ITypedList.GetItemProperties%2A>, a tablica <xref:System.ComponentModel.PropertyDescriptor>a nie ma wartości null, ostatni wpis w tablicy będzie deskryptorem właściwości opisującym Właściwość list, która jest kolejną listą elementów.

- Interfejs <xref:System.ComponentModel.ICustomTypeDescriptor>

  Klasa implementująca interfejs <xref:System.ComponentModel.ICustomTypeDescriptor> zapewnia dynamiczne informacje o sobie. Ten interfejs jest podobny do <xref:System.ComponentModel.ITypedList>, ale jest używany dla obiektów, a nie na listach. Ten interfejs jest używany przez <xref:System.Data.DataRowView>, aby zaprojektować schemat wierszy bazowych. Prosta implementacja <xref:System.ComponentModel.ICustomTypeDescriptor> jest udostępniana przez klasę <xref:System.ComponentModel.CustomTypeDescriptor>.

  > [!NOTE]
  > Aby obsługiwać powiązania czasu projektowania z typami, które implementują <xref:System.ComponentModel.ICustomTypeDescriptor>, typ musi również implementować <xref:System.ComponentModel.IComponent> i istnieć jako wystąpienie w formularzu.

- Interfejs <xref:System.ComponentModel.IListSource>

  Klasa implementująca interfejs <xref:System.ComponentModel.IListSource> włącza powiązanie oparte na liście dla obiektów niebędących listami. Metoda <xref:System.ComponentModel.IListSource.GetList%2A> <xref:System.ComponentModel.IListSource> służy do zwracania listy możliwej do powiązania z obiektu, który nie dziedziczy po <xref:System.Collections.IList>. <xref:System.ComponentModel.IListSource> jest używana przez klasę <xref:System.Data.DataSet>.

- Interfejs <xref:System.ComponentModel.IRaiseItemChangedEvents>

  Klasa implementująca interfejs <xref:System.ComponentModel.IRaiseItemChangedEvents> jest listą z powiązaniem, która implementuje także interfejs <xref:System.ComponentModel.IBindingList>. Ten interfejs służy do wskazywania, czy typ generuje zdarzenia <xref:System.ComponentModel.IBindingList.ListChanged> typu <xref:System.ComponentModel.ListChangedType.ItemChanged> za poorednictwem jego właściwości <xref:System.ComponentModel.IRaiseItemChangedEvents.RaisesItemChangedEvents%2A>.

  > [!NOTE]
  > Należy zaimplementować <xref:System.ComponentModel.IRaiseItemChangedEvents>, jeśli źródło danych udostępnia właściwość, aby można było wyświetlić listę opisanej wcześniej konwersji zdarzeń i działa ze składnikiem <xref:System.Windows.Forms.BindingSource>. W przeciwnym razie <xref:System.Windows.Forms.BindingSource> wykona również właściwość, aby wyświetlić listę zdarzeń, co powoduje wolniejszą wydajność.

- Interfejs <xref:System.ComponentModel.ISupportInitialize>

  Składnik implementujący interfejs <xref:System.ComponentModel.ISupportInitialize> ma zalety optymalizacji partii, aby ustawić właściwości i inicjować właściwości współzależne. <xref:System.ComponentModel.ISupportInitialize> zawiera dwie metody:

  - <xref:System.ComponentModel.ISupportInitialize.BeginInit%2A> sygnalizuje uruchomienie inicjalizacji obiektu.

  - <xref:System.ComponentModel.ISupportInitialize.EndInit%2A> sygnalizuje zakończenie inicjowania obiektu.

- Interfejs <xref:System.ComponentModel.ISupportInitializeNotification>

  Składnik implementujący interfejs <xref:System.ComponentModel.ISupportInitializeNotification> również implementuje interfejs <xref:System.ComponentModel.ISupportInitialize>. Ten interfejs umożliwia powiadomienie innych składników <xref:System.ComponentModel.ISupportInitialize>, które zakończyły się inicjalizacją. Interfejs <xref:System.ComponentModel.ISupportInitializeNotification> zawiera dwóch członków:

  - <xref:System.ComponentModel.ISupportInitializeNotification.IsInitialized%2A> zwraca `boolean` wartość wskazującą, czy składnik jest zainicjowany.

  - <xref:System.ComponentModel.ISupportInitializeNotification.Initialized> występuje, gdy wywoływany jest <xref:System.ComponentModel.ISupportInitialize.EndInit%2A>.

- Interfejs <xref:System.ComponentModel.INotifyPropertyChanged>

  Klasa implementująca ten interfejs jest typem, który wywołuje zdarzenie, gdy dowolna z jego wartości właściwości zostanie zmieniona. Ten interfejs jest przeznaczony do zastępowania wzorca mającego zdarzenie zmiany dla każdej właściwości formantu. W przypadku użycia w <xref:System.ComponentModel.BindingList%601>obiekt biznesowy powinien implementować interfejs <xref:System.ComponentModel.INotifyPropertyChanged>, a BindingList\`1 spowoduje przekonwertowanie zdarzeń <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> na <xref:System.ComponentModel.BindingList%601.ListChanged> zdarzenia typu <xref:System.ComponentModel.ListChangedType.ItemChanged>.

  > [!NOTE]
  > Aby powiadomienie o zmianie miało miejsce w powiązaniu między klientem powiązanym a źródłem danych, dla którego powiązany Typ źródła danych powinien implementować interfejs <xref:System.ComponentModel.INotifyPropertyChanged> (preferowany) lub można dostarczyć zdarzenia *propertyName*`Changed` dla typu powiązanego, ale nie należy wykonywać obu tych czynności.

### <a name="interfaces-for-implementation-by-component-authors"></a>Interfejsy dla implementacji przez autorów składników

Następujące interfejsy zostały zaprojektowane do użytku przez aparat powiązań danych Windows Forms:

- Interfejs <xref:System.Windows.Forms.IBindableComponent>

  Klasa implementująca ten interfejs to składnik niebędący kontrolką, który obsługuje powiązanie danych. Ta klasa zwraca powiązania danych i kontekst powiązania składnika za pomocą właściwości <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> i <xref:System.Windows.Forms.IBindableComponent.BindingContext%2A> tego interfejsu.

  > [!NOTE]
  > Jeśli składnik dziedziczy po <xref:System.Windows.Forms.Control>, nie trzeba implementować interfejsu <xref:System.Windows.Forms.IBindableComponent>.

- Interfejs <xref:System.Windows.Forms.ICurrencyManagerProvider>

  Klasa implementująca interfejs <xref:System.Windows.Forms.ICurrencyManagerProvider> jest składnikiem, który zapewnia własne <xref:System.Windows.Forms.CurrencyManager> do zarządzania powiązaniami skojarzonymi z tym konkretnym składnikiem. Dostęp do <xref:System.Windows.Forms.CurrencyManager> niestandardowego jest udostępniany przez właściwość <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>.

  > [!NOTE]
  > Klasa, która dziedziczy po <xref:System.Windows.Forms.Control> zarządza powiązaniami automatycznie za pośrednictwem właściwości <xref:System.Windows.Forms.Control.BindingContext%2A>, tak więc przypadki, w których należy zaimplementować <xref:System.Windows.Forms.ICurrencyManagerProvider> są dość rzadki.

## <a name="see-also"></a>Zobacz także

- [Wiązanie danych i formularzy Windows Forms](data-binding-and-windows-forms.md)
- [Instrukcje: tworzenie prostej kontrolki powiązanej na formularzu systemu Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Wiązanie danych formularzy Windows Forms](windows-forms-data-binding.md)

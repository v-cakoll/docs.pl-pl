---
title: Architektura składnika BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
ms.openlocfilehash: 54a23ba899ceb05701fe3580aefbb723c6b3f0fd
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364418"
---
# <a name="bindingsource-component-architecture"></a>Architektura składnika BindingSource
Za pomocą <xref:System.Windows.Forms.BindingSource> składnika można uniwersalnie powiązać wszystkie kontrolki Windows Forms ze źródłami danych.  
  
 <xref:System.Windows.Forms.BindingSource> Składnik upraszcza proces powiązań kontroli ze źródłem danych i zapewnia następujące korzyści w porównaniu z tradycyjnym wiązaniem danych:  
  
- Włącza powiązanie czasu projektowania z obiektami biznesowymi.  
  
- <xref:System.Windows.Forms.CurrencyManager> Hermetyzuje <xref:System.Windows.Forms.CurrencyManager> funkcjonalność i uwidacznia zdarzenia w czasie projektowania.  
  
- Upraszcza tworzenie listy, która obsługuje <xref:System.ComponentModel.IBindingList> interfejs, dostarczając powiadomienie o zmianie listy dla źródeł danych, które nie obsługują natywnie powiadomienia o zmianie listy.  
  
- Udostępnia punkt rozszerzalności dla <xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType> metody.  
  
- Zapewnia poziom pośredni między źródłem danych i kontrolką. Ten operator pośredni jest ważny, gdy źródło danych może ulec zmianie w czasie wykonywania.  
  
- Współdziała z innymi kontrolkami Windows Forms związanymi z danymi, <xref:System.Windows.Forms.BindingNavigator> w tym <xref:System.Windows.Forms.DataGridView> formantami i.  
  
 Z tego względu <xref:System.Windows.Forms.BindingSource> składnik jest preferowanym sposobem powiązania formantów Windows Forms ze źródłami danych.  
  
## <a name="bindingsource-features"></a>BindingSource — funkcje  
 <xref:System.Windows.Forms.BindingSource> Składnik udostępnia kilka funkcji powiązania kontroli z danymi. Korzystając z tych funkcji, można zaimplementować większość scenariuszy związanych z danymi, dzięki czemu nie ma już możliwości kodowania.  
  
 <xref:System.Windows.Forms.BindingSource> Składnik osiąga ten sposób, zapewniając spójny interfejs do uzyskiwania dostępu do wielu różnych rodzajów źródeł danych. Oznacza to, że należy użyć tej samej procedury dla powiązania z dowolnym typem. Na przykład możesz dołączyć <xref:System.Windows.Forms.BindingSource.DataSource%2A> Właściwość <xref:System.Data.DataSet> do obiektu biznesowego i w obu przypadkach używasz tego samego zestawu właściwości, metod i zdarzeń, aby manipulować źródłem danych.  
  
 Spójny interfejs zapewniany przez <xref:System.Windows.Forms.BindingSource> składnik znacznie upraszcza proces powiązań danych z kontrolkami. W przypadku typów źródeł danych, które udostępniają powiadomienia o <xref:System.Windows.Forms.BindingSource> zmianie, składnik automatycznie komunikuje się ze zmianami między kontrolką a źródłem danych. W przypadku typów źródeł danych, które nie udostępniają powiadomienia o zmianach, udostępniane są zdarzenia, które umożliwiają zgłaszanie powiadomień o zmianach. Na poniższej liście przedstawiono funkcje obsługiwane przez <xref:System.Windows.Forms.BindingSource> składnik:  
  
- Pośredni.  
  
- Zarządzanie walutą.  
  
- Źródło danych jako listę.  
  
- <xref:System.Windows.Forms.BindingSource><xref:System.ComponentModel.IBindingList>jako.  
  
- Tworzenie elementów niestandardowych.  
  
- Tworzenie elementów transakcyjnych.  
  
- <xref:System.Collections.IEnumerable>pomocy.  
  
- Obsługa czasu projektowania.  
  
- Metody <xref:System.Windows.Forms.ListBindingHelper> statyczne.  
  
- Sortowanie i filtrowanie za pomocą <xref:System.ComponentModel.IBindingListView> interfejsu.  
  
- Integracja z <xref:System.Windows.Forms.BindingNavigator>programem.  
  
### <a name="indirection"></a>Pośredniość  
 <xref:System.Windows.Forms.BindingSource> Składnik zapewnia poziom pośredni między kontrolką a źródłem danych. Zamiast bezpośrednio powiązać formant ze źródłem danych, należy powiązać formant z <xref:System.Windows.Forms.BindingSource>i dołączyć źródło danych <xref:System.Windows.Forms.BindingSource> do <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości składnika.  
  
 Za pomocą tego poziomu pośredniego można zmienić źródło danych bez resetowania powiązania kontrolki. Zapewnia to następujące możliwości:  
  
- Można dołączyć <xref:System.Windows.Forms.BindingSource> do różnych źródeł danych, zachowując bieżące powiązania kontroli.  
  
- Można zmienić elementy w źródle danych i kontrolować powiązane kontrolki. Aby uzyskać więcej informacji, zobacz [jak: Odzwierciedlanie aktualizacji źródła danych w kontrolce Windows Forms z elementem](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)BindingSource.  
  
- W pamięci można powiązać <xref:System.Type> obiekt zamiast obiektu. Aby uzyskać więcej informacji, zobacz [jak: Powiąż formant Windows Forms z typem](how-to-bind-a-windows-forms-control-to-a-type.md). Następnie można powiązać z obiektem w czasie wykonywania.  
  
### <a name="currency-management"></a>Zarządzanie walutą  
 <xref:System.Windows.Forms.BindingSource> Składnik<xref:System.Windows.Forms.ICurrencyManagerProvider> implementuje interfejs obsługujący zarządzanie walutą. Za pomocą <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource.DataMember%2A>interfejsu można także uzyskać dostęp do Menedżera waluty dla a, oprócz Menedżera waluty dla innego powiązania z tym samym. <xref:System.Windows.Forms.ICurrencyManagerProvider>  
  
 Składnik hermetyzuje funkcje i uwidacznia najbardziej typowe <xref:System.Windows.Forms.CurrencyManager> właściwości i zdarzenia. <xref:System.Windows.Forms.CurrencyManager> <xref:System.Windows.Forms.BindingSource> W poniższej tabeli opisano niektóre elementy członkowskie związane z zarządzaniem walutą.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>wartość  
 Pobiera Menedżera waluty skojarzone z <xref:System.Windows.Forms.BindingSource>.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A>Method  
 Jeśli istnieje inny <xref:System.Windows.Forms.BindingSource> powiązany z określonym elementem członkowskim danych, pobiera jego Menedżera waluty.  
  
 <xref:System.Windows.Forms.BindingSource.Current%2A>wartość  
 Pobiera bieżący element źródła danych.  
  
 <xref:System.Windows.Forms.BindingSource.Position%2A>wartość  
 Pobiera lub ustawia bieżącą pozycję na liście podstawowej.  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A>Method  
 Stosuje oczekujące zmiany do bazowego źródła danych.  
  
 <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>Method  
 Anuluje bieżącą operację edycji.  
  
### <a name="data-source-as-a-list"></a>Źródło danych jako listę  
 Składnik implementuje interfejsy<xref:System.ComponentModel.ITypedList> i <xref:System.ComponentModel.IBindingListView>. <xref:System.Windows.Forms.BindingSource> W tej implementacji można używać <xref:System.Windows.Forms.BindingSource> samego składnika jako źródła danych, bez żadnego magazynu zewnętrznego.  
  
 <xref:System.Windows.Forms.BindingSource> Gdy składnik jest dołączony do źródła danych, udostępnia źródło danych jako listę.  
  
 <xref:System.Windows.Forms.BindingSource.DataSource%2A> Właściwość można ustawić na kilka źródeł danych. Obejmują one typy, obiekty i listy typów. Utworzone źródło danych zostanie uwidocznione jako lista. W poniższej tabeli przedstawiono niektóre typowe źródła danych i ocenę listy wyników.  
  
|DataSource — właściwość|Wyświetl wyniki|  
|-------------------------|------------------|  
|Odwołanie o wartości null`Nothing` (w Visual Basic)|Puste <xref:System.ComponentModel.IBindingList> obiekty. Dodanie elementu ustawia listę na typ dodanego elementu.|  
|Odwołanie o wartości null`Nothing` (w Visual Basic) <xref:System.Windows.Forms.BindingSource.DataMember%2A> z zestawem|Nieobsługiwane; podnosi <xref:System.ArgumentException>.|  
|Typ bez listy lub obiekt typu "T"|Pusty <xref:System.ComponentModel.IBindingList> typ "T".|  
|Wystąpienie tablicy|<xref:System.ComponentModel.IBindingList> Zawierający elementy tablicy.|  
|<xref:System.Collections.IEnumerable>np|<xref:System.ComponentModel.IBindingList> Zawierający elementy<xref:System.Collections.IEnumerable>|  
|Wystąpienie listy zawierające typ "T"|<xref:System.ComponentModel.IBindingList> Wystąpienie zawierające typ "T".|  
  
 Ponadto można ustawić inne typy list, takie jak <xref:System.ComponentModel.IListSource> i <xref:System.ComponentModel.ITypedList>, a także <xref:System.Windows.Forms.BindingSource> je odpowiednio obsłużyć. <xref:System.Windows.Forms.BindingSource.DataSource%2A> W takim przypadku Typ zawarty na liście powinien mieć konstruktora bez parametrów.  
  
### <a name="bindingsource-as-an-ibindinglist"></a>Źródło BindingSource jako element IBindingList  
 Składnik <xref:System.Windows.Forms.BindingSource> ten zawiera elementy członkowskie do uzyskiwania dostępu do danych <xref:System.ComponentModel.IBindingList>źródłowych i manipulowania nimi. W poniższej tabeli opisano niektóre z tych elementów członkowskich.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.List%2A>wartość|Pobiera listę będącą wynikiem oceny <xref:System.Windows.Forms.BindingSource.DataSource%2A> lub <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwości.|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A>Method|Dodaje nowy element do listy podstawowej. Dotyczy źródeł danych, które implementują <xref:System.ComponentModel.IBindingList> interfejs i zezwalają na dodawanie elementów (oznacza to <xref:System.Windows.Forms.BindingSource.AllowNew%2A> , że właściwość jest `true`ustawiona na).|  
  
### <a name="custom-item-creation"></a>Tworzenie elementów niestandardowych  
 Możesz obsłużyć <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzenie, aby zapewnić własną logikę tworzenia elementów. Zdarzenie występuje przed dodaniem nowego obiektu <xref:System.Windows.Forms.BindingSource>do elementu. <xref:System.Windows.Forms.BindingSource.AddingNew> To zdarzenie jest wywoływane po <xref:System.Windows.Forms.BindingSource.AddNew%2A> wywołaniu metody, ale przed dodaniem nowego elementu do listy podstawowej. Dzięki obsłudze tego zdarzenia możesz zapewnić zachowanie tworzenia elementów niestandardowych bez wyznaczania z <xref:System.Windows.Forms.BindingSource> klasy. Aby uzyskać więcej informacji, zobacz [jak: Dostosuj Dodawanie elementów za pomocą elementu BindingSource](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)Windows Forms.  
  
### <a name="transactional-item-creation"></a>Tworzenie elementów transakcyjnych  
 <xref:System.Windows.Forms.BindingSource> Składnik<xref:System.ComponentModel.ICancelAddNew> implementuje interfejs, który umożliwia tworzenie elementów transakcyjnych. Po tymczasowym utworzeniu nowego elementu przy użyciu wywołania do <xref:System.Windows.Forms.BindingSource.AddNew%2A>, dodanie może zostać zatwierdzone lub wycofane w następujący sposób:  
  
- <xref:System.ComponentModel.ICancelAddNew.EndNew%2A> Metoda jawnie zatwierdzi oczekujące dodanie.  
  
- Wykonanie innej operacji kolekcji, takiej jak wstawianie, usuwanie lub przenoszenie, spowoduje niejawne zatwierdzenie oczekującego dodania.  
  
- <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A> Metoda zostanie wycofana jako oczekujące dodanie, jeśli metoda nie została jeszcze zatwierdzona.  
  
### <a name="ienumerable-support"></a>Obsługa interfejsu IEnumerable  
 Składnik umożliwia kontrolowanie powiązań ze <xref:System.Collections.IEnumerable> źródłami danych. <xref:System.Windows.Forms.BindingSource> Za pomocą tego składnika można powiązać ze źródłem danych, takim jak <xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>.  
  
 <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource> <xref:System.Collections.IEnumerable> Gdy źródło danych jest przypisane do<xref:System.ComponentModel.IBindingList> składnika, program tworzy i dodaje zawartość źródła danych do listy. <xref:System.Collections.IEnumerable>  
  
### <a name="design-time-support"></a>Obsługa czasu projektowania  
 Niektórych typów obiektów nie można tworzyć w czasie projektowania, takich jak obiekty utworzone na podstawie klasy fabryki lub obiekty zwracane przez usługę sieci Web. Czasami może być konieczne powiązanie kontrolek z tymi typami w czasie projektowania, nawet jeśli w pamięci nie ma obiektu, do którego można powiązać formanty. Może na przykład być konieczne etykietowanie nagłówków <xref:System.Windows.Forms.DataGridView> kolumn formantu z nazwami właściwości publicznych typu niestandardowego.  
  
 Aby można było obsługiwać ten scenariusz <xref:System.Windows.Forms.BindingSource> , składnik obsługuje powiązanie <xref:System.Type>z. Gdy przypiszesz <xref:System.Type> <xref:System.Windows.Forms.BindingSource.DataSource%2A> do właściwości, <xref:System.Windows.Forms.BindingSource> składnik tworzy puste <xref:System.ComponentModel.BindingList%601> <xref:System.Type> elementy. Wszystkie kontrolki, które następnie zostaną <xref:System.Windows.Forms.BindingSource> powiązane ze składnikiem, będą otrzymywać alerty o obecności właściwości lub schematu typu w czasie projektowania lub w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [jak: Powiąż formant Windows Forms z typem](how-to-bind-a-windows-forms-control-to-a-type.md).  
  
### <a name="static-listbindinghelper-methods"></a>Statyczne metody ListBindingHelper  
 <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType>, ,I<xref:System.Windows.Forms.BindingSource> wszystkie typy `DataSource` wspólnychlogikiudostępnianiadogenerowania`DataMember` listy z pary./ <xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType> Ponadto ta wspólna logika jest publicznie narażona na używanie przez autorów kontroli i innych podmiotów trzecich w następujących `static` metodach:  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>.  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>Sortowanie i filtrowanie za pomocą interfejsu IBindingListView  
 <xref:System.Windows.Forms.BindingSource> Składnik implementuje<xref:System.ComponentModel.IBindingList> interfejs, który rozszerza interfejs. <xref:System.ComponentModel.IBindingListView> Sortuje pojedyncze kolumny <xref:System.ComponentModel.IBindingListView> i oferują zaawansowane sortowanie i filtrowanie. <xref:System.ComponentModel.IBindingList> W <xref:System.ComponentModel.IBindingListView>programie można sortować i filtrować elementy w źródle danych, jeśli źródło danych również implementuje jeden z tych interfejsów. <xref:System.Windows.Forms.BindingSource> Składnik nie dostarcza implementacji referencyjnej tych elementów członkowskich. Zamiast tego wywołania są przekazywane do listy podstawowej.  
  
 W poniższej tabeli opisano właściwości używane do sortowania i filtrowania.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A>wartość|Jeśli źródło danych jest <xref:System.ComponentModel.IBindingListView>, Pobiera lub ustawia wyrażenie używane do filtrowania wierszy, które są wyświetlane.|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A>wartość|Jeśli źródło danych to <xref:System.ComponentModel.IBindingList>, Pobiera lub ustawia nazwę kolumny służącą do sortowania i sortowania informacji.<br /><br /> —lub—<br /><br /> Jeśli źródło danych jest obsługiwane przez <xref:System.ComponentModel.IBindingListView> funkcję sortowania zaawansowanego, pobiera wiele nazw kolumn używanych w celu sortowania i sortowania|  
  
### <a name="integration-with-bindingnavigator"></a>Integracja z parametrem BindingNavigator  
 Można użyć składnika, <xref:System.Windows.Forms.BindingSource> aby powiązać dowolny formant Windows Forms ze źródłem danych, <xref:System.Windows.Forms.BindingNavigator> ale formant jest zaprojektowany <xref:System.Windows.Forms.BindingSource> specjalnie do pracy ze składnikiem. Formant udostępnia interfejs użytkownika służący do <xref:System.Windows.Forms.BindingSource> kontrolowania bieżącego elementu składnika. <xref:System.Windows.Forms.BindingNavigator> Domyślnie <xref:System.Windows.Forms.BindingNavigator> kontrolka udostępnia przyciski odpowiadające metodom nawigacji <xref:System.Windows.Forms.BindingSource> w składniku. Aby uzyskać więcej informacji, zobacz [jak: Przejdź do danych za pomocą kontrolki](how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md)Windows Forms BindingNavigator.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [BindingSource, składnik — omówienie](bindingsource-component-overview.md)
- [BindingNavigator, kontrolka](bindingnavigator-control-windows-forms.md)
- [Wiązanie danych formularzy Windows Forms](../windows-forms-data-binding.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
- [Instrukcje: Powiąż formant Windows Forms z typem](how-to-bind-a-windows-forms-control-to-a-type.md)
- [Instrukcje: Odzwierciedlanie aktualizacji źródła danych w kontrolce Windows Forms za pomocą elementu BindingSource](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)

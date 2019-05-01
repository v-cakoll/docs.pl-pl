---
title: Architektura składnika BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
ms.openlocfilehash: 81559444b6e3da2861e48bdc637ae01d246c0758
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961580"
---
# <a name="bindingsource-component-architecture"></a>Architektura składnika BindingSource
Za pomocą <xref:System.Windows.Forms.BindingSource> składnika wszystkie kontrolki Windows Forms można powiązać powszechnie dla źródła danych.  
  
 <xref:System.Windows.Forms.BindingSource> Składnik upraszcza proces powiązywanie kontrolek ze źródłem danych i zapewnia następujące korzyści za pośrednictwem powiązania danych tradycyjny:  
  
- Umożliwia powiązanie obiektów biznesowych czasu projektowania.  
  
- Hermetyzuje <xref:System.Windows.Forms.CurrencyManager> funkcjonalność i ujawnia <xref:System.Windows.Forms.CurrencyManager> zdarzeń w czasie projektowania.  
  
- Upraszcza tworzenie listy, która obsługuje <xref:System.ComponentModel.IBindingList> interfejs, dostarczając listy powiadomienia o zmianie dla źródeł danych, które nie obsługują natywnie listy powiadomienie o zmianie.  
  
- Udostępnia punkt rozszerzalności dla <xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType> metody.  
  
- Zapewnia poziom pośredni między źródłem danych i kontrolki. Tego operatora pośredniego jest ważne, gdy źródło danych mogą ulec zmianie w czasie wykonywania.  
  
- Współdziała z innymi formantami związanych z danymi formularze Windows specjalnie <xref:System.Windows.Forms.BindingNavigator> i <xref:System.Windows.Forms.DataGridView> kontrolki.  
  
 Z tego względu <xref:System.Windows.Forms.BindingSource> składnik jest preferowanym sposobem powiązanie formantów Windows Forms ze źródłami danych.  
  
## <a name="bindingsource-features"></a>BindingSource — funkcje  
 <xref:System.Windows.Forms.BindingSource> Składnik udostępnia kilka funkcji dla powiązywanie kontrolek z danymi. Te funkcje można zaimplementować większości scenariuszy wiązania z danymi niemal bez pisania kodu ze strony użytkownika.  
  
 <xref:System.Windows.Forms.BindingSource> Składnik to w ramach, zapewniając spójny interfejs do uzyskiwania dostępu do wielu różnych rodzajów źródeł danych. Oznacza to, użyj tej samej procedury dla powiązania do dowolnego typu. Na przykład, możesz dołączyć <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości <xref:System.Data.DataSet> lub obiektem biznesowym i w obu przypadkach ten sam zestaw właściwości, metody i zdarzenia są używane do manipulowania źródła danych.  
  
 Spójny interfejs dostarczony przez <xref:System.Windows.Forms.BindingSource> składnika znacznie upraszcza proces powiązywanie danych z kontrolkami. Dla typów źródła danych, które zapewniają zmiany powiadomienia, <xref:System.Windows.Forms.BindingSource> składnik automatycznie komunikuje się zmiany między formantem i źródła danych. Dla typów źródła danych, które nie są oferowane powiadomienie o zmianie zdarzenia są dostarczane umożliwiające wywoływanie powiadomień o zmianie. Na poniższej liście przedstawiono funkcje obsługiwane przez <xref:System.Windows.Forms.BindingSource> składników:  
  
- Operatory pośrednie.  
  
- Zarządzanie waluty.  
  
- Źródło danych w postaci listy.  
  
- <xref:System.Windows.Forms.BindingSource> jako <xref:System.ComponentModel.IBindingList>.  
  
- Tworzenie niestandardowego elementu.  
  
- Tworzenie elementu transakcyjnych.  
  
- <xref:System.Collections.IEnumerable> Pomoc techniczna.  
  
- Obsługi w czasie projektowania.  
  
- Statyczne <xref:System.Windows.Forms.ListBindingHelper> metody.  
  
- Sortowanie i filtrowanie przy użyciu <xref:System.ComponentModel.IBindingListView> interfejsu.  
  
- Integracja z usługą <xref:System.Windows.Forms.BindingNavigator>.  
  
### <a name="indirection"></a>Pośredniość  
 <xref:System.Windows.Forms.BindingSource> Składnik zapewnia poziom pośredni między formantem źródłem danych. Zamiast formant bezpośrednio ze źródłem danych, możesz powiązać formant <xref:System.Windows.Forms.BindingSource>, i Dołącz źródła danych, aby <xref:System.Windows.Forms.BindingSource> składnika <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości.  
  
 Z tego poziomu pośredniego źródła danych można zmienić bez resetowania powiązania kontrolki. Zapewnia następujące możliwości:  
  
- Możesz dołączyć <xref:System.Windows.Forms.BindingSource> do różnych źródeł danych przy zachowaniu bieżącego powiązania kontroli.  
  
- Można zmienić elementów w źródle danych i powiadom formanty powiązane. Aby uzyskać więcej informacji, zobacz [jak: Odzwierciedlanie aktualizacji źródła danych w kontrolce Windows Forms przy użyciu kontrolki BindingSource](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md).  
  
- Możesz powiązać <xref:System.Type> zamiast obiektu w pamięci. Aby uzyskać więcej informacji, zobacz [jak: Powiązywanie formantu Windows Forms z typem](how-to-bind-a-windows-forms-control-to-a-type.md). Następnie możesz powiązać z obiektem w czasie wykonywania.  
  
### <a name="currency-management"></a>Zarządzanie waluty  
 <xref:System.Windows.Forms.BindingSource> Wdrażane <xref:System.Windows.Forms.ICurrencyManagerProvider> interfejsu do obsługi zarządzania waluty dla Ciebie. Za pomocą <xref:System.Windows.Forms.ICurrencyManagerProvider> interfejsu, można również przejść do menedżera waluty <xref:System.Windows.Forms.BindingSource>, oprócz menedżera waluty dla innego <xref:System.Windows.Forms.BindingSource> powiązany do tej samej <xref:System.Windows.Forms.BindingSource.DataMember%2A>.  
  
 <xref:System.Windows.Forms.BindingSource> Hermetyzuje składnika <xref:System.Windows.Forms.CurrencyManager> funkcjonalność i udostępnia najbardziej typowe <xref:System.Windows.Forms.CurrencyManager> właściwości i zdarzenia. W poniższej tabeli opisano niektóre elementy członkowskie powiązane z zarządzaniem waluty.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> Właściwość  
 Pobiera menedżera waluty skojarzonego z <xref:System.Windows.Forms.BindingSource>.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A> — Metoda  
 W przypadku innego <xref:System.Windows.Forms.BindingSource> powiązany element członkowski danych określona, pobiera jego menedżera waluty.  
  
 <xref:System.Windows.Forms.BindingSource.Current%2A> Właściwość  
 Pobiera bieżący element źródła danych.  
  
 <xref:System.Windows.Forms.BindingSource.Position%2A> Właściwość  
 Pobiera lub ustawia bieżącą pozycję na liście podstawowej.  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> — Metoda  
 Ma zastosowanie oczekujących zmian do bazowego źródła danych.  
  
 <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> — Metoda  
 Anuluje bieżącą operację edycji.  
  
### <a name="data-source-as-a-list"></a>Źródło danych w postaci listy  
 <xref:System.Windows.Forms.BindingSource> Wdrażane <xref:System.ComponentModel.IBindingListView> i <xref:System.ComponentModel.ITypedList> interfejsów. W tej implementacji, możesz użyć <xref:System.Windows.Forms.BindingSource> sam składnik jako źródła danych bez żadnych magazynu zewnętrznego.  
  
 Gdy <xref:System.Windows.Forms.BindingSource> składnik jest podłączony do źródła danych, udostępnia źródło danych w postaci listy.  
  
 <xref:System.Windows.Forms.BindingSource.DataSource%2A> Właściwość można ustawić kilka źródeł danych. Obejmują one typy, obiekty i listy typów. Wynikowy źródło danych będzie widoczne jako listę. W poniższej tabeli przedstawiono niektóre typowe źródła danych i wynikowy oceny listy.  
  
|Wartość właściwości DataSource|Listy wyników|  
|-------------------------|------------------|  
|Odwołanie o wartości null (`Nothing` w języku Visual Basic)|Pusta <xref:System.ComponentModel.IBindingList> obiektów. Dodanie elementu umożliwia określenie listy Typ dodanego elementu.|  
|Odwołanie o wartości null (`Nothing` w języku Visual Basic) z <xref:System.Windows.Forms.BindingSource.DataMember%2A> zestawu|Nieobsługiwane. wywołuje <xref:System.ArgumentException>.|  
|Typ spoza listy lub obiektu typu "T"|Pusta <xref:System.ComponentModel.IBindingList> typu "T".|  
|Wystąpienie tablicy|<xref:System.ComponentModel.IBindingList> Zawierający elementy tablicy.|  
|<xref:System.Collections.IEnumerable> wystąpienia|<xref:System.ComponentModel.IBindingList> Zawierający <xref:System.Collections.IEnumerable> elementów|  
|Lista wystąpień z typem "T"|<xref:System.ComponentModel.IBindingList> Wystąpienia typu "T".|  
  
 Ponadto <xref:System.Windows.Forms.BindingSource.DataSource%2A> można ustawić do innych typów list, takich jak <xref:System.ComponentModel.IListSource> i <xref:System.ComponentModel.ITypedList>i <xref:System.Windows.Forms.BindingSource> odpowiednio je będzie obsługiwać. W tym przypadku typ, który znajduje się na liście powinien mieć domyślnego konstruktora.  
  
### <a name="bindingsource-as-an-ibindinglist"></a>BindingSource — jako IBindingList  
 <xref:System.Windows.Forms.BindingSource> Składnika oferuje elementy członkowskie do uzyskiwania dostępu i manipulowania danych bazowych jako <xref:System.ComponentModel.IBindingList>. W poniższej tabeli opisano niektóre z tych elementów członkowskich.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.List%2A> Właściwość|Pobiera listę, która wynika z oceny <xref:System.Windows.Forms.BindingSource.DataSource%2A> lub <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwości.|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A> — Metoda|Dodaje nowy element do listy źródłowej. Stosuje się do źródeł danych, które implementują <xref:System.ComponentModel.IBindingList> interfejs i Zezwalaj na dodawanie elementów (czyli <xref:System.Windows.Forms.BindingSource.AllowNew%2A> właściwość jest ustawiona na `true`).|  
  
### <a name="custom-item-creation"></a>Tworzenie niestandardowego elementu  
 Może obsługiwać <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzenie, aby zapewnić logikę Tworzenie elementu. <xref:System.Windows.Forms.BindingSource.AddingNew> Wystąpi zdarzenie, przed dodaniem nowego obiektu do <xref:System.Windows.Forms.BindingSource>. To zdarzenie jest wywoływane po wykonaniu <xref:System.Windows.Forms.BindingSource.AddNew%2A> wywoływana jest metoda, ale zanim nowy element zostanie dodany do listy źródłowej. Dzięki obsłudze to zdarzenie, może zapewnić zachowanie tworzenia niestandardowego elementu bez pochodząca od <xref:System.Windows.Forms.BindingSource> klasy. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie dodawania elementu przy użyciu kontrolki BindingSource formularzy Windows](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md).  
  
### <a name="transactional-item-creation"></a>Tworzenie elementu transakcyjne  
 <xref:System.Windows.Forms.BindingSource> Wdrażane <xref:System.ComponentModel.ICancelAddNew> interfejs, który umożliwia utworzenie elementu transakcyjnych. Tymczasowo utworzony nowy element za pomocą wywołania <xref:System.Windows.Forms.BindingSource.AddNew%2A>, dodanie może zostać przekazana lub wycofana w następujący sposób:  
  
- <xref:System.ComponentModel.ICancelAddNew.EndNew%2A> Metoda oczekującego dodania jawnie spowoduje to zatwierdzenie.  
  
- Wykonywanie innej operacji kolekcji, takich jak wstawianie, usuwanie lub Przenieś, niejawnie zatwierdzić oczekującego dodania.  
  
- <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A> Metoda wycofa oczekującego dodania Jeśli metoda nie została jeszcze zatwierdzona.  
  
### <a name="ienumerable-support"></a>Obsługa interfejsu IEnumerable  
 <xref:System.Windows.Forms.BindingSource> Składnik umożliwia powiązanie kontrolek do <xref:System.Collections.IEnumerable> źródeł danych. Za pomocą tego składnika można powiązać ze źródłem danych takich jak <xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>.  
  
 Gdy <xref:System.Collections.IEnumerable> źródło danych jest przypisane do <xref:System.Windows.Forms.BindingSource> składnika <xref:System.Windows.Forms.BindingSource> tworzy <xref:System.ComponentModel.IBindingList> i dodaje zawartość <xref:System.Collections.IEnumerable> źródła danych na liście.  
  
### <a name="design-time-support"></a>Pomoc techniczna czasu projektowania  
 Nie można utworzyć niektórych typów obiektów w czasie projektowania, takich jak obiekty utworzone na podstawie klasę fabryki lub obiektów zwróconych przez usługę sieci Web. Czasami może być konieczne powiązanie formantów do tych typów w czasie projektowania, nawet jeśli nie ma obiektu w pamięci, do którego można powiązać kontrolki. Na przykład, konieczne może być domyślnie nagłówkami kolumn o <xref:System.Windows.Forms.DataGridView> kontrolki z nazwami właściwości publiczne typu niestandardowego.  
  
 Aby obsługiwać ten scenariusz <xref:System.Windows.Forms.BindingSource> składnik obsługuje wiązania <xref:System.Type>. Po przypisaniu <xref:System.Type> do <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości <xref:System.Windows.Forms.BindingSource> składnik tworzy pustą <xref:System.ComponentModel.BindingList%601> z <xref:System.Type> elementów. Następnie powiązać formanty <xref:System.Windows.Forms.BindingSource> składnika będą przedstawiane alerty na obecność właściwości lub schemat tego typu w czasie projektowania lub w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [jak: Powiązywanie formantu Windows Forms z typem](how-to-bind-a-windows-forms-control-to-a-type.md).  
  
### <a name="static-listbindinghelper-methods"></a>Metody statyczne ListBindingHelper  
 <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType>, <xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType>, I <xref:System.Windows.Forms.BindingSource> typy całą logikę wspólnej udziału do generowania listy z `DataSource` / `DataMember` pary. Ponadto typowe logika jest publicznie udostępniane do użycia przez autorów kontroli i osoby trzecie w następującym `static` metody:  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>.  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>Sortowanie i filtrowanie przy użyciu IBindingListView — interfejs  
 <xref:System.Windows.Forms.BindingSource> Wdrażane <xref:System.ComponentModel.IBindingListView> interfejs, który rozszerza <xref:System.ComponentModel.IBindingList> interfejsu. <xref:System.ComponentModel.IBindingList> Oferuje pojedynczą kolumnę sortowania i <xref:System.ComponentModel.IBindingListView> oferuje zaawansowane filtrowanie i sortowanie. Za pomocą <xref:System.ComponentModel.IBindingListView>, można sortować i filtrować elementy w źródle danych, jeśli źródło danych również implementuje jedną z tych interfejsów. <xref:System.Windows.Forms.BindingSource> Składnika nie zapewnia referencyjnej implementacji tych elementów członkowskich. Zamiast tego wywołania są przekazywane do listy źródłowej.  
  
 W poniższej tabeli opisano właściwości używanych w przypadku sortowania i filtrowania.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A> Właściwość|Jeśli źródło danych jest <xref:System.ComponentModel.IBindingListView>, pobiera lub ustawia wyrażenie używane do filtrowania, które wiersze są wyświetlane.|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A> Właściwość|Jeśli źródło danych jest <xref:System.ComponentModel.IBindingList>, pobiera lub ustawia nazwę kolumny, używane do sortowania i informacje o kolejności sortowania.<br /><br /> —lub—<br /><br /> Jeśli źródło danych jest <xref:System.ComponentModel.IBindingListView> i obsługuje zaawansowane, sortowanie, pobiera wiele nazw kolumn, używane do sortowania i porządek sortowania|  
  
### <a name="integration-with-bindingnavigator"></a>Integracja z usługą BindingNavigator  
 Możesz użyć <xref:System.Windows.Forms.BindingSource> składnika, aby powiązać dowolnej kontrolki Windows Forms ze źródłem danych, ale <xref:System.Windows.Forms.BindingNavigator> kontroli jest zaprojektowany specjalnie w celu pracy z <xref:System.Windows.Forms.BindingSource> składnika. <xref:System.Windows.Forms.BindingNavigator> Kontroli udostępnia interfejs użytkownika do kontrolowania <xref:System.Windows.Forms.BindingSource> składnika bieżącego elementu. Domyślnie <xref:System.Windows.Forms.BindingNavigator> control oferuje przycisków, które odnoszą się do metod nawigacji <xref:System.Windows.Forms.BindingSource> składnika. Aby uzyskać więcej informacji, zobacz [jak: Nawigowanie po danych za pomocą kontrolki BindingNavigator formularzy Windows](how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [BindingSource, składnik — omówienie](bindingsource-component-overview.md)
- [BindingNavigator, kontrolka](bindingnavigator-control-windows-forms.md)
- [Wiązanie danych formularzy Windows Forms](../windows-forms-data-binding.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
- [Instrukcje: Powiązanie z typem formantu Windows Forms](how-to-bind-a-windows-forms-control-to-a-type.md)
- [Instrukcje: Odzwierciedlanie aktualizacji źródła danych w kontrolce Windows Forms przy użyciu kontrolki BindingSource](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)

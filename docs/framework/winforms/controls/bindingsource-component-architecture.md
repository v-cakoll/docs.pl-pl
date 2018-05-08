---
title: Architektura składnika BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
ms.openlocfilehash: b0334bd7a0bc5ff46c43fd7ee549422d98c35efe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="bindingsource-component-architecture"></a>Architektura składnika BindingSource
Z <xref:System.Windows.Forms.BindingSource> składnika, wszystkie formanty formularzy systemu Windows można powiązać powszechnie dla źródeł danych.  
  
 <xref:System.Windows.Forms.BindingSource> Składnika upraszcza proces powiązanie formantów ze źródłem danych i ma następujące zalety przez powiązanie tradycyjnych danych:  
  
-   Umożliwia powiązanie obiektów biznesowych czasu projektowania.  
  
-   Hermetyzuje <xref:System.Windows.Forms.CurrencyManager> funkcjonalność i ujawnia <xref:System.Windows.Forms.CurrencyManager> zdarzenia w czasie projektowania.  
  
-   Upraszcza tworzenie listy, która obsługuje <xref:System.ComponentModel.IBindingList> interfejs dla źródeł danych, które nie obsługują natywnie listy powiadomienie o zmianie, zapewniając powiadomienia o zmianie listy.  
  
-   Udostępnia punkt rozszerzalności dla <xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType> metody.  
  
-   Zapewnia poziom pośredni między źródłem danych i formantu. Tego operatora pośredniego jest ważne, gdy źródła danych mogą ulec zmianie w czasie wykonywania.  
  
-   Współdziała z innych formantów związanych z danymi formularzy systemu Windows, w szczególności <xref:System.Windows.Forms.BindingNavigator> i <xref:System.Windows.Forms.DataGridView> kontrolki.  
  
 Z tego względu <xref:System.Windows.Forms.BindingSource> składnik jest preferowany sposób powiązanie formantów formularzy systemu Windows ze źródłami danych.  
  
## <a name="bindingsource-features"></a>BindingSource — funkcje  
 <xref:System.Windows.Forms.BindingSource> Składnika zawiera kilka funkcji dla powiązywanie kontrolek z danymi. Z tych funkcji można zaimplementować większości scenariuszy powiązanie danych z prawie nie kodowania ze strony użytkownika.  
  
 <xref:System.Windows.Forms.BindingSource> Składnika w tym celu wprowadza udostępniając spójny interfejs do uzyskiwania dostępu do wielu różnych rodzajów źródeł danych. Oznacza to, użyj procedury tego samego powiązania do dowolnego typu. Na przykład możesz dołączyć <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości <xref:System.Data.DataSet> lub obiektu biznesowego i w obu przypadkach Użyj ten sam zestaw właściwości, metod i zdarzeń do manipulowania źródła danych.  
  
 Spójny interfejs dostarczony przez <xref:System.Windows.Forms.BindingSource> składnika znacząco upraszcza proces wiązanie danych do kontrolek. Typy źródła danych, które zapewniają zmian powiadomień, <xref:System.Windows.Forms.BindingSource> składnika automatycznie komunikuje się zmiany między formantem a źródła danych. Dla typów źródła danych, które nie udostępniają powiadomienia o zmianie zdarzenia są dostarczane umożliwiające wywoływanie powiadomień o zmianie. Poniższa lista zawiera funkcje obsługiwane przez <xref:System.Windows.Forms.BindingSource> składnika:  
  
-   Pośredni.  
  
-   Zarządzanie waluty.  
  
-   Źródło danych w postaci listy.  
  
-   <xref:System.Windows.Forms.BindingSource> jako <xref:System.ComponentModel.IBindingList>.  
  
-   Tworzenie niestandardowego elementu.  
  
-   Tworzenie elementu transakcyjnych.  
  
-   <xref:System.Collections.IEnumerable> Obsługa.  
  
-   Obsługa czasu projektowania.  
  
-   Statyczne <xref:System.Windows.Forms.ListBindingHelper> metody.  
  
-   Sortowanie i filtrowanie z <xref:System.ComponentModel.IBindingListView> interfejsu.  
  
-   Integracja z <xref:System.Windows.Forms.BindingNavigator>.  
  
### <a name="indirection"></a>Pośredniość  
 <xref:System.Windows.Forms.BindingSource> Składnika zapewnia poziom pośredni między formantem a źródłem danych. Zamiast powiązanie formantu bezpośrednio ze źródłem danych, możesz powiązać formant <xref:System.Windows.Forms.BindingSource>, a źródła danych, aby dołączyć <xref:System.Windows.Forms.BindingSource> składnika <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwości.  
  
 Na tym poziomie pośredni można zmienić bez potrzeby resetowania powiązania kontroli źródła danych. Zapewnia następujące możliwości:  
  
-   Możesz dołączyć <xref:System.Windows.Forms.BindingSource> do różnych źródeł danych przy zachowaniu bieżącej powiązania kontroli.  
  
-   Można zmienić elementów w źródle danych i powiadomić formanty powiązane. Aby uzyskać więcej informacji, zobacz [porady: odzwierciedlają aktualizacji źródła danych w formancie formularzy systemu Windows za pomocą elementu BindingSource](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md).  
  
-   Można powiązać <xref:System.Type> zamiast obiektu w pamięci. Aby uzyskać więcej informacji, zobacz [porady: powiązanie formantu formularzy systemu Windows z typem](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md). Następnie możesz powiązać do obiektu w czasie wykonywania.  
  
### <a name="currency-management"></a>Zarządzanie waluty  
 <xref:System.Windows.Forms.BindingSource> Wdrażane <xref:System.Windows.Forms.ICurrencyManagerProvider> interfejsu zarządzania waluty dla Ciebie. Z <xref:System.Windows.Forms.ICurrencyManagerProvider> interfejsu, można także przejść do menedżera waluty dla <xref:System.Windows.Forms.BindingSource>, oprócz menedżera waluty dla drugiego <xref:System.Windows.Forms.BindingSource> powiązany do tej samej <xref:System.Windows.Forms.BindingSource.DataMember%2A>.  
  
 <xref:System.Windows.Forms.BindingSource> Hermetyzuje składnika <xref:System.Windows.Forms.CurrencyManager> funkcjonalność i przedstawia najbardziej typowe <xref:System.Windows.Forms.CurrencyManager> właściwości i zdarzeń. W poniższej tabeli opisano niektóre elementy związane z zarządzaniem waluty.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> Właściwość  
 Pobiera menedżera waluty skojarzonego z <xref:System.Windows.Forms.BindingSource>.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A> — Metoda  
 Jeśli istnieje inny <xref:System.Windows.Forms.BindingSource> powiązana z elementem członkowskim określone dane, pobiera jego menedżera waluty.  
  
 <xref:System.Windows.Forms.BindingSource.Current%2A> Właściwość  
 Pobiera bieżący element źródła danych.  
  
 <xref:System.Windows.Forms.BindingSource.Position%2A> Właściwość  
 Pobiera lub ustawia bieżącą pozycję na liście podstawowej.  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> — Metoda  
 Zastosowanie oczekujących zmian źródła danych.  
  
 <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> — Metoda  
 Umożliwia anulowanie bieżącej operacji edycji.  
  
### <a name="data-source-as-a-list"></a>Źródło danych w postaci listy  
 <xref:System.Windows.Forms.BindingSource> Wdrażane <xref:System.ComponentModel.IBindingListView> i <xref:System.ComponentModel.ITypedList> interfejsów. W tej implementacji, możesz użyć <xref:System.Windows.Forms.BindingSource> sam składnik jako źródła danych, bez żadnych magazynu zewnętrznego.  
  
 Gdy <xref:System.Windows.Forms.BindingSource> składnik jest podłączony do źródła danych, udostępnia ona źródło danych w postaci listy.  
  
 <xref:System.Windows.Forms.BindingSource.DataSource%2A> Do wielu źródeł danych można ustawić właściwości. Obejmują one typy obiektów i listy typów. Wynikowa źródła danych mają być widoczne w postaci listy. W poniższej tabeli przedstawiono niektóre wspólnych źródeł danych i wynikowy oceny listy.  
  
|Właściwości DataSource|Lista wyników|  
|-------------------------|------------------|  
|Odwołanie o wartości null (`Nothing` w języku Visual Basic)|Pusta <xref:System.ComponentModel.IBindingList> obiektów. Dodawanie elementu ustawia listę typowi dodanego elementu.|  
|Odwołanie o wartości null (`Nothing` w języku Visual Basic) z <xref:System.Windows.Forms.BindingSource.DataMember%2A> ustawić|Nieobsługiwane. zgłasza <xref:System.ArgumentException>.|  
|Typ spoza listy lub obiektu typu "T"|Pusta <xref:System.ComponentModel.IBindingList> typu "T".|  
|Wystąpienia tablicy|<xref:System.ComponentModel.IBindingList> Zawierających elementy tablicy.|  
|<xref:System.Collections.IEnumerable> Wystąpienie|<xref:System.ComponentModel.IBindingList> Zawierający <xref:System.Collections.IEnumerable> elementów|  
|Lista wystąpienia typu "T"|<xref:System.ComponentModel.IBindingList> Wystąpienia typu "T".|  
  
 Ponadto <xref:System.Windows.Forms.BindingSource.DataSource%2A> można ustawić na innych typów list, takich jak <xref:System.ComponentModel.IListSource> i <xref:System.ComponentModel.ITypedList>i <xref:System.Windows.Forms.BindingSource> odpowiednio je będzie obsługiwać. W takim przypadku typ, który znajduje się na liście powinien mieć domyślnego konstruktora.  
  
### <a name="bindingsource-as-an-ibindinglist"></a>BindingSource — jako elementu IBindingList  
 <xref:System.Windows.Forms.BindingSource> Składnika zawiera elementy członkowskie do uzyskiwania dostępu do danych i operowanie nimi podstawowej jako <xref:System.ComponentModel.IBindingList>. W poniższej tabeli opisano niektóre z tych elementów członkowskich.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.List%2A> Właściwość|Pobiera listę będącą wynikiem obliczania <xref:System.Windows.Forms.BindingSource.DataSource%2A> lub <xref:System.Windows.Forms.BindingSource.DataMember%2A> właściwości.|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A> — Metoda|Dodaje nowy element do listy źródłowej. Stosuje się do źródła danych, które implementują <xref:System.ComponentModel.IBindingList> interfejsu i Zezwalaj na dodawanie elementów (to znaczy <xref:System.Windows.Forms.BindingSource.AllowNew%2A> właściwość jest ustawiona na `true`).|  
  
### <a name="custom-item-creation"></a>Tworzenie niestandardowego elementu  
 Może obsłużyć <xref:System.Windows.Forms.BindingSource.AddingNew> zdarzenie w celu udostępnienia logika tworzenia elementu. <xref:System.Windows.Forms.BindingSource.AddingNew> Zdarzenie przed dodaniem nowego obiektu do <xref:System.Windows.Forms.BindingSource>. To zdarzenie jest wywoływane po wykonaniu <xref:System.Windows.Forms.BindingSource.AddNew%2A> metoda jest wywoływana, ale przed dodaniem nowego elementu do listy źródłowej. Obsługa tego zdarzenia, zapewnia zachowanie tworzenia niestandardowego elementu bez pochodny <xref:System.Windows.Forms.BindingSource> klasy. Aby uzyskać więcej informacji, zobacz [porady: dostosowywanie dodawania elementu przy formantu BindingSource formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md).  
  
### <a name="transactional-item-creation"></a>Tworzenie elementu transakcyjne  
 <xref:System.Windows.Forms.BindingSource> Wdrażane <xref:System.ComponentModel.ICancelAddNew> interfejsu, co umożliwia tworzenie elementu transakcyjnych. Po za pomocą wywołania tymczasowo jest tworzony nowy element <xref:System.Windows.Forms.BindingSource.AddNew%2A>, dodanie może być zatwierdzona lub wycofana w następujący sposób:  
  
-   <xref:System.ComponentModel.ICancelAddNew.EndNew%2A> Metoda jawnie zobowiązuje się Trwa oczekiwanie na dodanie.  
  
-   Wykonywanie innej operacji kolekcji, takie jak wstawianie, usuwanie lub Przenieś, niejawnie zatwierdzić Trwa oczekiwanie na dodanie.  
  
-   <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A> Metody cofnie Trwa oczekiwanie na dodanie Jeśli metoda nie już został przekazany.  
  
### <a name="ienumerable-support"></a>Obsługa interfejsu IEnumerable  
 <xref:System.Windows.Forms.BindingSource> Składnik umożliwia powiązanie formantów z <xref:System.Collections.IEnumerable> źródeł danych. Z tego składnika można powiązać ze źródłem danych takich jak <xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>.  
  
 Gdy <xref:System.Collections.IEnumerable> źródło danych jest przypisany do <xref:System.Windows.Forms.BindingSource> składnika <xref:System.Windows.Forms.BindingSource> tworzy <xref:System.ComponentModel.IBindingList> i dodaje zawartość <xref:System.Collections.IEnumerable> źródła danych do listy.  
  
### <a name="design-time-support"></a>Obsługi w czasie projektowania  
 Nie można utworzyć niektórych typów obiektów w czasie projektowania, takie jak utworzone z fabryki klasy obiektów lub obiekty zwrócone przez usługę sieci Web. Czasami może być konieczne powiązanie formantów do tych typów w czasie projektowania, nawet jeśli nie ma żadnego obiektu w pamięci, do którego można powiązać formantów. Na przykład konieczne może być etykiety nagłówków kolumn z <xref:System.Windows.Forms.DataGridView> kontroli z nazwami właściwości publiczne typu niestandardowego.  
  
 Aby obsługiwać ten scenariusz <xref:System.Windows.Forms.BindingSource> składnik obsługuje powiązania <xref:System.Type>. Po przypisaniu <xref:System.Type> do <xref:System.Windows.Forms.BindingSource.DataSource%2A> właściwość <xref:System.Windows.Forms.BindingSource> składnik tworzy pustą <xref:System.ComponentModel.BindingList%601> z <xref:System.Type> elementów. Wszystkie formanty, które można następnie powiązać <xref:System.Windows.Forms.BindingSource> składnika będzie otrzymywać alerty o obecność właściwości lub schematu danego typu w czasie projektowania lub w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [porady: powiązanie formantu formularzy systemu Windows z typem](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md).  
  
### <a name="static-listbindinghelper-methods"></a>Metody statycznej ListBindingHelper  
 <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType>, <xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType>, I <xref:System.Windows.Forms.BindingSource> typy całą logikę wspólnej udziału wygenerować listę na podstawie `DataSource` / `DataMember` pary. Ponadto tego wspólnego logiki publicznie uwidocznioną do użytku przez autorów kontroli i osoby trzecie poniżej `static` metod:  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>.  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>Sortowanie i filtrowanie przy użyciu interfejsu IBindingListView  
 <xref:System.Windows.Forms.BindingSource> Wdrażane <xref:System.ComponentModel.IBindingListView> interfejs, który rozszerza <xref:System.ComponentModel.IBindingList> interfejsu. <xref:System.ComponentModel.IBindingList> Oferuje pojedynczej kolumny sortowania i <xref:System.ComponentModel.IBindingListView> oferuje zaawansowane filtrowanie i sortowanie. Z <xref:System.ComponentModel.IBindingListView>, można sortować i filtrować elementy w źródle danych, jeśli źródło danych, również implementuje jednej z tych interfejsów. <xref:System.Windows.Forms.BindingSource> Składnik nie dostarcza implementacji tych elementów. Zamiast tego połączenia są przekazywane do listy źródłowej.  
  
 W poniższej tabeli opisano właściwości używane w przypadku sortowania i filtrowania.  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A> Właściwość|Jeśli źródło danych jest <xref:System.ComponentModel.IBindingListView>, pobiera lub ustawia wyrażenie używane do filtrowania wierszy, które są wyświetlane.|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A> Właściwość|Jeśli źródło danych jest <xref:System.ComponentModel.IBindingList>, pobiera lub ustawia nazwę kolumny sortowania i informacje o kolejności sortowania.<br /><br /> —lub—<br /><br /> Jeśli źródło danych jest <xref:System.ComponentModel.IBindingListView> i obsługuje sortowanie, zaawansowane pobiera wiele nazw kolumn używana do sortowania i kolejność sortowania|  
  
### <a name="integration-with-bindingnavigator"></a>Integracja z BindingNavigator  
 Można użyć <xref:System.Windows.Forms.BindingSource> składnika można powiązać żadnych formantu formularzy systemu Windows ze źródłem danych, ale <xref:System.Windows.Forms.BindingNavigator> kontroli zaprojektowane z myślą o pracy z <xref:System.Windows.Forms.BindingSource> składnika. <xref:System.Windows.Forms.BindingNavigator> Kontroli udostępnia interfejs użytkownika do kontrolowania <xref:System.Windows.Forms.BindingSource> składnika bieżącego elementu. Domyślnie <xref:System.Windows.Forms.BindingNavigator> formant zawiera przyciski odpowiadające metod nawigacji na <xref:System.Windows.Forms.BindingSource> składnika. Aby uzyskać więcej informacji, zobacz [porady: nawigowanie danych za pomocą BindingNavigator formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [BindingSource, składnik — omówienie](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 [BindingNavigator, kontrolka](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Wiązanie danych formularzy Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Instrukcje: powiązanie kontrolki Windows Forms z typem](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [Instrukcje: odzwierciedlanie aktualizacji źródła danych w kontrolce Windows Forms za pomocą elementu BindingSource](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)

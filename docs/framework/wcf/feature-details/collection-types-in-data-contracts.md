---
title: Typy kolekcji w kontraktach danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- collection types [WCF], data contracts
- data contracts [WCF], collection types
- collection types [WCF]
ms.assetid: 9b45b28e-0a82-4ea3-8c33-ec0094aff9d5
ms.openlocfilehash: a2528699387a86ca276cb3ba63eab39544552a4f
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850879"
---
# <a name="collection-types-in-data-contracts"></a>Typy kolekcji w kontraktach danych
A *kolekcji* znajduje się lista elementów określonego typu. W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], takie listy mogą być reprezentowane za pomocą tablic lub innych typów (listy ogólnej, ogólny <xref:System.ComponentModel.BindingList%601>, <xref:System.Collections.Specialized.StringCollection>, lub <xref:System.Collections.ArrayList>). Na przykład kolekcja może zawierać, listę adresów dla danego klienta. Kolekcje te są nazywane *listy kolekcji*, niezależnie od ich rzeczywistego typu.  
  
 Istnieje specjalną postać kolekcji, która reprezentuje skojarzenie między jednego przedmiotu ("klucz"), a inny ("wartość"). W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], takie jak, te są reprezentowane przez typy <xref:System.Collections.Hashtable> i generyczny słownik. Na przykład w kolekcji skojarzenie może być mapowany city ("key") jego populację ("value"). Kolekcje te są nazywane *kolekcji słownika*, niezależnie od ich rzeczywistego typu.  
  
 Kolekcje otrzymują specjalnego traktowania w modelu kontraktu danych.  
  
 Typami, które implementują <xref:System.Collections.IEnumerable> interfejsu, w tym tablice i kolekcje ogólne są rozpoznawane jako kolekcji. Takie typami, które implementują <xref:System.Collections.IDictionary> lub ogólny <xref:System.Collections.Generic.IDictionary%602> interfejsy są kolekcjami słownika; wszystkie inne są listy kolekcji.  
  
 Dodatkowe wymagania dotyczące typów kolekcji, takich jak o metodę o nazwie `Add` i domyślnego konstruktora, opisano szczegółowo w poniższych sekcjach. Gwarantuje to, że typy kolekcji może być zarówno serializacji i deserializacji. Oznacza to, że niektóre kolekcje nie są bezpośrednio obsługiwane, takie jak typowa <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> (ponieważ go nie ma domyślnego konstruktora). Jednak uzyskać informacji o obejściu tych ograniczeń, zobacz sekcję "Przy użyciu kolekcji interfejs typy tylko do odczytu kolekcje i" w dalszej części tego tematu.  
  
 Typy zawarte w kolekcji musi być typy kontraktu danych, lub w inny sposób możliwy do serializacji. Aby uzyskać więcej informacji, zobacz [typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
 Aby uzyskać więcej informacji na temat nowości i co jest uznawane za prawidłowe kolekcji, a także o jak kolekcje są serializacji zobacz informacje o serializacji kolekcji w sekcji "Zaawansowane zasady kolekcji" tego tematu.  
  
## <a name="interchangeable-collections"></a>Wymienne kolekcji  
 Wszystkie kolekcje list tego samego typu, jest uznawany za te same dane kontraktu (o ile nie są dostosowywane przy użyciu <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu, zgodnie z opisem w dalszej części tego tematu). W związku z tym na przykład, poniższy kontraktów danych są równoważne.  
  
 [!code-csharp[c_collection_types_in_data_contracts#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#0)]
 [!code-vb[c_collection_types_in_data_contracts#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#0)]  
  
 Zarówno kontraktów danych powodować podobne do następującego kodu XML.  
  
```xml  
<PurchaseOrder>  
    <customerName>...</customerName>  
    <items>  
        <Item>...</Item>  
        <Item>...</Item>  
        <Item>...</Item>  
        ...  
    </items>  
    <comments>  
        <string>...</string>  
        <string>...</string>  
        <string>...</string>  
        ...  
    </comments>  
</PurchaseOrder>  
```  
  
 Możliwości wymiennego stosowania kolekcji umożliwia należy użyć, na przykład, typ kolekcji, zoptymalizowana pod kątem wydajności na serwerze i typ kolekcji, które mają być powiązane z składników interfejsu użytkownika na komputerze klienckim.  
  
 Podobnie jak kolekcje list, wszystkie kolekcje słownika, które mają te same typy kluczy i wartości jest uznawany za te same dane kontraktu (chyba że dostosowywane przez <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu).  
  
 Tylko w zakresie, w jakim dotyczy kolekcji równoważności sprawach typu kontraktu danych, nie typów .NET. Oznacza to zbiór Type1 jest uważany za równoważny zbiór Type2, jeśli Type1 i Type2 kontraktów danych równoważne.  
  
 Inne niż ogólne kolekcje są uznawane za mają te same dane kontrakt co kolekcje ogólne typu `Object`. (Na przykład kontraktów danych dla <xref:System.Collections.ArrayList> i ogólny <xref:System.Collections.Generic.List%601> z `Object` są takie same.)  
  
## <a name="using-collection-interface-types-and-read-only-collections"></a>Przy użyciu typów interfejsów kolekcji i kolekcji tylko do odczytu  
 Typy interfejsów kolekcji (<xref:System.Collections.IEnumerable>, <xref:System.Collections.IDictionary>ogólny <xref:System.Collections.Generic.IDictionary%602>, lub interfejsy pochodzące z tych interfejsów) również są traktowane jako jako posiadające kontraktów danych kolekcji, odpowiednikiem kontraktów danych kolekcji dla typów rzeczywista kolekcja. W związku z tym można zadeklarować typ poddany serializacji jako typ interfejsu kolekcji, a wyniki są takie same, jak użycie typu rzeczywista kolekcja. Na przykład poniższy kontraktów danych są równoważne.  
  
 [!code-csharp[c_collection_types_in_data_contracts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#1)]
 [!code-vb[c_collection_types_in_data_contracts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#1)]  
  
 Podczas serializacji gdy deklarowany typ jest interfejsem użytej do rzeczywistego wystąpienia może być dowolnego typu, który implementuje ten interfejs. Ograniczenia omówionych wcześniej (o konstruktora domyślnego i `Add` metoda) nie mają zastosowania. Na przykład można ustawić adresy w Customer2 na wystąpienie klasy ogólnej <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> adresu, nawet jeśli nie można zadeklarować bezpośrednio składowa danych klasy typu ogólnego <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
 Podczas deserializacji gdy deklarowany typ jest interfejsem, mechanizm serializacji wybiera typ, który implementuje interfejs zadeklarowane, a typ zostanie uruchomiony. Znane typy mechanizm (opisanego w [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)) nie ma wpływu w tym miejscu; wybór typu jest wbudowana w usługi WCF.  
  
## <a name="customizing-collection-types"></a>Dostosowywanie typów kolekcji  
 Typy kolekcji można dostosować przy użyciu <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybut, który ma kilka zastosowań.  
  
 Należy zwrócić uwagę tego Dostosowywanie kolekcji typy naruszeń kolekcji wymiennego stosowania, dlatego zazwyczaj zalecane jest aby uniknąć stosowania tego atrybutu, jeśli to możliwe. Aby uzyskać więcej informacji na temat tego problemu zobacz sekcję "Zaawansowane zasady kolekcji" w dalszej części tego tematu.  
  
### <a name="collection-data-contract-naming"></a>Kontraktu danych kolekcji nazewnictwa  
 Reguły nazewnictwa typy kolekcji są podobne do reguł nazewnictwa typy kontraktu danych regularnie, zgodnie z opisem w [nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md), chociaż istnieją pewne ważne różnice:  
  
-   <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Atrybut jest używany do dostosowywania nazw, zamiast <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Atrybut ma również `Name` i `Namespace` właściwości.  
  
-   Gdy <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybut nie ma zastosowania, domyślną nazwę i przestrzeń nazw dla typów kolekcji zależą od nazwy i przestrzenie nazw, typów zawartych w kolekcji. Nie wpływają one według nazwy i przestrzeń nazw samego typu kolekcji. Aby uzyskać przykład zobacz następujące typy.  
  
    ```  
    public CustomerList1 : Collection<string> {}  
    public StringList1 : Collection<string> {}  
    ```  
  
 Oba typy samej nazwie kontraktu danych "ArrayOfstring" i nie jest "CustomerList1" lub "StringList1". Oznacza to, że serializacji jednego z tych typów, na poziomie głównym daje podobny do następującego kodu XML.  
  
```xml  
<ArrayOfstring>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</ArrayOfstring>  
```  
  
 Ta reguła nazewnictwa został wybrany do upewnij się, że dowolnego typu bez dostosowania, który reprezentuje listę ciągów ma ten sam kontrakt danych oraz reprezentację XML. Umożliwia możliwości wymiennego stosowania kolekcji. W tym przykładzie CustomerList1 i StringList1 są całkowicie wymienne.  
  
 Jednak gdy <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybut jest stosowany, Kolekcja staje się kontraktu danych kolekcji niestandardowych, nawet jeśli żadne właściwości są ustawione w atrybucie. Nazwa i nazw danych kolekcji umowę, a następnie są zależne od samego typu kolekcji. Aby uzyskać przykład zobacz następujący typ.  
  
 [!code-csharp[c_collection_types_in_data_contracts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#2)]
 [!code-vb[c_collection_types_in_data_contracts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#2)]  
  
 Po serializacji, wynikowy kod XML jest podobny do następującego.  
  
```xml  
<CustomerList2>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</CustomerList2>  
```  
  
 Należy zauważyć, że już nie jest to równoważne Reprezentacja XML typów innych niż dostosowanego przez producenta.  
  
-   Możesz użyć `Name` i `Namespace` właściwości w celu dalszego dostosowywania nazw. Zobacz następujące klasy.  
  
     [!code-csharp[c_collection_types_in_data_contracts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#3)]
     [!code-vb[c_collection_types_in_data_contracts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#3)]  
  
 Wynikowy kod XML jest podobny do następującego.  
  
```xml  
<cust_list>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</cust_list>  
```  
  
 Aby uzyskać więcej informacji zobacz sekcję "Zaawansowane zasady kolekcji" w dalszej części tego tematu.  
  
### <a name="customizing-the-repeating-element-name-in-list-collections"></a>Dostosowywanie powtarzające się nazwy elementu w kolekcji List  
 Kolekcje list zawiera powtarzające się wpisów. Zwykle każdego wpisu powtarzające się jest reprezentowany jako elementu o nazwie zgodnej ze nazwie kontraktu danych typu zawartego w kolekcji.  
  
 W `CustomerList` przykłady, ciągi kolekcji. Nazwa kontraktu danych dla typu pierwotnego ciągu jest "string", więc powtarzający się element "\<Parametry >".  
  
 Jednak przy użyciu <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> właściwość <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu, powtarzając ten można dostosować nazwy elementu. Aby uzyskać przykład zobacz następujący typ.  
  
 [!code-csharp[c_collection_types_in_data_contracts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#4)]
 [!code-vb[c_collection_types_in_data_contracts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#4)]  
  
 Wynikowy kod XML jest podobny do następującego.  
  
```xml  
<CustomerList4>  
    <customer>...</customer>  
    <customer>...</customer>  
    <customer>...</customer>  
    ...  
</CustomerList4>  
```  
  
 Przestrzeń nazw powtarzający się element jest zawsze taki sam, jak przestrzeń nazw kontraktu danych kolekcji, które można dostosować za pomocą `Namespace` właściwości, zgodnie z wcześniejszym opisem.  
  
### <a name="customizing-dictionary-collections"></a>Dostosowywanie kolekcji słownika  
 Kolekcje słownika są zasadniczo listy wpisów, gdzie każdy wpis ma klucz, a następnie według wartości. Tak samo, jak za pomocą regularnego list, można zmienić nazwy elementu, który odpowiada elementowi powtarzające się za pomocą <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> właściwości.  
  
 Ponadto można zmienić nazw elementów, które reprezentują klucz i wartość przy użyciu <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> i <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> właściwości. Przestrzenie nazw dla tych elementów jest taki sam, jak przestrzeń nazw kontraktu danych kolekcji.  
  
 Aby uzyskać przykład zobacz następujący typ.  
  
 [!code-csharp[c_collection_types_in_data_contracts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#5)]
 [!code-vb[c_collection_types_in_data_contracts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#5)]  
  
 Po serializacji, wynikowy kod XML jest podobny do następującego.  
  
```xml  
<CountriesOrRegionsWithCapitals>  
    <entry>  
        <countryorregion>USA</countryorregion>  
        <capital>Washington</capital>  
    </entry>  
    <entry>  
        <countryorregion>France</countryorregion>  
        <capital>Paris</capital>  
    </entry>  
    ...  
</CountriesOrRegionsWithCapitals>  
```  
  
 Aby uzyskać więcej informacji na temat kolekcji słownika zobacz sekcję "Zaawansowane zasady kolekcji" w dalszej części tego tematu.  
  
## <a name="collections-and-known-types"></a>Kolekcje i znanych typów  
 Nie trzeba dodać typy kolekcji do znanych typów, gdy jest używana polymorphically zamiast innych kolekcji lub interfejsów kolekcji. Na przykład, jeśli Deklarujesz element członkowski danych typu <xref:System.Collections.IEnumerable> i przy jego użyciu wysłać wystąpienia <xref:System.Collections.ArrayList>, nie trzeba dodawać <xref:System.Collections.ArrayList> znanych typów.  
  
 Gdy używasz kolekcji polymorphically zamiast typów innych niż kolekcji, należy dodać do znanych typów. Na przykład, jeśli Deklarujesz element członkowski danych typu `Object` i przy jego użyciu wysłać wystąpienia <xref:System.Collections.ArrayList>, Dodaj <xref:System.Collections.ArrayList> znanych typów.  
  
 To pozwala na polymorphically serializacji kolekcji równoważne. Na przykład po dodaniu <xref:System.Collections.ArrayList> do listy znanych typów w poprzednim przykładzie, to nie umożliwiają przypisywanie `Array of Object` klasy, nawet jeśli ma on kontraktu danych równoważne. To nie różni się od zachowania regularne znane typy na serializacji dla typów innych niż kolekcji, ale jest szczególnie ważne, aby zrozumieć w przypadku kolekcji, ponieważ jest ono często kolekcji jako równoważne.  
  
 Podczas serializacji tylko jeden typ może być znane, w dowolnym danym zakresie dla kontraktu danych, a równoważne kolekcje wszystkie mają ten sam kontraktów danych. Oznacza to, że w poprzednim przykładzie, nie można dodać oba <xref:System.Collections.ArrayList> i `Array of Object` do znanych typów w tym samym zakresie. Ponownie jest to równoważne zachowanie znane typy dla typów innych niż kolekcji, ale jest szczególnie ważne, aby zrozumieć dla kolekcji.  
  
 Znane typy mogą być również wymagane dla zawartości z kolekcji. Na przykład jeśli <xref:System.Collections.ArrayList> faktycznie zawiera wystąpienia `Type1` i `Type2`, oba te typy powinny zostać dodane do znanych typów.  
  
 Poniższy przykład przedstawia wykres obiektu poprawnie skonstruowany przy użyciu kolekcji i znanych typów. Przykład jest contrived nieco, ponieważ w rzeczywistej aplikacji będzie zwykle nie definiują następujące elementy członkowskie danych jako `Object`i dlatego nie ma problemów znanego typu/polimorfizmu.  
  
 [!code-csharp[c_collection_types_in_data_contracts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#6)]
 [!code-vb[c_collection_types_in_data_contracts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#6)]  
  
 Na deserializacji gdy deklarowany typ jest typem kolekcji deklarowany typ jest tworzone bez względu na typ, który faktycznie został wysłany. Deklarowany typ jest interfejsem kolekcji, Deserializator wybiera typ, który ma zostać utworzona nie w odniesieniu do znanych typów.  
  
 Również na deserializacji, jeśli deklarowany typ jest typem kolekcji, ale typem kolekcji jest przesyłany, o pasującym typie kolekcji jest pobierany z listy znanych typów. Istnieje możliwość dodawania kolekcji interfejs typów do listy znanych typów, przy deserializacji. W tym przypadku aparat deserializacji ponownie wybiera typ, który ma zostać utworzona.  
  
## <a name="collections-and-the-netdatacontractserializer-class"></a>Kolekcje i klasa NetDataContractSerializer  
 Podczas <xref:System.Runtime.Serialization.NetDataContractSerializer> klasy jest w użyciu, typy kolekcji bez dostosowania (bez <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybut), są tablice nie utracić ich specjalnego znaczenia.  
  
 Typy kolekcji dostosowanego przez producenta nie jest oznaczona za pomocą <xref:System.SerializableAttribute> atrybut nadal może być serializowany przez <xref:System.Runtime.Serialization.NetDataContractSerializer> klasy zgodnie z opisem w <xref:System.SerializableAttribute> atrybutu lub <xref:System.Runtime.Serialization.ISerializable> interfejsu reguły.  
  
 Typy kolekcji niestandardowych, interfejsów kolekcji i tablic nadal są traktowane jako kolekcji, nawet wtedy, gdy <xref:System.Runtime.Serialization.NetDataContractSerializer> klasa jest używana.  
  
## <a name="collections-and-schema"></a>Kolekcje i schematu  
 Wszystkie kolekcje równoważne mają tę samą reprezentację w schemacie języka (XSD) definicji schematu XML. W związku z tym zazwyczaj nie uzyskasz tego samego typu kolekcji w kodzie wygenerowanego klienta, na serwerze. Na przykład serwer może wykorzystać kontraktu danych za pomocą rodzajowego <xref:System.Collections.Generic.List%601> liczby całkowitej składowej danych, ale w kodzie wygenerowanego klienta ten sam element członkowski danych może stać się tablicy liczb całkowitych.  
  
 Słownik kolekcje są oznaczone adnotację schematu specyficzne dla usługi WCF, wskazujące, że są one słowników; w przeciwnym razie są nie do odróżnienia od prostych list, które zawierają wpisów z kluczem i wartością. Aby uzyskać dokładny opis jak kolekcje są reprezentowane w schematu kontraktu danych, zobacz [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Domyślnie typy nie są generowane dla innych dostosowanego przez producenta kolekcji w programie code zaimportowane. Typy kolekcji list składowych danych są importowane jako tablice i typy kolekcji: słownikowy elementów członkowskich danych są importowane jako generyczny słownik.  
  
 Jednak dla kolekcji niestandardowych, oddzielne typy są generowane, oznaczone <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu. (Typ kolekcji niestandardowych w schemacie to taki, który nie używa domyślny obszar nazw, nazwę, powtarzające się nazwy elementu lub klucz/wartość nazw elementów.) Te typy są puste typów, które dziedziczą z ogólnych <xref:System.Collections.Generic.List%601> dla listy typów i generyczny słownik typów słownika.  
  
 Na przykład może mieć następujące typy na serwerze.  
  
 [!code-csharp[c_collection_types_in_data_contracts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#7)]
 [!code-vb[c_collection_types_in_data_contracts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#7)]  
  
 Podczas schematu są eksportowane i importowane wstecz ponownie wygenerowanego kodu klienta jest podobny do następującego (pola są wyświetlane zamiast właściwości w celu ułatwienia odczytu).  
  
 [!code-csharp[c_collection_types_in_data_contracts#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#8)]
 [!code-vb[c_collection_types_in_data_contracts#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#8)]  
  
 Można użyć różnych typów w wygenerowanym kodzie niż domyślne. Na przykład, warto użyć ogólnej <xref:System.ComponentModel.BindingList%601> zamiast regularnych tablic swoje składowych danych ułatwić powiązać składników interfejsu użytkownika.  
  
 Wybierz typy kolekcji w celu wygenerowania, polega na przekazaniu lista typów kolekcji, której chcesz użyć do <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> właściwość <xref:System.Runtime.Serialization.ImportOptions> obiektu podczas importowania schematu. Te typy są nazywane *przywoływane typy kolekcji*.  
  
 Po odwołaniu typów ogólnych one muszą zostać ogólne pełni open lub całkowicie zamknięte typy ogólne.  
  
> [!NOTE]
>  Podczas korzystania z narzędzia Svcutil.exe, to odwołanie można osiągnąć za pomocą **/collectionType** przełącznik wiersza polecenia (skrócona forma: **/ct**). Należy pamiętać, że należy także określić zestawu dla wskazanych typów kolekcji za pomocą **/reference** przełącznika (skrócona forma: **/r**). Typ jest ogólna, musi następować odwrócony pojedynczy cudzysłów i liczby parametrów ogólnych. Odwrócony pojedynczy cudzysłów (\`) nie należy go mylić z znak pojedynczego cudzysłowu ('). Można określić wiele wskazanych typów kolekcji przy użyciu **/collectionType** Przełącz więcej niż jeden raz.  
  
 Na przykład, aby spowodować, że wszystkie listy do zaimportowania jako ogólny <xref:System.Collections.Generic.List%601>.  
  
```  
svcutil.exe MyService.wsdl MyServiceSchema.xsd /r:C:\full_path_to_system_dll\System.dll /ct:System.Collections.Generic.List`1  
```  
  
 Podczas importowania dowolnej kolekcji, ta lista wskazanych typów kolekcji jest skanowany, a najlepiej pasujące kolekcja jest używana, jeśli został znaleziony, jako typ element członkowski danych (w przypadku kolekcji bez dostosowanego przez producenta) lub jako typu podstawowego, aby dziedziczyć po (w przypadku kolekcji niestandardowych). Słowniki tylko są dopasowywane słowników, podczas gdy list są dopasowywane do listy.  
  
 Na przykład jeśli dodasz ogólnego <xref:System.ComponentModel.BindingList%601> i <xref:System.Collections.Hashtable> Lista wskazanych typów wygenerowanego kodu klienta dla poprzedniego przykładu jest podobny do następującego.  
  
 [!code-csharp[c_collection_types_in_data_contracts#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#9)]
 [!code-vb[c_collection_types_in_data_contracts#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#9)]  
  
 Typy interfejsów kolekcji można określić jako część Twojego wskazanych typów kolekcji, ale nie można określić typy kolekcji nieprawidłowy (takie jak te bez `Add` metoda lub Konstruktor publiczny).  
  
 Zamknięte ogólnego jest uważana za najlepsze dopasowanie. (Typy nieuniwersalne są uważane za równoważne do zamkniętego typów ogólnych z `Object`). Na przykład jeśli typy ogólne <xref:System.Collections.Generic.List%601> z <xref:System.DateTime>ogólny <xref:System.ComponentModel.BindingList%601> (rodzajowa Otwórz), i <xref:System.Collections.ArrayList> są wskazanych typów kolekcji, że jest generowany.  
  
 [!code-csharp[c_collection_types_in_data_contracts#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#10)]
 [!code-vb[c_collection_types_in_data_contracts#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#10)]  
  
 Kolekcje list tylko przypadki w poniższej tabeli są obsługiwane.  
  
|Typ odwołania|Interfejs implementowany przez typ odwołania|Przykład|Typ traktowane jako:|  
|---------------------|----------------------------------------------|-------------|----------------------|  
|Ogólny nieuniwersalne lub zamknięte (dowolnej liczbie parametrów)|Inne niż ogólne|`MyType : IList`<br /><br /> lub<br /><br /> `MyType<T> : IList`<br /><br /> gdzie T = `int`|Zamknięte ogólnego elementu `Object` (na przykład `IList<object>`)|  
|Ogólny nieuniwersalne lub zamknięte (dowolną liczbę parametrów, które nie muszą odpowiadać typ kolekcji)|Zamknięte ogólny|`MyType : IList<string>`<br /><br /> lub<br /><br /> `MyType<T> : IList<string>` gdzie T =`int`|Ogólny zamknięte (na przykład `IList<string>`)|  
|Zamknięte ogólnego z dowolnej liczby parametrów|Otwarte ogólne przy użyciu jednego z parametrów typu|`MyType<T,U,V> : IList<U>`<br /><br /> gdzie T =`int`, U =`string`, V =`bool`|Ogólny zamknięte (na przykład `IList<string>`)|  
|Otwarte ogólne z jednym parametrem|Ogólny Otwórz za pomocą parametru typu|`MyType<T> : IList<T>`, T jest otwarty|Otwarte ogólne (na przykład `IList<T>`)|  
  
 Jeśli typ implementuje więcej niż jeden listy kolekcji interfejs, obowiązują następujące ograniczenia:  
  
-   Jeśli typ implementuje ogólny <xref:System.Collections.Generic.IEnumerable%601> (lub jego interfejsy pochodne) wiele razy dla różnych typów, typ nie jest uznawany za typ prawidłową kolekcję odwołania i jest ignorowana. Ta zasada obowiązuje, nawet jeśli niektóre implementacje są nieprawidłowe lub otwartych typów ogólnych. Na przykład typ, który implementuje ogólny <xref:System.Collections.Generic.IEnumerable%601> z `int` i ogólny <xref:System.Collections.Generic.IEnumerable%601> t będzie nigdy używana jako kolekcja odwołania `int` lub innego typu, niezależnie od tego, czy typ ma `Add` akceptowanie — metoda `int` lub `Add` metoda akceptuje parametr typu T lub obu.  
  
-   Jeśli typ implementuje interfejs kolekcji generycznej także <xref:System.Collections.IList>, typ nigdy nie jest używany jako typ kolekcji odwołania, chyba że interfejs kolekcji generycznej jest zamknięty ogólnego typu <xref:System.Object>.  
  
 Dla kolekcji słownika obsługiwane są tylko przypadki w poniższej tabeli.  
  
|Typ odwołania|Interfejs implementowany przez typ odwołania|Przykład|Typ traktowane jako|  
|---------------------|----------------------------------------------|-------------|---------------------|  
|Ogólny nieuniwersalne lub zamknięte (dowolnej liczbie parametrów)|<xref:System.Collections.IDictionary>|`MyType : IDictionary`<br /><br /> lub<br /><br /> `MyType<T> : IDictionary` gdzie T =`int`|Zamknięte ogólny `IDictionary<object,object>`|  
|Ogólny zamknięte (dowolnej liczbie parametrów)|<xref:System.Collections.Generic.IDictionary%602>, zamknięte|`MyType<T> : IDictionary<string, bool>` gdzie T =`int`|Ogólny zamknięte (na przykład `IDIctionary<string,bool>`)|  
|Ogólny zamknięte (dowolnej liczbie parametrów)|Ogólny <xref:System.Collections.Generic.IDictionary%602>klucza lub wartość jest zamknięty, druga jest otwarty i korzysta z jednego z parametrów typu|`MyType<T,U,V> : IDictionary<string,V>` gdzie T =`int`, U =`float`, V =`bool`<br /><br /> lub<br /><br /> `MyType<Z> : IDictionary<Z,bool>` gdy Z =`string`|Ogólny zamknięte (na przykład `IDictionary<string,bool>`)|  
|Ogólny zamknięte (dowolnej liczbie parametrów)|Ogólny <xref:System.Collections.Generic.IDictionary%602>, zarówno klucz i wartość są otwarte i każda używa parametrów typu|`MyType<T,U,V> : IDictionary<V,U>` gdzie T =`int`, U =`bool`, V =`string`|Ogólny zamknięte (na przykład `IDictionary<string,bool>`)|  
|Otwarte ogólne (dwa parametry)|Ogólny <xref:System.Collections.Generic.IDictionary%602>, Otwórz, będą wykorzystywane serwery ogólnych parametrów typu w kolejności, są wyświetlane|`MyType<K,V> : IDictionary<K,V>`, K i V zarówno Otwórz|Otwarte ogólne (na przykład `IDictionary<K,V>`)|  
  
 Jeśli typ implementuje interfejsy <xref:System.Collections.IDictionary> i ogólny <xref:System.Collections.Generic.IDictionary%602>tylko ogólny <xref:System.Collections.Generic.IDictionary%602> uznaje się.  
  
 Odwoływanie się do typów ogólnych częściowych nie jest obsługiwane.  
  
 Duplikaty są niedozwolone, na przykład nie można dodać zarówno ogólnego <xref:System.Collections.Generic.List%601> z `Integer` i ogólny zbiór `Integer` do <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, ponieważ dzięki temu możliwe ustalenie, znajduje się on do użycia podczas na liście liczb całkowitych w schemacie. Duplikaty są wykrywane tylko wtedy, gdy typem w schemacie, który udostępnia problem duplikaty. Na przykład, jeśli schemat importowanych nie zawiera listy liczb całkowitych, może on być ma zarówno ogólnego <xref:System.Collections.Generic.List%601> z `Integer` i ogólny zbiór `Integer` w <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, ale nie ma żadnego efektu.  
  
## <a name="advanced-collection-rules"></a>Kolekcja zaawansowanych reguł  
  
### <a name="serializing-collections"></a>Serializowanie kolekcji  
 Oto lista reguł kolekcji serializacji:  
  
-   Łączenie typów kolekcji (o kolekcji kolekcji) jest dozwolone. Tablice nieregularne są traktowane jako kolekcji z kolekcji. Tablice wielowymiarowe nie są obsługiwane.  
  
-   Tablice bajtów i tablice <xref:System.Xml.XmlNode> są typy specjalne tablic, które są traktowane jako podstawowych, nie kolekcji. Szeregowanie tablicę bajtów wyników w pojedynczy element XML, który zawiera fragment dane zakodowane w formacie Base64, zamiast element osobne dla każdego bajtu. Aby uzyskać więcej informacji o tym, jak tablica <xref:System.Xml.XmlNode> jest traktowane, zobacz [typy XML i ADO.NET w kontraktach danych](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md). Oczywiście tych specjalnych typów mogą się uczestniczyć w kolekcji: tablica tablicy bajtów powoduje powstanie wielu elementów XML za pomocą zawierającego fragmentów danych w formacie Base64.  
  
-   Jeśli <xref:System.Runtime.Serialization.DataContractAttribute> atrybut jest stosowany do typu kolekcji, typ jest traktowany jako typ kontraktu regularnych danych, nie jako kolekcję.  
  
-   Jeśli typ kolekcji implementuje <xref:System.Xml.Serialization.IXmlSerializable> interfejs, są stosowane następujące reguły, posiada typ `myType:IList<string>, IXmlSerializable`:  
  
    -   Gdy deklarowany typ jest `IList<string>`, typ jest serializowana jako listę.  
  
    -   Gdy deklarowany typ jest `myType`, jest serializowany jako `IXmlSerializable`.  
  
    -   Gdy deklarowany typ jest `IXmlSerializable`, jest serializowany jako `IXmlSerializable`, ale tylko wtedy, gdy dodasz `myType` do listy znanych typów.  
  
-   Kolekcje są serializacji i deserializacji za pomocą metod przedstawiono w poniższej tabeli.  
  
|Implementuje — typ kolekcji|Metody o nazwie na serializacji|Metody o nazwie na deserializacji|  
|--------------------------------|-----------------------------------------|-------------------------------------------|  
|Ogólny <xref:System.Collections.Generic.IDictionary%602>|`get_Keys`, `get_Values`|Dodaj ogólny|  
|<xref:System.Collections.IDictionary>|`get_Keys`, `get_Values`|`Add`|  
|Ogólny <xref:System.Collections.Generic.IList%601>|Ogólny <xref:System.Collections.Generic.IList%601> indeksatora|Dodaj ogólny|  
|Ogólny <xref:System.Collections.Generic.ICollection%601>|Moduł wyliczający|Dodaj ogólny|  
|<xref:System.Collections.IList>|<xref:System.Collections.IList> Indeksator|`Add`|  
|Ogólny <xref:System.Collections.Generic.IEnumerable%601>|`GetEnumerator`|Wywołana metoda statyczna `Add` przyjmującą jeden parametr odpowiedniego typu (typ parametru ogólnego) lub jednej z jej typów podstawowych. Taka metoda musi istnieć przez serializator traktowanie typ kolekcji jako kolekcji zarówno podczas serializacji i deserializacji.|  
|<xref:System.Collections.IEnumerable> (i w związku z tym <xref:System.Collections.ICollection>, co wynika z niego)|`GetEnumerator`|Wywołana metoda niestatycznych `Add` przyjmującą jeden parametr typu `Object`. Taka metoda musi istnieć przez serializator traktowanie typ kolekcji jako kolekcji zarówno podczas serializacji i deserializacji.|  
  
 Powyższa tabela zawiera interfejsy kolekcji w kolejności malejącej. Oznacza to, na przykład, że typ implementuje interfejsy <xref:System.Collections.IList> i ogólny <xref:System.Collections.Generic.IEnumerable%601>, kolekcji jest serializacji i deserializacji zgodnie z opisem w <xref:System.Collections.IList> reguły:  
  
-   Po deserializacji wszystkie kolekcje są deserializacji przez utworzenie wystąpienia typu przez wywołanie konstruktora domyślnego, który musi być obecny serializator traktowanie typ kolekcji jako kolekcji zarówno podczas serializacji i deserializacji.  
  
-   Jeśli ten sam interfejs kolekcji generycznej jest więcej niż raz (na przykład, jeśli typ implementuje zarówno ogólnego <xref:System.Collections.Generic.ICollection%601> z `Integer` i ogólny <xref:System.Collections.Generic.ICollection%601> z <xref:System.String>) i znajduje się interfejs nie jest wyższy priorytet, jest kolekcji nie są traktowane jako prawidłową kolekcję.  
  
-   Typy kolekcji mogą mieć <xref:System.SerializableAttribute> atrybut zastosowanych do nich i zaimplementować <xref:System.Runtime.Serialization.ISerializable> interfejsu. Oba te są ignorowane. Jednak jeśli typ nie spełnia całkowicie wymagań typu kolekcji (na przykład `Add` Brak metody), typ nie jest uważany za typem kolekcji i w związku z tym <xref:System.SerializableAttribute> atrybutu i <xref:System.Runtime.Serialization.ISerializable> interfejsu służą do określania czy typ może być serializowany.  
  
-   Stosowanie <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu kolekcję, aby dostosować go usuwa <xref:System.SerializableAttribute> poprzedzających mechanizm rezerwowy. Zamiast tego, jeśli dostosowany kolekcji jest kolekcji nie spełniają wpisz wymagań, <xref:System.Runtime.Serialization.InvalidDataContractException> wyjątku. Parametry wyjątków często zawierają informacje, który wyjaśnia, dlaczego danego typu nie jest uważany za prawidłowy kolekcji (nie `Add` metody, bez konstruktora domyślnego i tak dalej), więc jest często przydatne w celu zastosowania <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu dla celów debugowania.  
  
### <a name="collection-naming"></a>Nadawanie nazw kolekcji  
 Oto lista kolekcji reguł nazewnictwa:  
  
-   Domyślny obszar nazw dla wszystkich umów danych kolekcji słownika, a także dla kontraktów danych kolekcji listy, które zawierają typy pierwotne, jest `http://schemas.microsoft.com/2003/10/Serialization/Arrays` chyba że zastąpione przy użyciu Namespace. Typy, które mapują na wbudowane typy XSD, a także `char`, `Timespan`, i `Guid` typów, są traktowane jako podstawowych, w tym celu.  
  
-   Domyślny obszar nazw dla typów kolekcji, które zawierają niepodstawowe typy, chyba że zostanie on przesłonięty za pomocą Namespace, jest taka sama jak przestrzeń nazw kontraktu danych typu zawartego w kolekcji.  
  
-   Domyślnej nazwy kontraktów danych kolekcji listy, chyba że zastąpione przy użyciu nazwy, to ciąg, który "ArrayOf" w połączeniu z nazwą kontraktu danych typu zawartego w kolekcji. Na przykład w nazwie kontraktu danych dla ogólnego listy liczb całkowitych jest "ArrayOfint". Należy pamiętać, że nazwa kontraktu danych `Object` jest "anyType", więc nazwa kontraktu danych nieogólnego list, takich jak <xref:System.Collections.ArrayList> jest "ArrayOfanyType".  
  
 Domyślna nazwa dla słownika danych kolekcji kontraktów, chyba że zastąpione przy użyciu `Name`, jest ciąg "ArrayOfKeyValueOf" w połączeniu z nazwą kontraktu danych typu klucza, następuje nazwa kontraktu danych o typie wartości. Na przykład dane Nazwa kontraktu dla słownika ogólny ciąg i liczba całkowita jest "ArrayOfKeyValueOfstringint". Ponadto jeśli klucz i typy wartości nie są typami pierwotnymi, skrótu przestrzeni nazw z przestrzeni nazw kontraktu danych typów kluczy i wartości jest dołączany do nazwy. Aby uzyskać więcej informacji na temat skrótów przestrzeni nazw, zobacz [nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 Każdy kontraktu danych kolekcji słownika ma pomocnika kontraktu danych, który reprezentuje jeden wpis w słowniku. Jego nazwa jest taka sama jak słownik kontraktu danych, z wyjątkiem prefiks "ArrayOf" i jego przestrzeń nazw są takie same jak dla kontraktu danych słownika. Na przykład dla kontraktu danych "ArrayOfKeyValueOfstringint" słownik, kontraktu danych "KeyValueofstringint" reprezentuje jeden wpis w słowniku. Można dostosować nazwę tohoto kontraktu danych za pomocą `ItemName` właściwości, zgodnie z opisem w następnej sekcji.  
  
 Reguły nazewnictwa typu ogólnego, zgodnie z opisem w [nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md)pełni mają zastosowanie do typów kolekcji; będący, nawiasy klamrowe w nazwie służy do wskazania parametrów typu ogólnego. Jednak numery w nawiasy klamrowe dotyczą parametrów ogólnych i nie typy zawarte w tej kolekcji.  
  
## <a name="collection-customization"></a>Dostosowywanie kolekcji  
 Zastosowań następujące <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu jest zabronione i spowodować <xref:System.Runtime.Serialization.InvalidDataContractException> wyjątek:  
  
-   Stosowanie <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu z typem, do którego <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybut została zastosowana, lub do jednego z jego typów pochodnych.  
  
-   Stosowanie <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu typu, który implementuje <xref:System.Xml.Serialization.IXmlSerializable> interfejsu.  
  
-   Stosowanie <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu typu innego niż kolekcji.  
  
-   Trwa próba skonfigurowania <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> lub <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> na <xref:System.Runtime.Serialization.CollectionDataContractAttribute> zastosowany do typu innego niż słownika.  
  
### <a name="polymorphism-rules"></a>Polimorfizm reguły  
 Jak wcześniej wspomniano, dostosowywanie kolekcji za pomocą <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybut może zakłócać możliwości wymiennego stosowania kolekcji. Dwa typy kolekcji niestandardowych tylko jest uznawana za równoważne, jeśli ich nazwy, przestrzeń nazw, nazwa elementu, a także nazwy klucza i wartości (jeśli są to kolekcje słownika) są zgodne.  
  
 Z powodu dostosowań istnieje możliwość przypadkowo Użyj kontraktu danych kolekcji jednego gdy oczekiwany jest inny. Należy ich unikać. Zobacz następujące typy.  
  
 [!code-csharp[c_collection_types_in_data_contracts#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#11)]
 [!code-vb[c_collection_types_in_data_contracts#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#11)]  
  
 W tym przypadku wystąpienie `Marks1` mogą być przypisane do `testMarks`. Jednak `Marks2` nie należy używać, ponieważ jego kontraktu danych nie jest uważany za równoważny `IList<int>` kontraktu danych. Nazwa kontraktu danych jest "Marks2", a nie "ArrayOfint" i powtarzające się nazwa elementu jest "\<oznaczyć >" ale nie "\<int >".  
  
 Reguły w tabeli poniżej dotyczą polimorficznego przypisania kolekcji.  
  
|Deklarowany typ|Przypisanie kolekcji bez dostosowania|Przypisanie kolekcji niestandardowych|  
|-------------------|--------------------------------------------|---------------------------------------|  
|Obiekt|Nazwa kontraktu jest serializowana.|Nazwa kontraktu jest serializowana.<br /><br /> Dostosowywanie jest używany.|  
|Interfejs kolekcji|Nazwa umowy nie jest serializowana.|Nazwa umowy nie jest serializowana.<br /><br /> Dostosowanie nie jest used.*|  
|Dostosowanego przez producenta spoza zbioru|Nazwa umowy nie jest serializowana.|Nazwa kontraktu jest serializowana.<br /><br /> Dostosowanie jest used.* *|  
|Kolekcja niestandardowych|Nazwa kontraktu jest serializowana. Dostosowanie nie jest used.* *|Nazwa kontraktu jest serializowana.<br /><br /> Dostosowywanie przypisanego typu jest used.* *|  
  
 * Z <xref:System.Runtime.Serialization.NetDataContractSerializer> klas, dostosowywanie jest używany w tym przypadku. <xref:System.Runtime.Serialization.NetDataContractSerializer> Klasy w tym przypadku również serializuje nazwą rzeczywistego typu, więc deserializacji działa zgodnie z oczekiwaniami.  
  
 ** W tych przypadkach wystąpień nieprawidłowy schemat i dlatego należy unikać.  
  
 W przypadkach, w którym Nazwa kontraktu jest serializowana typ kolekcji przypisanej powinien być na liście znanych typów. Odwrotny również ma wartość true: w przypadkach, w którym nazwa nie jest serializowana, dodając typ do listy znanych typów nie jest wymagana.  
  
 Tablica typu pochodnego można przypisać do tablicy typu podstawowego. W takim przypadku Nazwa kontraktu przypadku typ pochodny jest serializowany dla każdego elementu powtarzające się. Na przykład, jeśli typ `Book` pochodzi od typu `LibraryItem`, można przypisać tablicę `Book` tablicę `LibraryItem`. To nie ma zastosowania do innych typów kolekcji. Na przykład nie można przypisać `Generic List of Book` do `Generic List of LibraryItem`. Można jednak przypisywać `Generic List of LibraryItem` zawierający `Book` wystąpień. Zarówno w tablicy, jak i w przypadku nietablicowego `Book` powinien znajdować się na liście znanych typów.  
  
## <a name="collections-and-object-reference-preservation"></a>Kolekcje i zachowywania odwołanie do obiektu  
 Funkcje serializatora w trybie, w których zostaje zachowany odwołania do obiektu, zachowywanie odwołanie do obiektu również zastosowanie do kolekcji. W szczególności tożsamość obiektu są zachowywane dla całej kolekcji i pojedynczych elementów zawartych w kolekcjach. Słowników tożsamość obiektu są zachowywane, zarówno dla obiektów pary klucz/wartość i poszczególnych obiektów kluczy i wartości.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>

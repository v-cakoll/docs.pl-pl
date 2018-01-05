---
title: Typy kolekcji w kontraktach danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- collection types [WCF], data contracts
- data contracts [WCF], collection types
- collection types [WCF]
ms.assetid: 9b45b28e-0a82-4ea3-8c33-ec0094aff9d5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e74bd7d90d5653890fd5cf48e76c81d0227c6172
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="collection-types-in-data-contracts"></a>Typy kolekcji w kontraktach danych
A *kolekcji* znajduje się lista elementów określonego typu. W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], tych list można przedstawić przy użyciu tablic lub innych typów (listy ogólnej, ogólny <xref:System.ComponentModel.BindingList%601>, <xref:System.Collections.Specialized.StringCollection>, lub <xref:System.Collections.ArrayList>). Na przykład kolekcja może utrzymywać listę adresów dla danego klienta. Kolekcje te są nazywane *listy kolekcji*, niezależnie od ich rzeczywistego typu.  
  
 Istnieje specjalny rodzaj kolekcji, która reprezentuje skojarzenie między jeden element ("klucza") i innej ("wartość"). W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], takich jak, te są reprezentowane przez typy <xref:System.Collections.Hashtable> i rodzajowy słownika. Na przykład w kolekcji skojarzenie może być mapowany Miasto ("klucza") jego wypełniania ("value"). Kolekcje te są nazywane *kolekcje słownika*, niezależnie od ich rzeczywistego typu.  
  
 Kolekcje odbierać szczególnego traktowania w modelu kontraktu danych.  
  
 Typy, które implementują <xref:System.Collections.IEnumerable> interfejsu, łącznie z tablicami i kolekcje ogólne są uznawane za kolekcji. Typy które implementują <xref:System.Collections.IDictionary> lub ogólny <xref:System.Collections.Generic.IDictionary%602> interfejsy są kolekcjami słownika; pozostałe są kolekcjami listy.  
  
 Dodatkowe wymagania dla typów kolekcji, takie jak o metodę o nazwie `Add` i konstruktora domyślnego opisano szczegółowo w poniższych sekcjach. Dzięki temu, że typy kolekcji można zarówno serializacji i deserializacji. Oznacza to, że niektóre kolekcje nie są bezpośrednio obsługiwane, takie jak ogólnego <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> (ponieważ go nie ma konstruktora domyślnego). Jednak uzyskać informacji o tych ograniczeń obejścia, zobacz sekcję "Przy użyciu kolekcji interfejsu typów i tylko do odczytu kolekcji" w dalszej części tego tematu.  
  
 Typy zawarte w kolekcji musi być typy kontraktu danych, lub w inny sposób możliwy do serializacji. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Co to jest i co to jest uznawane za prawidłowe kolekcji, jak również informacje jak kolekcje są serializowane, zapoznaj się z informacjami o serializowanie kolekcji w sekcji "Zaawansowane zasady kolekcji" tego tematu.  
  
## <a name="interchangeable-collections"></a>Wymienne kolekcje  
 Wszystkie kolekcje listy tego samego typu, jest uznawany za tych samych danych kontraktu (chyba że są one dostosowane przy użyciu <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu, zgodnie z opisem w dalszej części tego tematu). W związku z tym na przykład następujące kontraktów danych są równoważne.  
  
 [!code-csharp[c_collection_types_in_data_contracts#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#0)]
 [!code-vb[c_collection_types_in_data_contracts#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#0)]  
  
 Zarówno kontraktów danych powoduje podobny do następującego kodu XML.  
  
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
  
 Możliwości wymiennego stosowania kolekcji umożliwia można użyć, na przykład typ kolekcji, zoptymalizowana pod kątem wydajności na serwerze i typ kolekcji zaprojektowane powiązać składniki interfejsu użytkownika na komputerze klienckim.  
  
 Podobnie jak listy kolekcji, wszystkie kolekcje słownika, które mają taki sam klucz i wartość typy jest uznawany za tych samych danych kontraktu (chyba że dostosowane przez <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu).  
  
 Tylko w zakresie, w jakim dotyczy kolekcji pełnienia roli równoważnika sprawach typu kontraktu danych, nie typów .NET. Oznacza to zbiór Type1 jest uznane za równorzędne kolekcji Type2, jeśli Type1 i Type2 kontraktów danych równoważne.  
  
 Inne niż ogólne kolekcje są traktowane jako mają te same dane kontrakt, co kolekcje ogólne typu `Object`. (Na przykład kontraktów danych do <xref:System.Collections.ArrayList> i rodzajowy <xref:System.Collections.Generic.List%601> z `Object` są takie same.)  
  
## <a name="using-collection-interface-types-and-read-only-collections"></a>Przy użyciu typów interfejsów kolekcji i kolekcji tylko do odczytu  
 Typy interfejsów kolekcji (<xref:System.Collections.IEnumerable>, <xref:System.Collections.IDictionary>ogólny <xref:System.Collections.Generic.IDictionary%602>, lub interfejsy pochodzące z tych interfejsów) są również uznać kontraktów danych kolekcji, odpowiednikiem kontraktów danych kolekcji dla typów rzeczywista kolekcja. W związku z tym można zadeklarować typ poddany serializacji jako typ interfejsu kolekcji, a wyniki są takie same jak użycie typu rzeczywistego kolekcji. Na przykład następujące kontraktów danych są równoważne.  
  
 [!code-csharp[c_collection_types_in_data_contracts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#1)]
 [!code-vb[c_collection_types_in_data_contracts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#1)]  
  
 Podczas serializacji gdy deklarowany typ jest interfejsem, typ rzeczywistego wystąpienia używany może być dowolnego typu, który implementuje ten interfejs. Ograniczenia omówionych wcześniej (o konstruktora domyślnego i `Add` metoda) nie są stosowane. Na przykład można ustawić adresów w Customer2 na wystąpienie ogólnej <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> adresu, mimo że element członkowski danych klasy bezpośrednio nie można zadeklarować typu ogólnego <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
 Podczas deserializacji, gdy deklarowany typ jest interfejsem, aparat serializacji wybiera typ, który implementuje interfejs zadeklarowane i tworzenia wystąpienia typu klasy. Znane typy mechanizmu (opisany w [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)) nie ma wpływu; wbudowane wybór typu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="customizing-collection-types"></a>Dostosowywanie typów kolekcji  
 Typy kolekcji można dostosować, używając <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybut, który ma kilka zastosowań.  
  
 Należy zwrócić uwagę tego Dostosowywanie kolekcji typów dokonywania kolekcji wymiennego stosowania, dlatego zazwyczaj zalecane jest aby uniknąć stosowania tego atrybutu, jeśli to możliwe. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Ten problem, zobacz sekcję "Zaawansowane zasady kolekcji" w dalszej części tego tematu.  
  
### <a name="collection-data-contract-naming"></a>Kontraktu danych kolekcji nazewnictwa  
 Reguły nazewnictwa typy kolekcji są podobne do reguł nazewnictwa typy kontraktu danych regularne, zgodnie z opisem w [nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md), mimo że istnieje kilka istotnych różnic:  
  
-   <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Atrybut służy do dostosowywania nazwę, a nie <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Ma również atrybut `Name` i `Namespace` właściwości.  
  
-   Gdy <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybut nie ma zastosowania, domyślną nazwę i przestrzeń nazw dla typów kolekcji są zależne od nazwy i przestrzenie nazw typów zawartych w kolekcji. Nie jest narażony na nazwę i przestrzeń nazw samego typu kolekcji. Na przykład zobacz następujące typy.  
  
    ```  
    public CustomerList1 : Collection<string> {}  
    public StringList1 : Collection<string> {}  
    ```  
  
 Nazwa kontraktu danych obu typów "ArrayOfstring" i nie jest "CustomerList1" lub "StringList1". Oznacza to, że serializacji jednego z następujących typów na poziomie głównym daje podobny do następującego kodu XML.  
  
```xml  
<ArrayOfstring>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</ArrayOfstring>  
```  
  
 Ta reguła nazewnictwa została wybrana, aby upewnić się, że wszelkie bez dostosowania typ, który reprezentuje listę ciągów ma sam kontrakt danych oraz reprezentacji XML. Umożliwia możliwości wymiennego stosowania kolekcji. W tym przykładzie CustomerList1 i StringList1 są całkowicie wymienne.  
  
 Jednakże, gdy <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybut jest stosowany, kolekcji staje się kontraktu danych kolekcji niestandardowych, nawet jeśli żadne właściwości są ustawiane w ustawieniach atrybutu. Nazwę i przestrzeń nazw zebrania danych kontraktu, a następnie są zależne od samego typu kolekcji. Na przykład zobacz następujący typ.  
  
 [!code-csharp[c_collection_types_in_data_contracts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#2)]
 [!code-vb[c_collection_types_in_data_contracts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#2)]  
  
 Podczas serializacji, wynikowy kod XML jest podobny do następującego.  
  
```xml  
<CustomerList2>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</CustomerList2>  
```  
  
 Zwróć uwagę, że nie jest to już odpowiednikiem reprezentację XML typy bez dostosowania.  
  
-   Można użyć `Name` i `Namespace` właściwości w celu przeprowadzenia dalszej dostosowywania nazw. Zobacz następujące klasy.  
  
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
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]w sekcji "Zaawansowane zasady kolekcji" w dalszej części tego tematu.  
  
### <a name="customizing-the-repeating-element-name-in-list-collections"></a>Dostosowywanie identycznych nazwa elementu w kolekcji listy  
 Lista kolekcje zawierają identycznych wpisów. Zazwyczaj każdy wpis identycznych jest reprezentowany jako element o nazwie zgodnie z nazwą kontraktu danych typu zawartego w kolekcji.  
  
 W `CustomerList` przykłady, kolekcje zawiera ciągi. Nazwie kontraktu danych dla typu pierwotnego ciągu jest "string", dlatego został powtarzający się element "\<ciągu >".  
  
 Jednak przy użyciu <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> właściwość <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu to powtarzające się nazwy elementu można dostosować. Na przykład zobacz następujący typ.  
  
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
  
 Przestrzeń nazw elementu powtarzalnego zawsze jest taka sama jak przestrzeń nazw kontraktu danych kolekcji, które można dostosować za pomocą `Namespace` właściwości, jak opisano wcześniej.  
  
### <a name="customizing-dictionary-collections"></a>Dostosowywanie słownika kolekcje  
 Słownik kolekcje są zasadniczo listy wpisów, gdzie każdy wpis ma klucz, a następnie według wartości. Tak samo, jak przy użyciu list regularne, można zmienić nazwy elementu, który odpowiada na powtarzający się element za pomocą <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> właściwości.  
  
 Ponadto można zmienić nazw elementów reprezentujących klucz i wartość przy użyciu <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> i <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> właściwości. Przestrzenie nazw dla tych elementów są takie same jak przestrzeń nazw kontraktu danych kolekcji.  
  
 Na przykład zobacz następujący typ.  
  
 [!code-csharp[c_collection_types_in_data_contracts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#5)]
 [!code-vb[c_collection_types_in_data_contracts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#5)]  
  
 Podczas serializacji, wynikowy kod XML jest podobny do następującego.  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Słownik kolekcji, zobacz sekcję "Zaawansowane zasady kolekcji" w dalszej części tego tematu.  
  
## <a name="collections-and-known-types"></a>Kolekcje i znanych typów  
 Dodawanie typów kolekcji znanych typów stosowania polymorphically zamiast inne kolekcje lub interfejsy kolekcji nie jest konieczne. Na przykład w przypadku elementu członkowskiego danych typu <xref:System.Collections.IEnumerable> i umożliwia wysyłanie wystąpienia <xref:System.Collections.ArrayList>, nie trzeba dodać <xref:System.Collections.ArrayList> do znanych typów.  
  
 Gdy używasz kolekcji polymorphically zamiast typy kolekcji nie muszą zostać dodane do znanych typów. Na przykład w przypadku elementu członkowskiego danych typu `Object` i umożliwia wysyłanie wystąpienia <xref:System.Collections.ArrayList>, Dodaj <xref:System.Collections.ArrayList> do znanych typów.  
  
 To nie pozwalają na polymorphically serializować równoważne kolekcji. Na przykład podczas dodawania <xref:System.Collections.ArrayList> do listy znanych typów w poprzednim przykładzie, to nie jest możliwe przypisanie `Array of Object` klasy, nawet jeśli ma kontraktu danych równoważne. To nie różni się od w serializacji dla typów innych niż kolekcji zachowanie regularne znanych typów, ale jest szczególnie ważne zrozumieć w przypadku kolekcji, ponieważ bardzo często kolekcji jako równoważne.  
  
 Podczas serializacji może być znane tylko jeden typ w dowolnym danym zakresie dla kontraktu danych danego i równoważne kolekcje wszystkie mają tego samego kontraktów danych. Oznacza to, że w poprzednim przykładzie, nie można dodać zarówno <xref:System.Collections.ArrayList> i `Array of Object` do znanych typów, w tym samym zakresie. Ponownie co jest równoważne zachowanie znanych typów dla typów innych niż kolekcji, ale jest szczególnie ważne zrozumieć dla kolekcji.  
  
 Znane typy mogą być również wymagane dla zawartości kolekcji. Na przykład jeśli <xref:System.Collections.ArrayList> faktycznie zawiera wystąpienia `Type1` i `Type2`, oba te typy powinny zostać dodane do znanych typów.  
  
 Poniższy przykład przedstawia wykres obiektu poprawnie skonstruowany przy użyciu kolekcji i znanych typów. Przykład jest contrived nieco, ponieważ w rzeczywistej aplikacji zwykle nie definiuje się następujące elementy członkowskie danych jako `Object`i dlatego nie ma typu/polimorfizm znane problemy.  
  
 [!code-csharp[c_collection_types_in_data_contracts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#6)]
 [!code-vb[c_collection_types_in_data_contracts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#6)]  
  
 Podczas deserializacji gdy deklarowany typ jest typem kolekcji deklarowany typ jest utworzona bez względu na typ faktycznie wysłane. Deklarowany typ jest interfejsem kolekcji, Deserializator wybiera typ, który ma zostać utworzone nie w odniesieniu do znanych typów.  
  
 Również podczas deserializacji, jeśli deklarowany typ nie jest typem kolekcji, ale typ kolekcji jest wysyłany, odpowiedniego typu kolekcji jest pobierany z listy znanych typów. Istnieje możliwość Dodaj typy kolekcji interfejs do listy znanych typów przy deserializacji. W takim przypadku aparat deserializacji ponownie wybiera typ, który ma zostać utworzona.  
  
## <a name="collections-and-the-netdatacontractserializer-class"></a>Kolekcje i klasy NetDataContractSerializer  
 Gdy <xref:System.Runtime.Serialization.NetDataContractSerializer> klasa jest używana, typy kolekcji bez dostosowania (bez <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybut) czy są tablice nie utracić ich specjalne znaczenie.  
  
 Typy kolekcji dostosowane nie jest oznaczony atrybutem <xref:System.SerializableAttribute> atrybutu nadal może być serializowany przez <xref:System.Runtime.Serialization.NetDataContractSerializer> klasy zgodnie z <xref:System.SerializableAttribute> atrybutu lub <xref:System.Runtime.Serialization.ISerializable> interfejsu reguły.  
  
 Typy kolekcji niestandardowych, interfejsy kolekcji i tablic nadal są traktowane jako kolekcje, nawet wtedy, gdy <xref:System.Runtime.Serialization.NetDataContractSerializer> klasy jest używany.  
  
## <a name="collections-and-schema"></a>Kolekcje i schematu  
 Wszystkie kolekcje równoważne mają taką samą reprezentację w schemacie (XSD) języka definicji schematu XML. W związku z tym zazwyczaj nie otrzymasz ten sam typ kolekcji w kodzie wygenerowanego klienta co na serwerze. Na przykład serwer może wykorzystać kontraktu danych z ogólnego <xref:System.Collections.Generic.List%601> elementu członkowskiego danych Liczba całkowita, ale w kodzie wygenerowanego klienta elementu członkowskiego danych może stać się tablica liczb całkowitych.  
  
 Słownik kolekcje są oznaczone ikoną z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]— adnotacja schematu, wskazujące, że znajdują się słowniki; w przeciwnym razie są nierozróżnialne z prostej listy zawierające wpisów z klucza i wartości. Aby uzyskać dokładny opis sposobu kolekcje są reprezentowane w schemacie kontraktu danych, zobacz [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Domyślnie typy nie są generowane bez dostosowania kolekcji w kodzie zaimportowany. Elementy członkowskie danych typów kolekcji listy są importowane jako tablic, a elementy członkowskie danych typów kolekcji słownika są importowane jako ogólnego słownika.  
  
 Jednak dla kolekcji niestandardowych, osobne typy są generowane, oznaczone <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu. (Typ kolekcji niestandardowych w schemacie to taki, który nie używa domyślnej przestrzeni nazw, nazwę, identycznych nazwy elementu lub klucza i wartości nazwy elementu.) Te typy są puste typów, które pochodzą od zwykłego <xref:System.Collections.Generic.List%601> dla listy typów i rodzajowy słownika dla typów słownika.  
  
 Na przykład może mieć następujące typy na serwerze.  
  
 [!code-csharp[c_collection_types_in_data_contracts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#7)]
 [!code-vb[c_collection_types_in_data_contracts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#7)]  
  
 Gdy schematu są eksportowane i importowane spód ponownie wygenerowanego kodu klienta jest podobne do następujących (pola są wyświetlane zamiast właściwości czytelnej).  
  
 [!code-csharp[c_collection_types_in_data_contracts#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#8)]
 [!code-vb[c_collection_types_in_data_contracts#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#8)]  
  
 Można użyć różnych typów w wygenerowanym kodzie niż domyślne. Na przykład można używać zwykłego <xref:System.ComponentModel.BindingList%601> zamiast regularne tablice sieci elementów członkowskich danych ułatwić powiązać składników interfejsu użytkownika.  
  
 Aby wybrać typy kolekcji w celu wygenerowania, Przekaż listę typów kolekcji, którego chcesz użyć do <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> właściwość <xref:System.Runtime.Serialization.ImportOptions> obiektu podczas importowania schematu. Te typy są nazywane *odwołuje się do typów kolekcji*.  
  
 Po odwołaniu typów ogólnych one musi być całkowicie otwarte ogólne lub ogólne całkowicie zamknięty.  
  
> [!NOTE]
>  Podczas korzystania z narzędzia Svcutil.exe, to odwołanie można osiągnąć za pomocą **/collectionType** przełącznik wiersza polecenia (forma krótka: **/ct**). Należy pamiętać, że musi również określać zestawu dla wskazanych typów kolekcji przy użyciu **/reference** przełącznika (forma krótka: **/r**). Typ jest rodzajowy, musi występować oferty Wstecz i liczby parametrów ogólnych. Wstecz cudzysłowu (') jest nie należy mylić z znak pojedynczego cudzysłowu ('). Można określić wiele wskazanych typów kolekcji za pomocą **/collectionType** przełącznika więcej niż raz.  
  
 Na przykład, aby spowodować, że wszystkie listy do zaimportowania jako zwykłego <xref:System.Collections.Generic.List%601>.  
  
```  
svcutil.exe MyService.wsdl MyServiceSchema.xsd /r:C:\full_path_to_system_dll\System.dll /ct:System.Collections.Generic.List`1  
```  
  
 Podczas importowania kolekcji, ta lista wskazanych typów kolekcji jest skanowany i najlepiej pasujące kolekcja jest używana, jeśli został znaleziony, jako typ elementu członkowskiego danych (w przypadku kolekcji bez dostosowania) lub jako podstawowy typ wyprowadzenia z (dla kolekcji niestandardowych). Słowniki tylko są dopasowywane słowników, podczas gdy listy są dopasowywane do listy.  
  
 Na przykład, jeśli dodasz ogólnego <xref:System.ComponentModel.BindingList%601> i <xref:System.Collections.Hashtable> do listy typów do którego istnieje odwołanie, jest podobny do następującego wygenerowanego kodu klienta dla poprzedniego przykładu.  
  
 [!code-csharp[c_collection_types_in_data_contracts#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#9)]
 [!code-vb[c_collection_types_in_data_contracts#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#9)]  
  
 Typy interfejsów kolekcji można określić jako część programu wskazanych typów kolekcji, ale nie można określić typy kolekcji nieprawidłowe (takich jak te, których nie `Add` metody lub konstruktora publicznego).  
  
 Zamknięte rodzajowa jest uważana za najlepsze dopasowanie. (Inne niż ogólne typy zostały uznane za równorzędne do zamkniętego typów ogólnych z `Object`). Na przykład jeśli typy ogólne <xref:System.Collections.Generic.List%601> z <xref:System.DateTime>ogólny <xref:System.ComponentModel.BindingList%601> (Otwórz ogólny), i <xref:System.Collections.ArrayList> są typy kolekcji do którego istnieje odwołanie, poniżej zostanie wygenerowany.  
  
 [!code-csharp[c_collection_types_in_data_contracts#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#10)]
 [!code-vb[c_collection_types_in_data_contracts#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#10)]  
  
 Dla listy kolekcji są obsługiwane tylko przypadków w poniższej tabeli.  
  
|Typu występującego w odwołaniu|Typ odwołania do interfejsu implementowanego przez|Przykład|Typ traktowane jako:|  
|---------------------|----------------------------------------------|-------------|----------------------|  
|Inne niż ogólne lub zamkniętych ogólny (dowolną liczbę parametrów)|Inne niż ogólne|`MyType : IList`<br /><br /> lub<br /><br /> `MyType<T> : IList`<br /><br /> gdzie T =`int`|Zamknięte ogólnego z `Object` (na przykład `IList<object>`)|  
|Inne niż ogólne lub zamkniętych ogólny (dowolną liczbę parametrów, które nie muszą odpowiadać typ kolekcji)|Zamknięte ogólny|`MyType : IList<string>`<br /><br /> lub<br /><br /> `MyType<T> : IList<string>`gdzie T =`int`|Ogólny zamkniętego (na przykład `IList<string>`)|  
|Zamknięte z dowolnej liczby parametrów ogólnych|Otwarte ogólne przy użyciu jednego z parametrów typu|`MyType<T,U,V> : IList<U>`<br /><br /> gdzie T =`int`, U =`string`, V =`bool`|Ogólny zamkniętego (na przykład `IList<string>`)|  
|Otwarte ogólne z jednym parametrem|Ogólny Otwórz za pomocą parametru typu|`MyType<T> : IList<T>`, T jest otwarty|Otwarte ogólne (na przykład `IList<T>`)|  
  
 Jeśli typ implementuje więcej niż jeden interfejs kolekcji listy, obowiązują następujące ograniczenia:  
  
-   Jeśli typ implementuje ogólny <xref:System.Collections.Generic.IEnumerable%601> (lub pochodne interfejsy) wiele razy dla różnych typów, typ nie jest uznawany za typ prawidłowej kolekcji przywoływany i jest ignorowana. Dotyczy to nawet wtedy, gdy niektóre implementacje są nieprawidłowe lub Otwórz ogólne. Na przykład typu, który implementuje ogólny <xref:System.Collections.Generic.IEnumerable%601> z `int` i rodzajowy <xref:System.Collections.Generic.IEnumerable%601> t nigdy nie będzie można użyć jako kolekcja przywoływanego `int` lub innego typu, niezależnie od tego, czy typ ma `Add` akceptowanie — metoda `int` lub `Add` metoda przyjmuje parametr typu T lub oba.  
  
-   Jeśli typ implementuje interfejs kolekcji ogólnych oraz <xref:System.Collections.IList>, typ nigdy nie jest używany jako typ kolekcji do którego istnieje odwołanie, chyba, że interfejs kolekcji ogólnych jest zamknięty ogólnego typu <xref:System.Object>.  
  
 Kolekcje słownika przypadkach w poniższej tabeli są obsługiwane.  
  
|Typu występującego w odwołaniu|Typ odwołania do interfejsu implementowanego przez|Przykład|Typ traktowane jako|  
|---------------------|----------------------------------------------|-------------|---------------------|  
|Inne niż ogólne lub zamkniętych ogólny (dowolną liczbę parametrów)|<xref:System.Collections.IDictionary>|`MyType : IDictionary`<br /><br /> lub<br /><br /> `MyType<T> : IDictionary`gdzie T =`int`|Zamknięte ogólny`IDictionary<object,object>`|  
|Ogólny zamkniętego (dowolną liczbę parametrów)|<xref:System.Collections.Generic.IDictionary%602>, zamknięty|`MyType<T> : IDictionary<string, bool>`gdzie T =`int`|Ogólny zamkniętego (na przykład `IDIctionary<string,bool>`)|  
|Ogólny zamkniętego (dowolną liczbę parametrów)|Ogólny <xref:System.Collections.Generic.IDictionary%602>, klucz lub wartość jest zamknięty, drugi jest otwarty i korzysta z jednego z parametrów typu|`MyType<T,U,V> : IDictionary<string,V>`gdzie T =`int`, U =`float`, V =`bool`<br /><br /> lub<br /><br /> `MyType<Z> : IDictionary<Z,bool>`gdy Z =`string`|Ogólny zamkniętego (na przykład `IDictionary<string,bool>`)|  
|Ogólny zamkniętego (dowolną liczbę parametrów)|Ogólny <xref:System.Collections.Generic.IDictionary%602>, zarówno klucz i wartość są otwarte i każda używa jednego z parametrów typu|`MyType<T,U,V> : IDictionary<V,U>`gdzie T =`int`, U =`bool`, V =`string`|Ogólny zamkniętego (na przykład `IDictionary<string,bool>`)|  
|Otwarte ogólne (dwa parametry)|Ogólny <xref:System.Collections.Generic.IDictionary%602>, Otwórz, używa zarówno ogólnych parametrów typu w kolejności ich występowania|`MyType<K,V> : IDictionary<K,V>`, K i V zarówno Otwórz|Otwarte ogólne (na przykład `IDictionary<K,V>`)|  
  
 Jeśli typ implementuje zarówno <xref:System.Collections.IDictionary> i rodzajowy <xref:System.Collections.Generic.IDictionary%602>tylko ogólny <xref:System.Collections.Generic.IDictionary%602> jest uznawany za.  
  
 Odwołania do typów ogólnych z częściowa nie jest obsługiwana.  
  
 Duplikaty są niedozwolone, na przykład nie można dodać zarówno ogólnego <xref:System.Collections.Generic.List%601> z `Integer` i rodzajowy zbiór `Integer` do <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, ponieważ dzięki temu możliwa do określenia, które do użycia podczas listy liczb całkowitych został znaleziony w schemacie. Duplikaty są wykrywane tylko wtedy, gdy jest typem w schemacie, który ujawnia problem duplikaty. Na przykład, jeśli schemat importowana nie zawiera listy liczb całkowitych, jego może mieć zarówno ogólnego <xref:System.Collections.Generic.List%601> z `Integer` i rodzajowy zbiór `Integer` w <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, ale nie ma żadnego efektu.  
  
## <a name="advanced-collection-rules"></a>Zaawansowane kolekcji reguł  
  
### <a name="serializing-collections"></a>Serializowanie kolekcji  
 Oto lista reguł kolekcji serializacji:  
  
-   Łączenie typów kolekcji (o kolekcji kolekcje) jest dozwolone. Tablice nieregularne są traktowane jako kolekcje z kolekcji. Tablice wielowymiarowe nie są obsługiwane.  
  
-   Tablice typu byte i tablice <xref:System.Xml.XmlNode> to typy tablicy specjalne, które są traktowane jako typów podstawowych, nie kolekcji. Serializacja tablicę bajtów wyników w pojedynczy element XML zawierający fragmentów danych algorytmem Base64, zamiast elementu osobne dla każdego bajtu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]w jaki sposób tablicę <xref:System.Xml.XmlNode> jest traktowane, zobacz [typy XML i ADO.NET w kontraktach danych](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md). Oczywiście te typy specjalne mogą się uczestniczyć w kolekcji: tablica tablicy bajtów skutkuje wiele elementów XML, z zawierających fragmentów danych algorytmem Base64.  
  
-   Jeśli <xref:System.Runtime.Serialization.DataContractAttribute> atrybut jest stosowany do typu kolekcji, typ jest traktowany jako typ kontraktu regularnych danych, nie jako kolekcja.  
  
-   Jeśli typ kolekcji implementuje <xref:System.Xml.Serialization.IXmlSerializable> interfejsu, stosowane są następujące reguły, określony typ `myType:IList<string>, IXmlSerializable`:  
  
    -   Jeśli jest zadeklarowanym typem `IList<string>`, typ jest szeregowana jako listę.  
  
    -   Jeśli jest zadeklarowanym typem `myType`, jest szeregowana jako `IXmlSerializable`.  
  
    -   Jeśli jest zadeklarowanym typem `IXmlSerializable`, jest szeregowana jako `IXmlSerializable`, ale tylko wtedy, gdy dodasz `myType` do listy znanych typów.  
  
-   Kolekcje są serializacji i deserializacji za pomocą metod przedstawiono w poniższej tabeli.  
  
|Implementuje typ kolekcji|Metody wywołano serializacji|Metody o nazwie przy deserializacji|  
|--------------------------------|-----------------------------------------|-------------------------------------------|  
|Ogólny<xref:System.Collections.Generic.IDictionary%602>|`get_Keys`, `get_Values`|Dodaj ogólny|  
|<xref:System.Collections.IDictionary>|`get_Keys`, `get_Values`|`Add`|  
|Ogólny<xref:System.Collections.Generic.IList%601>|Ogólny <xref:System.Collections.Generic.IList%601> indeksatora|Dodaj ogólny|  
|Ogólny<xref:System.Collections.Generic.ICollection%601>|Moduł wyliczający|Dodaj ogólny|  
|<xref:System.Collections.IList>|<xref:System.Collections.IList>Indeksator|`Add`|  
|Ogólny<xref:System.Collections.Generic.IEnumerable%601>|`GetEnumerator`|Wywołana metoda niestatyczna `Add` który przyjmuje jeden parametr odpowiedniego typu (typ parametru ogólnego) lub jeden z jego typów podstawowych. Taka metoda musi istnieć dla serializatora traktowanie typ kolekcji jako kolekcji zarówno podczas serializacji i deserializacji.|  
|<xref:System.Collections.IEnumerable>(a zatem <xref:System.Collections.ICollection>, co wynika z niego)|`GetEnumerator`|Wywołana metoda niestatyczna `Add` który przyjmuje jeden parametr typu `Object`. Taka metoda musi istnieć dla serializatora traktowanie typ kolekcji jako kolekcji zarówno podczas serializacji i deserializacji.|  
  
 W poprzedniej tabeli wymieniono interfejsy kolekcji w kolejności malejącej. Oznacza to, na przykład, że jeśli typ implementuje zarówno <xref:System.Collections.IList> i rodzajowy <xref:System.Collections.Generic.IEnumerable%601>, Kolekcja jest serializacji i deserializacji zgodnie z <xref:System.Collections.IList> reguł:  
  
-   Przy deserializacji wszystkie kolekcje są rozszeregować przez utworzenie wystąpienia typu przez wywołanie domyślnego konstruktora, który musi być obecny dla serializatora traktowanie typ kolekcji jako kolekcji zarówno podczas serializacji i deserializacji.  
  
-   Jeśli ten sam interfejs rodzajowej kolekcji jest więcej niż raz (na przykład, jeśli typ implementuje zarówno ogólnego <xref:System.Collections.Generic.ICollection%601> z `Integer` i rodzajowy <xref:System.Collections.Generic.ICollection%601> z <xref:System.String>) i zostanie znaleziony żaden interfejs wyższy priorytet, Kolekcja jest nie są traktowane jako prawidłowe kolekcji.  
  
-   Typy kolekcji może mieć <xref:System.SerializableAttribute> atrybut zastosowanych do nich i można zaimplementować <xref:System.Runtime.Serialization.ISerializable> interfejsu. Oba te są ignorowane. Jednak jeśli typ nie pełni spełnia wymagania typu kolekcji (na przykład `Add` brakuje metody), typ nie jest uznawany za typ kolekcji i w związku z tym <xref:System.SerializableAttribute> atrybutu i <xref:System.Runtime.Serialization.ISerializable> interfejsu są używane do określania Określa, czy można zserializować typu.  
  
-   Stosowanie <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu do kolekcji, aby dostosować go usuwa <xref:System.SerializableAttribute> poprzedzających mechanizm rezerwowy. Zamiast tego, jeśli dostosowany zbiór jest kolekcji nie spełniają wymagania dotyczące typu, <xref:System.Runtime.Serialization.InvalidDataContractException> wyjątku. Parametry wyjątków często zawierają informacje, wyjaśniający, dlaczego danego typu nie jest uznawane za prawidłowe kolekcji (nie `Add` metody, brak konstruktora domyślnego i tak dalej), więc często jest to przydatne w celu zastosowania <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu na potrzeby debugowania.  
  
### <a name="collection-naming"></a>Kolekcja nazw  
 Oto lista kolekcji reguł nazewnictwa:  
  
-   Domyślny obszar nazw dla wszystkich umów danych kolekcji słownika, a także listy kontraktów danych kolekcji, które zawierają typy pierwotne, jest http://schemas.microsoft.com/2003/10/Serialization/Arrays, chyba że przesłonić przy użyciu Namespace. Typy, które mapują na wbudowane typy XSD, jak również `char`, `Timespan`, i `Guid` typów, są traktowane jako podstawowych, w tym celu.  
  
-   Domyślny obszar nazw dla typów kolekcji, które zawierają typy innego niż pierwotny, chyba że jest on przesłaniany przy użyciu Namespace, jest taka sama jak przestrzeń nazw kontraktu danych typu zawartego w kolekcji.  
  
-   Domyślna nazwa listy kontraktów danych kolekcji, chyba że zastąpione przy użyciu nazwy, jest ciąg "ArrayOf" łączyć o nazwie kontraktu danych typu zawartego w kolekcji. Na przykład nazwa kontraktu danych ogólnych listy liczb całkowitych jest "ArrayOfint". Należy pamiętać, że nazwa kontraktu danych `Object` jest "anyType", takie jak nazwa kontraktu danych list nieogólnego <xref:System.Collections.ArrayList> jest "ArrayOfanyType".  
  
 Domyślna nazwa dla słownika danych kolekcji umów, chyba że przesłonić przy użyciu `Name`, to ciąg "ArrayOfKeyValueOf" połączone z nazwą kontraktu danych typu klucza następuje nazwa kontraktu danych typu wartości. Na przykład dane nazwy kontraktu dla ogólnego słownika ciągiem, a liczba całkowita jest "ArrayOfKeyValueOfstringint". Ponadto jeśli klucz lub typów wartości nie są typy pierwotne, skrót przestrzeni nazw z przestrzeni nazw kontraktu danych typów kluczy i wartości jest dołączany do nazwy. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]skróty przestrzeni nazw, zobacz [nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 Każdy kontraktu danych kolekcji słownik ma pomocnika kontraktu danych, który reprezentuje jeden wpis w słowniku. Jego nazwa jest taka sama jak w przypadku słownika kontraktu danych, z wyjątkiem prefiksu "ArrayOf" i jego przestrzeni nazw są takie same jak kontraktu danych słownika. Na przykład dla kontraktu danych słownika "ArrayOfKeyValueOfstringint", "KeyValueofstringint" kontraktu danych reprezentuje jeden wpis w słowniku. Nazwa tego kontraktu danych można dostosować, używając `ItemName` właściwości, zgodnie z opisem w następnej sekcji.  
  
 Ogólny typ reguły nazewnictwa, zgodnie z opisem w [nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md)pełni dotyczą typów kolekcji; które jest, można podać parametry typu ogólnego nawiasy klamrowe w nazwie. Jednak liczb w nawiasy klamrowe dotyczą parametrów ogólnych i nie typów zawartych w kolekcji.  
  
## <a name="collection-customization"></a>Dostosowywanie kolekcji  
 Następujące zastosowania <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu jest zabronione i spowodować <xref:System.Runtime.Serialization.InvalidDataContractException> wyjątek:  
  
-   Stosowanie <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu z typem, do którego <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybut został zastosowany, lub do jednego z jego typów pochodnych.  
  
-   Stosowanie <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu typu, który implementuje <xref:System.Xml.Serialization.IXmlSerializable> interfejsu.  
  
-   Stosowanie <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu typu będącego kolekcją.  
  
-   Trwa próba skonfigurowania <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> lub <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> na <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybut zastosowany do typu z systemem innym niż słownika.  
  
### <a name="polymorphism-rules"></a>Polimorfizm reguły  
 Jak wcześniej wspomniano, dostosowywanie kolekcji przy użyciu <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybut może zakłócać możliwości wymiennego stosowania kolekcji. Dwa typy dostosowany zbiór tylko jest uznawana za równoważne, jeśli ich nazwy, przestrzeń nazw, nazwa elementu, a także nazwy kluczy i wartości (jeśli są one kolekcje słownika) są zgodne.  
  
 Z powodu dostosowań istnieje możliwość przypadkowego Użyj kontraktu danych kolekcji jednego gdy oczekiwano innego. Należy unikać to. Zobacz następujące typy.  
  
 [!code-csharp[c_collection_types_in_data_contracts#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#11)]
 [!code-vb[c_collection_types_in_data_contracts#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#11)]  
  
 W tym przypadku wystąpienie `Marks1` można przypisać do `testMarks`. Jednak `Marks2` nie powinna być używana, ponieważ jego kontraktu danych nie jest uznawane za równoważne `IList<int>` kontraktu danych. Nazwa kontraktu danych jest "Marks2", a nie "ArrayOfint" i identycznych nazwa elementu jest "\<oznaczyć >", a nie "\<int >".  
  
 Reguły w poniższej tabeli dotyczą polimorficznych przypisania kolekcji.  
  
|Deklarowany typ|Przypisywanie bez dostosowania kolekcji|Przypisywanie dostosowany zbiór|  
|-------------------|--------------------------------------------|---------------------------------------|  
|Obiekt|Nazwa kontraktu jest serializowany.|Nazwa kontraktu jest serializowany.<br /><br /> Dostosowywanie jest używany.|  
|Interfejs kolekcji|Nazwa kontraktu nie jest serializowany.|Nazwa kontraktu nie jest serializowany.<br /><br /> Dostosowanie nie jest used.*|  
|Dostosowane spoza zbioru|Nazwa kontraktu nie jest serializowany.|Nazwa kontraktu jest serializowany.<br /><br /> Dostosowywanie jest used.* *|  
|Kolekcja niestandardowych|Nazwa kontraktu jest serializowany. Dostosowanie nie jest used.* *|Nazwa kontraktu jest serializowany.<br /><br /> Dostosowanie typu przypisany jest used.* *|  
  
 * Z <xref:System.Runtime.Serialization.NetDataContractSerializer> klas, dostosowywanie jest używany w tym przypadku. <xref:System.Runtime.Serialization.NetDataContractSerializer> w takim przypadku klasa nazwy typu rzeczywistego serializuje również, więc deserializacji działa zgodnie z oczekiwaniami.  
  
 ** Tych przypadkach spowodować nieprawidłowy schemat wystąpień i w związku z tym należy unikać.  
  
 W przypadkach, gdy jest serializowany nazwy kontraktu typ kolekcji przypisanej musi należeć do listy znanych typów. Odwrotny również ma wartość true: w przypadku, gdy nazwa nie jest serializowany, dodanie typu do listy znanych typów nie jest wymagana.  
  
 Tablica typu pochodnego można przypisać do tablicy typu podstawowego. W takim przypadku Nazwa kontraktu dla typu pochodnego jest serializowany dla każdego elementu powtarzających się. Na przykład, jeśli typem `Book` pochodzi z typu `LibraryItem`, można przypisać tablicę `Book` do tablicy `LibraryItem`. Nie dotyczy innych typów kolekcji. Na przykład nie można przypisać `Generic List of Book` do `Generic List of LibraryItem`. Można jednak przypisywać `Generic List of LibraryItem` zawierający `Book` wystąpień. Zarówno w tablicy, jak i w przypadku nietablicowego `Book` musi należeć do listy znanych typów.  
  
## <a name="collections-and-object-reference-preservation"></a>Kolekcje i zachowywania odwołanie do obiektu  
 Funkcje serializator w trybie, w którym zachowuje on odwołania do obiektów, zachowywania odwołanie do obiektu również zastosowanie do kolekcji. W szczególności tożsamość obiektu są zachowywane dla całej kolekcji i indywidualnych elementów zawartych w kolekcji. Słowników tożsamość obiektu jest zachowywana zarówno dla obiekt pary klucz/wartość i pojedyncze obiekty klucz i wartość.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>

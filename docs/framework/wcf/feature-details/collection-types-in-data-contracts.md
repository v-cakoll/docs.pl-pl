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
ms.openlocfilehash: 810238ee631808dac472456f910eb52f8bbf550c
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363812"
---
# <a name="collection-types-in-data-contracts"></a>Typy kolekcji w kontraktach danych

*Kolekcja* jest listą elementów określonego typu. W .NET Framework takie listy mogą być reprezentowane przy użyciu tablic lub różnych typów (lista ogólna, ogólna <xref:System.ComponentModel.BindingList%601>, <xref:System.Collections.Specialized.StringCollection>lub <xref:System.Collections.ArrayList>). Na przykład kolekcja może zawierać listę adresów dla danego klienta. Kolekcje te są nazywane *kolekcjami list*, niezależnie od ich rzeczywistego typu.

Istnieje specjalna forma kolekcji, która reprezentuje skojarzenie między jednym elementem ("kluczem") a drugim ("value"). W .NET Framework są one reprezentowane przez typy takie jak <xref:System.Collections.Hashtable> i słownik ogólny. Na przykład kolekcja skojarzeń może mapować miasto ("klucz") na jego populację ("wartość"). Kolekcje te są nazywane *kolekcjami słownikowymi*, niezależnie od ich rzeczywistego typu.

Kolekcje otrzymują specjalne traktowanie w modelu kontraktu danych.

Typy implementujące <xref:System.Collections.IEnumerable> interfejs, łącznie z tablicami i kolekcjami ogólnymi, są rozpoznawane jako kolekcje. Z tych typów, które implementują <xref:System.Collections.IDictionary> <xref:System.Collections.Generic.IDictionary%602> interfejsy lub, są kolekcjami słownikowymi; wszystkie inne są kolekcjami list.

Dodatkowe wymagania dotyczące typów kolekcji, takich jak posiadanie metody `Add` i Konstruktor bez parametrów, zostały szczegółowo omówione w poniższych sekcjach. Gwarantuje to, że typy kolekcji mogą być serializowane i deserializowane. Oznacza to, że niektóre kolekcje nie są bezpośrednio obsługiwane, takie jak generyczne <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> (ponieważ nie ma konstruktora bez parametrów). Jednak aby uzyskać informacje o obchodzeniu tych ograniczeń, zobacz sekcję "używanie typów interfejsów kolekcji i kolekcji tylko do odczytu" w dalszej części tego tematu.

Typy zawarte w kolekcjach muszą być typami kontraktu danych lub mogą być serializowane w inny sposób. Aby uzyskać więcej informacji, zobacz [Typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).

Aby uzyskać więcej informacji o tym, co to jest i co nie jest traktowane jako prawidłowa kolekcja, a także o sposobie serializacji kolekcji, zobacz informacje na temat serializacji kolekcji w sekcji "Zaawansowane reguły kolekcji" w tym temacie.

## <a name="interchangeable-collections"></a>Kolekcje wymienne

Wszystkie kolekcje list tego samego typu są uznawane za mające ten sam kontrakt danych (chyba że są dostosowane przy <xref:System.Runtime.Serialization.CollectionDataContractAttribute> użyciu atrybutu, jak opisano w dalszej części tego tematu). W tym przypadku następujące kontrakty danych są równoważne.

[!code-csharp[c_collection_types_in_data_contracts#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#0)]
[!code-vb[c_collection_types_in_data_contracts#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#0)]

Oba Kontrakty danych powodują, że kod XML jest podobny do następującego kodu.

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

Możliwość zmiany kolekcji pozwala na przykład użyć typu kolekcji zoptymalizowanego pod kątem wydajności na serwerze i typu kolekcji zaprojektowanego do powiązania ze składnikami interfejsu użytkownika na komputerze klienckim.

Podobnie jak w przypadku kolekcji list, wszystkie kolekcje słowników, które mają ten sam typ klucza i wartości, są uznawane za mające ten sam <xref:System.Runtime.Serialization.CollectionDataContractAttribute> kontrakt danych (chyba że atrybut jest dostosowywany).

Tylko typ kontraktu danych ma znaczenie, jeśli chodzi o równoważność kolekcji, a nie typy .NET. Oznacza to, że kolekcja Type1 jest traktowana jako odpowiednik kolekcji Type2, jeśli Type1 i Type2 mają równoważne Kontrakty danych.

Kolekcje inne niż ogólne są uznawane za mające ten sam kontrakt danych jako kolekcje ogólne `Object`typu. (Na przykład Kontrakty danych dla <xref:System.Collections.ArrayList> i `Object` rodzajowe <xref:System.Collections.Generic.List%601> są takie same).

## <a name="using-collection-interface-types-and-read-only-collections"></a>Używanie typów interfejsów kolekcji i kolekcji tylko do odczytu

Typy interfejsów kolekcji (<xref:System.Collections.IEnumerable>, <xref:System.Collections.IDictionary>, ogólne <xref:System.Collections.Generic.IDictionary%602>lub interfejsy pochodzące z tych interfejsów) są również uznawane za mające Kontrakty danych kolekcji, równoważne z kontraktami danych kolekcji dla rzeczywistych typów kolekcji. W ten sposób można zadeklarować typ, który jest serializowany jako typ interfejsu kolekcji, a wyniki są takie same, jak w przypadku użycia rzeczywistego typu kolekcji. Na przykład następujące kontrakty danych są równoważne.

[!code-csharp[c_collection_types_in_data_contracts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#1)]
[!code-vb[c_collection_types_in_data_contracts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#1)]

Podczas serializacji, gdy zadeklarowany typ jest interfejsem, rzeczywisty typ wystąpienia może być dowolnym typem, który implementuje ten interfejs. Opisane wcześniej ograniczenia (posiadające Konstruktor bez parametrów i `Add` Metoda) nie mają zastosowania. Na przykład można ustawić adresy w Customer2 do wystąpienia ogólnego <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> adresu, nawet jeśli nie można bezpośrednio zadeklarować elementu członkowskiego danych typu ogólnego. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>

Podczas deserializacji, gdy zadeklarowany typ jest interfejsem, aparat serializacji wybiera typ implementujący zadeklarowany interfejs, a typ jest skonkretyzowany. Mechanizm znanych typów (opisany w [znanych typach kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)) nie ma wpływu na to miejsce; wybór typu jest wbudowany w funkcję WCF.

## <a name="customizing-collection-types"></a>Dostosowywanie typów kolekcji

Można dostosować typy kolekcji przy użyciu <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu, który ma kilka zastosowania.

Należy zauważyć, że dostosowanie typów kolekcji powoduje naruszenie możliwości zmiany kolekcji, dlatego ogólnie zaleca się uniknięcie stosowania tego atrybutu, jeśli to możliwe. Więcej informacji o tym problemie znajduje się w sekcji "Zaawansowane reguły kolekcji" w dalszej części tego tematu.

### <a name="collection-data-contract-naming"></a>Nazewnictwo kontraktu danych kolekcji

Reguły nazewnictwa typów kolekcji są podobne do tych w przypadku nazewnictwa zwykłych typów kontraktów danych, zgodnie z opisem w [nazwach kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md), chociaż istnieją pewne istotne różnice:

- Ten <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybut służy do dostosowywania nazwy, a nie <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu. Ten <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybut ma `Name` również właściwości `Namespace` i.

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Gdy atrybut nie jest stosowany, domyślna nazwa i przestrzeń nazw dla typów kolekcji zależą od nazw i przestrzeni nazw typów zawartych w kolekcji. Nie dotyczy to nazwy i przestrzeni nazw samego typu kolekcji. Aby zapoznać się z przykładem, zobacz następujące typy.

  ```csharp
  public CustomerList1 : Collection<string> {}
  public StringList1 : Collection<string> {}
  ```

Oba typy "Nazwa kontraktu danych to" ArrayOfstring ", a nie" CustomerList1 "lub" StringList1 ". Oznacza to, że Serializacja dowolnego z tych typów na poziomie głównym daje XML podobne do poniższego kodu.

```xml
<ArrayOfstring>
    <string>...</string>
    <string>...</string>
    <string>...</string>
    ...
</ArrayOfstring>
```

Ta reguła nazewnictwa została wybrana, aby upewnić się, że dowolny niedostosowany typ reprezentujący listę ciągów ma ten sam kontrakt danych i reprezentację XML. Dzięki temu możliwe jest przeprowadzenie wymienności kolekcji. W tym przykładzie CustomerList1 i StringList1 są całkowicie zamienne.

Jednak gdy <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybut zostanie zastosowany, kolekcja zostanie przypisana do niestandardowego kontraktu danych kolekcji, nawet jeśli w atrybucie nie są ustawione żadne właściwości. Nazwa i przestrzeń nazw kontraktu danych kolekcji są zależne od samego typu kolekcji. Aby zapoznać się z przykładem, zobacz następujący typ.

[!code-csharp[c_collection_types_in_data_contracts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#2)]
[!code-vb[c_collection_types_in_data_contracts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#2)]

Podczas serializacji, otrzymany kod XML jest podobny do poniższego.

```xml
<CustomerList2>
    <string>...</string>
    <string>...</string>
    <string>...</string>
    ...
</CustomerList2>
```

Należy zauważyć, że nie jest to już odpowiednik reprezentacji XML dostosowanych typów.

- Możesz użyć `Name` właściwości i `Namespace` , aby bardziej dostosować nazwy. Zapoznaj się z następującą klasą.

  [!code-csharp[c_collection_types_in_data_contracts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#3)]
  [!code-vb[c_collection_types_in_data_contracts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#3)]

Otrzymany kod XML jest podobny do poniższego.

```xml
<cust_list>
    <string>...</string>
    <string>...</string>
    <string>...</string>
    ...
</cust_list>
```

Aby uzyskać więcej informacji, zobacz sekcję "Zaawansowane reguły kolekcji" w dalszej części tego tematu.

### <a name="customizing-the-repeating-element-name-in-list-collections"></a>Dostosowywanie powtarzającej się nazwy elementu w kolekcjach list

Kolekcje list zawierają powtarzające się wpisy. Zwykle każdy powtarzający wpis jest reprezentowany jako element o nazwie zgodnie z nazwą kontraktu danych typu zawartego w kolekcji.

`CustomerList` W przykładach kolekcje zawierały ciągi. Nazwa kontraktu danych dla typu pierwotnego ciągu to "String", więc powtarzalny element miał wartość "\<String >".

Jednak przy użyciu <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> właściwości <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu, ta powtarzająca się nazwa elementu można dostosować. Aby zapoznać się z przykładem, zobacz następujący typ.

[!code-csharp[c_collection_types_in_data_contracts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#4)]
[!code-vb[c_collection_types_in_data_contracts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#4)]

Otrzymany kod XML jest podobny do poniższego.

```xml
<CustomerList4>
    <customer>...</customer>
    <customer>...</customer>
    <customer>...</customer>
    ...
</CustomerList4>
```

Przestrzeń nazw powtarzającego się elementu jest zawsze taka sama jak przestrzeń nazw kontraktu danych kolekcji, którą można dostosować przy użyciu `Namespace` właściwości, jak opisano wcześniej.

### <a name="customizing-dictionary-collections"></a>Dostosowywanie kolekcji słowników

Kolekcje słownika są zasadniczo listami wpisów, w których każdy wpis ma klucz, po którym następuje wartość. Podobnie jak w przypadku zwykłych list, można zmienić nazwę elementu, który odnosi się do powtarzalnego elementu przy użyciu <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> właściwości.

Ponadto można zmienić nazwy elementów reprezentujące klucz i wartość przy użyciu <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> właściwości i. <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> Przestrzenie nazw dla tych elementów są takie same jak przestrzeń nazw kontraktu danych kolekcji.

Aby zapoznać się z przykładem, zobacz następujący typ.

[!code-csharp[c_collection_types_in_data_contracts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#5)]
[!code-vb[c_collection_types_in_data_contracts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#5)]

Podczas serializacji, otrzymany kod XML jest podobny do poniższego.

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

Aby uzyskać więcej informacji na temat kolekcji słowników, zobacz sekcję "Zaawansowane reguły kolekcji" w dalszej części tego tematu.

## <a name="collections-and-known-types"></a>Kolekcje i znane typy

Nie trzeba dodawać typów kolekcji do znanych typów, jeśli są używane w sposób polimorficzny zamiast innych kolekcji lub interfejsów kolekcji. Na przykład, Jeśli deklarujesz element członkowski danych typu <xref:System.Collections.IEnumerable> i użyjesz go do wysłania <xref:System.Collections.ArrayList>wystąpienia, nie musisz dodawać <xref:System.Collections.ArrayList> do znanych typów.

Jeśli kolekcje są używane w sposób polimorficzny zamiast typów niebędących kolekcjami, muszą być dodawane do znanych typów. Na przykład, Jeśli deklarujesz element członkowski danych typu `Object` i użyjesz go do wysłania <xref:System.Collections.ArrayList>wystąpienia, Dodaj <xref:System.Collections.ArrayList> do znanych typów.

Nie pozwala to na bardziej Serializowanie jakiejkolwiek równoważnej kolekcji. Na przykład po dodaniu <xref:System.Collections.ArrayList> do listy znanych typów w poprzednim przykładzie nie pozwala to `Array of Object` przypisać klasy, nawet jeśli ma ona odpowiedni kontrakt danych. Nie różni się to od regularnego znanego typu zachowania podczas serializacji dla typów niebędących kolekcjami, ale jest szczególnie ważne, aby zrozumieć w przypadku kolekcji, ponieważ bardzo często kolekcje są równoważne.

Podczas serializacji tylko jeden typ może być znany w danym zakresie dla danego kontraktu danych, a równoważne kolekcje mają te same umowy dotyczące danych. Oznacza to, że w poprzednim przykładzie nie można dodać jednocześnie <xref:System.Collections.ArrayList> i `Array of Object` do znanych typów w tym samym zakresie. Jest to równoznaczne z zachowaniem znanych typów dla typów niebędących kolekcjami, ale jest to szczególnie ważne, aby zrozumieć kolekcje.

Znane typy mogą być również wymagane w przypadku zawartości kolekcji. Na przykład, jeśli <xref:System.Collections.ArrayList> w rzeczywistości zawiera `Type1` wystąpienia i `Type2`, oba typy powinny zostać dodane do znanych typów.

Poniższy przykład pokazuje prawidłowo skonstruowany wykres obiektów przy użyciu kolekcji i znanych typów. Przykładem jest nieco contrived, ponieważ w rzeczywistej aplikacji zazwyczaj nie można definiować następujących składowych danych jako `Object`, i w związku z tym nie ma znanych problemów z typem/polimorfizmem.

[!code-csharp[c_collection_types_in_data_contracts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#6)]
[!code-vb[c_collection_types_in_data_contracts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#6)]

W przypadku deserializacji, jeśli zadeklarowany typ jest typem kolekcji, zadeklarowany typ jest tworzona niezależnie od typu, który faktycznie został wysłany. Jeśli zadeklarowany typ jest interfejsem kolekcji, Deserializator wybiera typ, który ma być skonkretyzowany, bez uwzględniania znanych typów.

Również podczas deserializacji, jeśli zadeklarowany typ nie jest typem kolekcji, ale jest wysyłany typ kolekcji, zgodny typ kolekcji jest wybierany z listy znanych typów. Można dodać typy interfejsów kolekcji do listy znanych typów podczas deserializacji. W takim przypadku aparat deserializacji ponownie wybiera typ do wystąpienia.

## <a name="collections-and-the-netdatacontractserializer-class"></a>Kolekcje i Klasa NetDataContractSerializer

Gdy Klasa jest używana, niedostosowane typy kolekcji ( <xref:System.Runtime.Serialization.CollectionDataContractAttribute> bez atrybutu), które nie są tablicami, tracą specjalne znaczenie. <xref:System.Runtime.Serialization.NetDataContractSerializer>

Niedostosowane <xref:System.SerializableAttribute> typy kolekcji oznaczone atrybutem mogą nadal być serializowane <xref:System.Runtime.Serialization.NetDataContractSerializer> przez <xref:System.SerializableAttribute> klasę zgodnie z atrybutem lub <xref:System.Runtime.Serialization.ISerializable> regułami interfejsu.

Niestandardowe typy kolekcji, interfejsy kolekcji i tablice są nadal traktowane jako kolekcje, nawet gdy <xref:System.Runtime.Serialization.NetDataContractSerializer> Klasa jest używana.

## <a name="collections-and-schema"></a>Kolekcje i schemat

Wszystkie równoważne kolekcje mają tę samą reprezentację w schemacie języka definicji schematu XML (XSD). W związku z tym zwykle nie uzyskujesz tego samego typu kolekcji w wygenerowanym kodzie klienta jako ten, który znajduje się na serwerze. Na przykład serwer może używać kontraktu danych z ogólnym <xref:System.Collections.Generic.List%601> elementem członkowskim danych Integer, ale w kodzie wygenerowanego klienta ten sam element członkowski danych może stać się tablicą liczb całkowitych.

Kolekcje słownika są oznaczone adnotacją schematu specyficzną dla programu WCF, która wskazuje, że są to słowniki; w przeciwnym razie są one nieodróżniane od prostych list zawierających wpisy z kluczem i wartością. Dokładny opis sposobu reprezentowania kolekcji w schemacie kontraktu danych znajduje się w temacie [Informacje o schemacie kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).

Domyślnie typy nie są generowane dla niedostosowywanych kolekcji w zaimportowanym kodzie. Elementy członkowskie danych typów kolekcji list są importowane jako tablice, a elementy członkowskie danych typów kolekcji słownika są importowane jako słownik ogólny.

Jednak w przypadku dostosowanych kolekcji są generowane oddzielne typy, które <xref:System.Runtime.Serialization.CollectionDataContractAttribute> są oznaczone atrybutem. (Dostosowany typ kolekcji w schemacie to taki, który nie używa domyślnej przestrzeni nazw, nazwy, powtarzającej się nazwy elementu ani nazw elementów klucza/wartości). Te typy są pustymi typami pochodnymi od <xref:System.Collections.Generic.List%601> generycznego dla typów list i słownika ogólnego dla typów słowników.

Na przykład na serwerze mogą znajdować się następujące typy.

[!code-csharp[c_collection_types_in_data_contracts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#7)]
[!code-vb[c_collection_types_in_data_contracts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#7)]

Gdy schemat zostanie wyeksportowany i ponownie zaimportowany, wygenerowany kod klienta jest podobny do poniższego (pola są wyświetlane, a nie właściwości do ułatwienia czytania).

[!code-csharp[c_collection_types_in_data_contracts#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#8)]
[!code-vb[c_collection_types_in_data_contracts#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#8)]

Możesz chcieć użyć różnych typów w wygenerowanym kodzie niż domyślne. Na przykład możesz chcieć użyć generycznych <xref:System.ComponentModel.BindingList%601> zamiast zwykłych tablic dla członków danych, aby ułatwić powiązanie ich ze składnikami interfejsu użytkownika.

Aby wybrać typy kolekcji do wygenerowania, należy przekazać listę typów kolekcji, które mają być używane we <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> właściwości <xref:System.Runtime.Serialization.ImportOptions> obiektu podczas importowania schematu. Te typy są nazywane *typem kolekcji, do których się odwołuje*.

Gdy istnieją odwołania do typów ogólnych, muszą one być w pełni otwarte ogólne lub w pełni zamknięte typy ogólne.

> [!NOTE]
> W przypadku korzystania z narzędzia Svcutil. exe to odwołanie można wykonać za pomocą przełącznika wiersza polecenia **/CollectionType** (krótka wersja: **/CT**). Należy pamiętać, że należy również określić zestaw dla typów kolekcji, do których istnieją odwołania, przy użyciu przełącznika **/Reference** (krótka wersja: **/r**). Jeśli typ jest rodzajowy, musi następować cudzysłów tylny oraz liczbę parametrów ogólnych. Cudzysłowu wstecznego\`() nie należy mylić z pojedynczym znakiem cudzysłowu ('). Można określić wiele typów kolekcji, do których istnieją odwołania, za pomocą przełącznika **/CollectionType** więcej niż jeden raz.

Na przykład, aby spowodować, że wszystkie listy zostaną zaimportowane <xref:System.Collections.Generic.List%601>jako ogólne.

```console
svcutil.exe MyService.wsdl MyServiceSchema.xsd /r:C:\full_path_to_system_dll\System.dll /ct:System.Collections.Generic.List`1
```

Podczas importowania kolekcji, ta lista typów kolekcji, do których się odwołuje, jest skanowana i jest używana Najlepsza, pasująca kolekcja, gdy zostanie znaleziona, jako typ elementu członkowskiego danych (dla niedostosowanych kolekcji) lub jako typ podstawowy, który ma być pochodny (dla dostosowanych kolekcji). Słowniki są dopasowywane tylko do słowników, a listy są dopasowywane do list.

Na przykład jeśli dodasz ogólny <xref:System.ComponentModel.BindingList%601> i <xref:System.Collections.Hashtable> do listy typów, których dotyczy odwołanie, wygenerowany kod klienta dla poprzedniego przykładu będzie podobny do poniższego.

[!code-csharp[c_collection_types_in_data_contracts#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#9)]
[!code-vb[c_collection_types_in_data_contracts#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#9)]

Można określić typy interfejsów kolekcji jako część typów kolekcji, do których istnieją odwołania, ale nie można określić nieprawidłowych typów kolekcji (takich jak `Add` te bez metody lub konstruktora publicznego).

Zamknięte ogólne jest uznawane za najlepsze dopasowanie. (Typy inne niż ogólne są uważane za równoważne zamkniętym rodzajom `Object`). Na przykład, jeśli typy <xref:System.Collections.Generic.List%601> ogólne of <xref:System.DateTime>, Generic <xref:System.ComponentModel.BindingList%601> (Open Generic) i <xref:System.Collections.ArrayList> są typami kolekcji, do których istnieją odwołania, generowane są następujące elementy:

[!code-csharp[c_collection_types_in_data_contracts#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#10)]
[!code-vb[c_collection_types_in_data_contracts#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#10)]

W przypadku kolekcji list są obsługiwane tylko przypadki z poniższej tabeli.

|Typ przywoływany|Interfejs zaimplementowany przez przywoływany typ|Przykład|Typ traktowany jako:|
|---------------------|----------------------------------------------|-------------|----------------------|
|Nieogólne lub zamknięte ogólne (dowolna liczba parametrów)|Nieogólny|`MyType : IList`<br /><br /> lub<br /><br /> `MyType<T> : IList`<br /><br /> gdzie T =`int`|Zamknięte ogólne z `Object` (na `IList<object>`przykład)|
|Nieogólne lub zamknięte ogólne (dowolna liczba parametrów, które nie muszą być zgodne z typem kolekcji)|Zamknięte ogólne|`MyType : IList<string>`<br /><br /> lub<br /><br /> `MyType<T> : IList<string>`gdzie T =`int`|Zamknięte ogólne (na przykład `IList<string>`)|
|Zamknięto ogólne z dowolną liczbą parametrów|Otwórz ogólny przy użyciu dowolnego z parametrów typu|`MyType<T,U,V> : IList<U>`<br /><br /> gdzie T =`int`, U =`string`, V =`bool`|Zamknięte ogólne (na przykład `IList<string>`)|
|Otwórz ogólny z jednym parametrem|Otwórz ogólne przy użyciu parametru typu|`MyType<T> : IList<T>`, T jest otwarty|Otwórz ogólne (na przykład `IList<T>`)|

Jeśli typ implementuje więcej niż jeden interfejs kolekcji list, mają zastosowanie następujące ograniczenia:

- Jeśli typ implementuje ogólne <xref:System.Collections.Generic.IEnumerable%601> (lub jego interfejsy pochodne) wiele razy dla różnych typów, typ nie jest uważany za prawidłowy typ kolekcji, do której się odwołuje, i jest ignorowany. Jest to prawdziwe, nawet jeśli niektóre implementacje są nieprawidłowe lub używają otwartych typów ogólnych. Na przykład typ, który implementuje ogólne <xref:System.Collections.Generic.IEnumerable%601> of `int` i Generic <xref:System.Collections.Generic.IEnumerable%601> of T, `int` nigdy nie będzie używany jako kolekcja, do której się odwołuje, lub `Add` inny typ, niezależnie od tego, czy typ ma metodę akceptującą `int` lub MetodaakceptującaparametrtypuTlub`Add` oba te elementy.

- Jeśli typ implementuje interfejs kolekcji ogólnej <xref:System.Collections.IList>, a także, typ nie jest nigdy używany jako przywoływany typ kolekcji, chyba że ogólny interfejs kolekcji jest zamkniętym rodzajem typu. <xref:System.Object>

W przypadku kolekcji słownika są obsługiwane tylko przypadki z poniższej tabeli.

|Typ przywoływany|Interfejs zaimplementowany przez przywoływany typ|Przykład|Typ traktowany jako|
|---------------------|----------------------------------------------|-------------|---------------------|
|Nieogólne lub zamknięte ogólne (dowolna liczba parametrów)|<xref:System.Collections.IDictionary>|`MyType : IDictionary`<br /><br /> lub<br /><br /> `MyType<T> : IDictionary`gdzie T =`int`|Zamknięte ogólne`IDictionary<object,object>`|
|Zamknięte ogólne (dowolna liczba parametrów)|<xref:System.Collections.Generic.IDictionary%602>, zamknięte|`MyType<T> : IDictionary<string, bool>`gdzie T =`int`|Zamknięte ogólne (na przykład `IDIctionary<string,bool>`)|
|Zamknięte ogólne (dowolna liczba parametrów)|Ogólny <xref:System.Collections.Generic.IDictionary%602>, jeden z kluczy lub wartości jest zamknięty, drugi jest otwarty i używa jednego z parametrów typu|`MyType<T,U,V> : IDictionary<string,V>`gdzie T =`int`, U =`float`, V =`bool`<br /><br /> lub<br /><br /> `MyType<Z> : IDictionary<Z,bool>`gdzie Z =`string`|Zamknięte ogólne (na przykład `IDictionary<string,bool>`)|
|Zamknięte ogólne (dowolna liczba parametrów)|Ogólny <xref:System.Collections.Generic.IDictionary%602>, zarówno klucz, jak i wartość są otwarte, a każdy z nich używa jednego z parametrów typu|`MyType<T,U,V> : IDictionary<V,U>`gdzie T =`int`, U =`bool`, V =`string`|Zamknięte ogólne (na przykład `IDictionary<string,bool>`)|
|Otwórz ogólne (dwa parametry)|Ogólne <xref:System.Collections.Generic.IDictionary%602>, otwarte, używa obu parametrów ogólnych typu w kolejności, w jakiej występują|`MyType<K,V> : IDictionary<K,V>`, K i V — otwarte|Otwórz ogólne (na przykład `IDictionary<K,V>`)|

Jeśli typ implementuje zarówno <xref:System.Collections.IDictionary> , jak i rodzajowy <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.IDictionary%602> tylko ogólny jest brany pod uwagę.

Odwołania do częściowych typów ogólnych nie są obsługiwane.

Duplikaty są <xref:System.Collections.Generic.List%601> niedozwolone, na przykład nie można dodać obu rodzajowych `Integer` `Integer` i ogólnych kolekcji do <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, ponieważ uniemożliwia to ustalenie, która z nich ma być używana w przypadku znalezienia listy liczb całkowitych w schemacie. Duplikaty są wykrywane tylko wtedy, gdy w schemacie znajduje się typ, który ujawnia problem z duplikatami. Na przykład, Jeśli importowany schemat nie zawiera listy <xref:System.Collections.Generic.List%601> liczb całkowitych, może istnieć zarówno ogólny `Integer` element, `Integer` jak i <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>Ogólna kolekcja w, ale nie ma żadnego efektu.

## <a name="advanced-collection-rules"></a>Zaawansowane reguły zbierania

### <a name="serializing-collections"></a>Serializacja kolekcji

Poniżej znajduje się lista reguł kolekcji dla serializacji:

- Łączenie typów kolekcji (z kolekcjami kolekcji) jest dozwolone. Tablice nieregularne są traktowane jako kolekcje kolekcji. Tablice wielowymiarowe nie są obsługiwane.

- Tablice bajtów i tablic <xref:System.Xml.XmlNode> są specjalnymi typami tablic, które są traktowane jako elementy pierwotne, a nie kolekcje. Serializacja tablicy bajtów skutkuje pojedynczym elementem XML zawierającym fragment danych zakodowanych algorytmem Base64 zamiast oddzielnego elementu dla każdego bajtu. Aby uzyskać więcej informacji o sposobie traktowania <xref:System.Xml.XmlNode> tablicy, zobacz [Typy XML i ADO.NET w umowach dotyczących danych](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md). Oczywiście te typy specjalne mogą się znajdować w kolekcjach: tablica tablicy Byte powoduje wiele elementów XML, z których każdy zawiera fragment danych zakodowanych algorytmem Base64.

- <xref:System.Runtime.Serialization.DataContractAttribute> Jeśli atrybut jest stosowany do typu kolekcji, typ jest traktowany jako zwykły typ kontraktu danych, a nie jako kolekcja.

- Jeśli typ kolekcji implementuje <xref:System.Xml.Serialization.IXmlSerializable> interfejs, mają zastosowanie `myType:IList<string>, IXmlSerializable`następujące reguły:

  - Jeśli zadeklarowany typ to `IList<string>`, typ jest serializowany jako listę.

  - Jeśli zadeklarowany typ to `myType`, jest serializowany jako `IXmlSerializable`.

  - Jeśli zadeklarowany typ to `IXmlSerializable`, jest serializowany jako `IXmlSerializable`, ale tylko wtedy, gdy `myType` dodasz do listy znanych typów.

- Kolekcje są serializowane i deserializowane przy użyciu metod przedstawionych w poniższej tabeli.

|Implementacja typu kolekcji|Metody wywoływane podczas serializacji|Metody wywoływane podczas deserializacji|
|--------------------------------|-----------------------------------------|-------------------------------------------|
|Ogólnego<xref:System.Collections.Generic.IDictionary%602>|`get_Keys`, `get_Values`|Dodawanie ogólne|
|<xref:System.Collections.IDictionary>|`get_Keys`, `get_Values`|`Add`|
|Ogólnego<xref:System.Collections.Generic.IList%601>|Indeksator <xref:System.Collections.Generic.IList%601> ogólny|Dodawanie ogólne|
|Ogólnego<xref:System.Collections.Generic.ICollection%601>|Liczeni|Dodawanie ogólne|
|<xref:System.Collections.IList>|<xref:System.Collections.IList>Indeksatora|`Add`|
|Ogólnego<xref:System.Collections.Generic.IEnumerable%601>|`GetEnumerator`|Metoda niestatyczna wywołana `Add` , która przyjmuje jeden parametr odpowiedniego typu (typ parametru generycznego lub jeden z jego typów podstawowych). Taka metoda musi istnieć, aby serializator traktował typ kolekcji jako kolekcję podczas serializacji i deserializacji.|
|<xref:System.Collections.IEnumerable>(i w <xref:System.Collections.ICollection>ten sposób, który od niego pochodzi)|`GetEnumerator`|Metoda niestatyczna o nazwie `Add` , która przyjmuje jeden parametr typu `Object`. Taka metoda musi istnieć, aby serializator traktował typ kolekcji jako kolekcję podczas serializacji i deserializacji.|

Powyższa tabela zawiera listę interfejsów kolekcji w kolejności malejącej. Oznacza to, na przykład, że jeśli typ implementuje obie <xref:System.Collections.IList> i ogólne <xref:System.Collections.Generic.IEnumerable%601>, kolekcja jest serializowana i deserializowana zgodnie <xref:System.Collections.IList> z regułami:

- Podczas deserializacji wszystkie kolekcje są deserializowane przez utworzenie wystąpienia typu przez wywołanie konstruktora bez parametrów, który musi być obecny, aby serializator traktował typ kolekcji jako kolekcję podczas serializacji i deserializacji.

- Jeśli ten sam interfejs kolekcji ogólnej jest zaimplementowany więcej niż raz (na przykład jeśli <xref:System.Collections.Generic.ICollection%601> typ implementuje zarówno rodzajowy `Integer` , jak i <xref:System.String>ogólny <xref:System.Collections.Generic.ICollection%601> ) i nie zostanie znaleziony żaden interfejs o wyższym priorytecie, kolekcja jest nie jest traktowana jako prawidłowa kolekcja.

- Do typów kolekcji można <xref:System.SerializableAttribute> zastosować atrybut i można <xref:System.Runtime.Serialization.ISerializable> zaimplementować interfejs. Oba te elementy są ignorowane. Jeśli jednak typ nie spełnia wymagań dotyczących typu kolekcji (na przykład w `Add` przypadku braku metody), typ nie jest uważany za typ kolekcji i w <xref:System.SerializableAttribute> ten sposób atrybut i <xref:System.Runtime.Serialization.ISerializable> interfejs są używane do określania Określa, czy typ może być serializowany.

- Zastosowanie atrybutu do kolekcji w celu jego dostosowania <xref:System.SerializableAttribute> spowoduje usunięcie poprzedniego mechanizmu powrotu. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Zamiast tego, jeśli dostosowana kolekcja nie spełnia wymagań dotyczących typu kolekcji, <xref:System.Runtime.Serialization.InvalidDataContractException> zgłaszany jest wyjątek. Ciąg wyjątku często zawiera informacje wyjaśniające, dlaczego dany typ nie jest traktowany jako prawidłowa kolekcja (brak `Add` metody, brak konstruktora bez parametrów itd.), więc często warto <xref:System.Runtime.Serialization.CollectionDataContractAttribute> zastosować atrybut do debugowania płatnicz.

### <a name="collection-naming"></a>Nazewnictwo kolekcji

Poniżej znajduje się lista reguł nazewnictwa kolekcji:

- Domyślna przestrzeń nazw dla wszystkich kontraktów danych kolekcji słowników, a także dla kontraktów danych kolekcji list zawierających typy pierwotne `http://schemas.microsoft.com/2003/10/Serialization/Arrays` , jest chyba że zostanie zastąpiona przy użyciu przestrzeni nazw. Typy mapowane na wbudowane typy XSD, a także `char`, `Timespan`i `Guid` , są uznawane za elementy pierwotne w tym celu.

- Domyślna przestrzeń nazw dla typów kolekcji, które zawierają typy niepierwotne, chyba że zostanie zastąpiona przy użyciu przestrzeni nazw, jest taka sama jak przestrzeń nazw kontraktu danych typu zawartego w kolekcji.

- Nazwa domyślna dla kontraktów danych kolekcji list, chyba że zostanie zastąpiona przy użyciu nazwy, jest ciągiem "ArrayOf", połączonym z nazwą kontraktu danych typu zawartego w kolekcji. Na przykład nazwa kontraktu danych dla ogólnej listy liczb całkowitych to "ArrayOfint". Pamiętaj, że nazwa `Object` kontraktu danych to "anyType", więc nazwa kontraktu danych nieogólnych list, takich jak <xref:System.Collections.ArrayList> "ArrayOfanyType".

Nazwa domyślna dla kontraktów danych kolekcji słowników, chyba że `Name`jest zastępowana przy użyciu, jest ciągiem "ArrayOfKeyValueOf", połączonym z nazwą kontraktu danych typu klucza, po którym następuje nazwa kontraktu danych typu wartości. Na przykład nazwa kontraktu danych dla słownika generycznego String i Integer to "ArrayOfKeyValueOfstringint". Ponadto jeśli klucz lub typy wartości nie są typami pierwotnymi, skrót przestrzeni nazw obszaru nazw kontraktu danych klucza i wartości jest dołączany do nazwy. Aby uzyskać więcej informacji na temat skrótów przestrzeni nazw, zobacz [nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md).

Każdy kontrakt danych kolekcji słowników ma kontrakt danych pomocnika, który reprezentuje jeden wpis w słowniku. Jego nazwa jest taka sama jak dla kontraktu danych słownika, z wyjątkiem prefiksu "ArrayOf", a jego przestrzeń nazw jest taka sama jak dla kontraktu danych słownika. Na przykład dla kontraktu danych słownika "ArrayOfKeyValueOfstringint" kontrakt danych "KeyValueofstringint" reprezentuje jeden wpis w słowniku. Nazwę tego kontraktu danych można dostosować przy użyciu `ItemName` właściwości, zgodnie z opisem w następnej sekcji.

Reguły nazewnictwa typów ogólnych, zgodnie z opisem w [nazwach kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md), w pełni stosowane do typów kolekcji; oznacza to, że można użyć nawiasów klamrowych w nazwie do wskazania parametrów typu ogólnego. Jednakże liczby w nawiasach klamrowych odnoszą się do parametrów ogólnych, a nie typów zawartych w kolekcji.

## <a name="collection-customization"></a>Dostosowanie kolekcji

Następujące zastosowania <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu są zabronione i powodują <xref:System.Runtime.Serialization.InvalidDataContractException> wyjątek:

- Zastosowanie atrybutu do typu, do <xref:System.Runtime.Serialization.CollectionDataContractAttribute> którego zastosowano atrybut, lub do jednego z jego typów pochodnych. <xref:System.Runtime.Serialization.DataContractAttribute>

- Stosowanie atrybutu do typu, który <xref:System.Xml.Serialization.IXmlSerializable> implementuje interfejs. <xref:System.Runtime.Serialization.CollectionDataContractAttribute>

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Stosowanie atrybutu do typu niebędącego kolekcją.

- Podjęto próbę <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> ustawienia <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> lub <xref:System.Runtime.Serialization.CollectionDataContractAttribute> zastosowania atrybutu do typu innego niż słownik.

### <a name="polymorphism-rules"></a>Reguły polimorfizmu

Jak wspomniano wcześniej, dostosowanie kolekcji przy użyciu <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atrybutu może zakłócać możliwość zmiany kolekcji. Dwa niestandardowe typy kolekcji mogą być uważane za równoważne tylko wtedy, gdy ich nazwy, przestrzeń nazw, nazwa elementu, a także nazwy kluczy i wartości (jeśli są to kolekcje słownika), są zgodne.

Ze względu na dostosowania można przypadkowo użyć jednego kontraktu danych kolekcji, w którym jest oczekiwany inny. Należy to uniknąć. Zobacz następujące typy.

[!code-csharp[c_collection_types_in_data_contracts#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#11)]
[!code-vb[c_collection_types_in_data_contracts#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#11)]

W takim przypadku wystąpienie `Marks1` może być przypisane do. `testMarks` Nie należy `Marks2` jednak używać, ponieważ jego kontrakt danych nie jest uważany za odpowiednik `IList<int>` kontraktu danych. Nazwa kontraktu danych to "Marks2", a nie "ArrayOfint", a powtarzająca się nazwa elementu to\<"Mark >", a\<nie "int >".

Reguły w poniższej tabeli dotyczą przypisywania polimorficznych kolekcji.

|Zadeklarowany typ|Przypisywanie niedostosowanej kolekcji|Przypisywanie dostosowanej kolekcji|
|-------------------|--------------------------------------------|---------------------------------------|
|Obiekt|Nazwa kontraktu jest serializowana.|Nazwa kontraktu jest serializowana.<br /><br /> Użycie dostosowania.|
|Interfejs kolekcji|Nazwa kontraktu nie jest serializowana.|Nazwa kontraktu nie jest serializowana.<br /><br /> Dostosowywanie nie jest używane.\*|
|Dostosowana kolekcja|Nazwa kontraktu nie jest serializowana.|Nazwa kontraktu jest serializowana.<br /><br /> Użyto dostosowania. * *|
|Dostosowana kolekcja|Nazwa kontraktu jest serializowana. Dostosowywanie nie jest używane.\*\*|Nazwa kontraktu jest serializowana.<br /><br /> Używane jest dostosowanie przypisanego typu.\*\*|

\*W przypadku <xref:System.Runtime.Serialization.NetDataContractSerializer> klasy dostosowanie jest używane w tym przypadku. <xref:System.Runtime.Serialization.NetDataContractSerializer> Klasa również serializacji rzeczywistej nazwy typu w tym przypadku, dlatego deserializacja działa zgodnie z oczekiwaniami.

\*\*Te przypadki powodują wystąpienie nieprawidłowych wystąpień schematu i dlatego należy je unikać.

W przypadkach, gdy nazwa kontraktu jest serializowana, przypisany typ kolekcji powinien znajdować się na liście znanych typów. Przeciwieństwo również jest prawdziwe: w przypadkach, gdy nazwa nie jest serializowana, dodanie typu do listy znanych typów nie jest wymagane.

Tablica typu pochodnego może być przypisana do tablicy typu podstawowego. W takim przypadku nazwa kontraktu dla typu pochodnego jest serializowana dla każdego powtarzanego elementu. Na `Book` przykład, jeśli typ pochodzi od typu `LibraryItem`, można przypisać tablicę `Book` do tablicy `LibraryItem`. Nie dotyczy to innych typów kolekcji. Na przykład nie można przypisać `Generic List of Book` do elementu. `Generic List of LibraryItem` Można jednak przypisać obiekt `Generic List of LibraryItem` `Book` zawierający wystąpienia. Zarówno w tablicy, jak i w przypadku nietablicowym `Book` , powinny znajdować się na liście znanych typów.

## <a name="collections-and-object-reference-preservation"></a>Przechowywanie kolekcji i odwołań do obiektów

Gdy serializator działa w trybie, w którym zachowuje odwołania do obiektów, zachowywanie odwołań do obiektów ma zastosowanie również do kolekcji. W konkretnym przypadku tożsamość obiektu jest zachowywana dla całej kolekcji i poszczególnych elementów zawartych w kolekcjach. W przypadku słowników tożsamość obiektu jest zachowywana zarówno dla obiektów pary klucz/wartość, jak i poszczególnych obiektów klucza i wartości.

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>

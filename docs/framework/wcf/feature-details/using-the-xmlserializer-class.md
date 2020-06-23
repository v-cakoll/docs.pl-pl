---
title: Używanie klasy XmlSerializer
description: Dowiedz się więcej o elemencie XmlSerializer, który jest używany przez usługę WCF do serializacji danych w aplikacji do formatu XML, który jest przesyłany między klientami i usługami.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XmlSerializer [WCF], using
ms.assetid: c680602d-39d3-44f1-bf22-8e6654ad5069
ms.openlocfilehash: f7473de3f34ba543b4fabfe93167ea267f16dda5
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246388"
---
# <a name="using-the-xmlserializer-class"></a>Używanie klasy XmlSerializer

Windows Communication Foundation (WCF) może korzystać z dwóch różnych technologii serializacji, aby przekształcić dane w aplikacji do formatu XML, który jest przesyłany między klientami i usługami, proces nazywany serializacji.

## <a name="datacontractserializer-as-the-default"></a>Obiekt DataContractSerializer jako domyślny

Domyślnie WCF używa <xref:System.Runtime.Serialization.DataContractSerializer> klasy do serializacji typów danych. Ten serializator obsługuje następujące typy:

- Typy pierwotne (na przykład liczby całkowite, ciągi i tablice bajtowe), a także typy specjalne, takie jak <xref:System.Xml.XmlElement> i <xref:System.DateTime> , które są traktowane jako elementy pierwotne.

- Typy kontraktów danych (typy oznaczone <xref:System.Runtime.Serialization.DataContractAttribute> atrybutem).

- Typy oznaczone <xref:System.SerializableAttribute> atrybutem, które obejmują typy implementujące <xref:System.Runtime.Serialization.ISerializable> interfejs.

- Typy, które implementują <xref:System.Xml.Serialization.IXmlSerializable> interfejs.

- Wiele popularnych typów kolekcji, które obejmują wiele rodzajowych typów kolekcji.

Wiele typów .NET Framework należy do tych dwóch kategorii i są w ten sposób serializowane. Tablice typów możliwych do serializacji są również serializowane. Aby uzyskać pełną listę, zobacz [określanie transfer danych w kontraktach usług](specifying-data-transfer-in-service-contracts.md).

<xref:System.Runtime.Serialization.DataContractSerializer>Program, używany razem z typami kontraktu danych, jest zalecanym sposobem pisania nowych usług WCF. Aby uzyskać więcej informacji, zobacz [Korzystanie z kontraktów danych](using-data-contracts.md).

## <a name="when-to-use-the-xmlserializer-class"></a>Kiedy używać klasy XmlSerializer

Funkcja WCF obsługuje również <xref:System.Xml.Serialization.XmlSerializer> klasę. <xref:System.Xml.Serialization.XmlSerializer>Klasa nie jest unikatowa dla WCF. Jest to ten sam aparat serializacji, który jest używany przez usługi sieci Web ASP.NET. <xref:System.Xml.Serialization.XmlSerializer>Klasa obsługuje wiele węższego zestawu typów niż <xref:System.Runtime.Serialization.DataContractSerializer> Klasa, ale zapewnia znacznie większą kontrolę nad wynikiem XML i obsługuje znacznie większą ilość języka definicji schematu XML (XSD). Nie wymaga również żadnych atrybutów deklaratywnych dla typów możliwych do serializacji. Aby uzyskać więcej informacji, zobacz temat serializacji XML w dokumentacji .NET Framework. <xref:System.Xml.Serialization.XmlSerializer>Klasa nie obsługuje typów kontraktu danych.

W przypadku używania Svcutil.exe lub funkcji **Dodaj odwołanie do usługi** w programie Visual Studio do generowania kodu klienta dla usługi innej firmy lub do uzyskiwania dostępu do schematu innej firmy zostanie automatycznie wybrany odpowiedni serializator. Jeśli schemat nie jest zgodny z <xref:System.Runtime.Serialization.DataContractSerializer> , <xref:System.Xml.Serialization.XmlSerializer> jest zaznaczone.

## <a name="manually-switching-to-the-xmlserializer"></a>Ręczne przełączanie do elementu XmlSerializer

Czasami może być konieczne ręczne przełączenie na <xref:System.Xml.Serialization.XmlSerializer> . Dzieje się tak na przykład w następujących przypadkach:

- Podczas migrowania aplikacji z usług sieci Web ASP.NET do platformy WCF możesz chcieć ponownie wykorzystać istniejące, <xref:System.Xml.Serialization.XmlSerializer> zgodne typy, zamiast tworzyć nowe typy kontraktów danych.

- Gdy dokładna kontrola nad kodem XML, który pojawia się w komunikatach jest ważna, ale dokument Web Services Description Language (WSDL) nie jest dostępny, na przykład podczas tworzenia usługi z typami, które muszą być zgodne z określonym standardowym, publikowanym schematem, który nie jest zgodny z obiektem DataContractSerializer.

- Podczas tworzenia usług, które są zgodne ze starszym standardem kodowania SOAP.

W tych i innych przypadkach można ręcznie przełączyć się do <xref:System.Xml.Serialization.XmlSerializer> klasy przez zastosowanie `XmlSerializerFormatAttribute` atrybutu do usługi, jak pokazano w poniższym kodzie.

[!code-csharp[c_XmlSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#1)]
[!code-vb[c_XmlSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#1)]

## <a name="security-considerations"></a>Zagadnienia związane z zabezpieczeniami

> [!NOTE]
> Należy zachować ostrożność podczas przełączania aparatów serializacji. Ten sam typ można serializować do kodu XML inaczej w zależności od używanego serializatora. Jeśli przypadkowo używasz niewłaściwego serializatora, możesz wypróbować informacje z typu, który nie miał być ujawniany.

Na przykład <xref:System.Runtime.Serialization.DataContractSerializer> Klasa serializować tylko elementy członkowskie oznaczone <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutem podczas serializacji typów kontraktu danych. <xref:System.Xml.Serialization.XmlSerializer>Klasa serializować każdy publiczny element członkowski. Zobacz typ w poniższym kodzie.

[!code-csharp[c_XmlSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#2)]
[!code-vb[c_XmlSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#2)]

Jeśli typ jest nieumyślnie używany w kontrakcie usługi, w którym <xref:System.Xml.Serialization.XmlSerializer> została wybrana Klasa, `creditCardNumber` element członkowski jest serializowany, co jest prawdopodobnie nieprzewidziane.

Mimo że <xref:System.Runtime.Serialization.DataContractSerializer> Klasa jest wartością domyślną, można ją jawnie wybrać dla usługi (mimo że nie powinna być nigdy wymagana) przez zastosowanie <xref:System.ServiceModel.DataContractFormatAttribute> atrybutu do typu kontraktu usługi.

Serializator używany dla usługi jest integralną częścią kontraktu i nie można go zmienić, wybierając inne powiązanie lub zmieniając inne ustawienia konfiguracji.

Inne ważne zagadnienia dotyczące zabezpieczeń dotyczą <xref:System.Xml.Serialization.XmlSerializer> klasy. Najpierw zdecydowanie zaleca się, aby każda aplikacja WCF, która używa <xref:System.Xml.Serialization.XmlSerializer> klasy, była podpisana przy użyciu klucza zabezpieczającego przed ujawnieniem. To zalecenie ma zastosowanie w przypadku, gdy przełącznik ręczny <xref:System.Xml.Serialization.XmlSerializer> jest wykonywany i gdy jest wykonywane automatyczne przełączanie (za pomocą Svcutil.exe, Dodaj odwołanie do usługi lub podobnego narzędzia). Jest to spowodowane tym, że <xref:System.Xml.Serialization.XmlSerializer> aparat serializacji obsługuje ładowanie *wstępnie wygenerowanych zestawów serializacji* , o ile są podpisane przy użyciu tego samego klucza co aplikacja. Nieniepodpisana aplikacja jest całkowicie niechroniona przed możliwością złośliwego zestawu zgodnego z oczekiwaną nazwą wstępnie wygenerowanego zestawu serializacji umieszczanego w folderze aplikacji lub w globalnej pamięci podręcznej zestawów. Oczywiście osoba atakująca musi najpierw uzyskać dostęp do zapisu do jednej z tych dwóch lokalizacji, aby podjąć próbę wykonania tej akcji.

Inne zagrożenie, które istnieje za każdym razem, <xref:System.Xml.Serialization.XmlSerializer> jest powiązane z dostępem do zapisu do tymczasowego folderu systemowego. <xref:System.Xml.Serialization.XmlSerializer>Aparat serializacji tworzy i używa tymczasowych *zestawów serializacji* w tym folderze. Należy pamiętać, że każdy proces z dostępem do zapisu do folderu tymczasowego może zastąpić te zestawy serializacji złośliwym kodem.

## <a name="rules-for-xmlserializer-support"></a>Reguły dla obsługi XmlSerializer

Nie można bezpośrednio zastosować <xref:System.Xml.Serialization.XmlSerializer> atrybutów zgodnych z parametrami operacji kontraktu lub zwracanymi wartościami. Można je jednak stosować do komunikatów o określonym typie (części treści kontraktu wiadomości), jak pokazano w poniższym kodzie.

[!code-csharp[c_XmlSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#3)]
[!code-vb[c_XmlSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#3)]

Po zastosowaniu do elementów członkowskich wiadomości, te atrybuty zastępują właściwości w konflikcie względem wpisanych atrybutów wiadomości. Na przykład, w poniższym kodzie, `ElementName` zastępuje `Name` .

[!code-csharp[c_XmlSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#4)]
[!code-vb[c_XmlSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#4)]

<xref:System.ServiceModel.MessageHeaderArrayAttribute>Atrybut nie jest obsługiwany w przypadku korzystania z <xref:System.Xml.Serialization.XmlSerializer> .

> [!NOTE]
> W takim przypadku <xref:System.Xml.Serialization.XmlSerializer> zgłasza następujący wyjątek, który jest wydawany przed WCF: "element zadeklarowany na najwyższym poziomie schematu nie może mieć `maxOccurs` > 1. Podaj element otoki dla "więcej" przy użyciu `XmlArray` lub `XmlArrayItem` zamiast `XmlElementAttribute` lub przy użyciu stylu parametru opakowanego ".
>
> Jeśli zostanie wyświetlony taki wyjątek, sprawdź, czy ta sytuacja dotyczy.

Funkcja WCF nie obsługuje <xref:System.Xml.Serialization.SoapIncludeAttribute> atrybutów i <xref:System.Xml.Serialization.XmlIncludeAttribute> w kontraktach komunikatów i kontraktach operacji; <xref:System.Runtime.Serialization.KnownTypeAttribute> zamiast tego użyj atrybutu.

## <a name="types-that-implement-the-ixmlserializable-interface"></a>Typy implementujące interfejs IXmlSerializable

Typy implementujące `IXmlSerializable` interfejs są w pełni obsługiwane przez `DataContractSerializer` . Ten <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybut powinien być zawsze stosowany do tych typów w celu sterowania ich schematem.

> [!WARNING]
> W przypadku serializowania typów polimorficznych należy zastosować <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> do typu, aby upewnić się, że prawidłowy typ jest serializowany.

Istnieją trzy różne typy, które implementują `IXmlSerializable` : typy reprezentujące dowolną zawartość, typy reprezentujące pojedynczy element oraz starsze <xref:System.Data.DataSet> typy.

- Typy zawartości używają metody dostawcy schematu określonej przez `XmlSchemaProviderAttribute` atrybut. Metoda nie zwraca `null` i <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> Właściwość w atrybucie ma wartość domyślną `false` . Jest to najbardziej typowe użycie `IXmlSerializable` typów.

- Typy elementów są używane, gdy `IXmlSerializable` Typ musi kontrolować własną nazwę elementu głównego. Aby oznaczyć typ jako typ elementu, ustaw <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> Właściwość <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybutu na `true` lub Return `null` z metody dostawcy schematu. Posiadanie metody dostawcy schematu jest opcjonalne dla typów elementów — możesz określić `null` zamiast nazwy metody w `XmlSchemaProviderAttribute` . Jednakże jeśli `IsAny` jest `true` i określono metodę dostawcy schematu, metoda musi zwracać `null` .

- Starsze <xref:System.Data.DataSet> typy to `IXmlSerializable` typy, które nie są oznaczone `XmlSchemaProviderAttribute` atrybutem. Zamiast tego korzystają one z <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> metody generowania schematu. Ten wzorzec jest używany dla `DataSet` typu i jego typ DataSet jest klasą we wcześniejszych wersjach .NET Framework, ale jest już przestarzały i jest obsługiwany tylko w przypadku starszych przyczyn. Nie należy polegać na tym wzorcu i zawsze stosować `XmlSchemaProviderAttribute` do Twoich `IXmlSerializable` typów.

### <a name="ixmlserializable-content-types"></a>Typy zawartości interfejsu IXmlSerializable

Podczas serializacji elementu członkowskiego danych typu, który implementuje `IXmlSerializable` i jest typem zawartości zdefiniowanym wcześniej, serializator zapisuje element otoki dla elementu członkowskiego danych i przekazuje kontrolę do <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>Implementacja może napisać dowolny kod XML, który obejmuje Dodawanie atrybutów do elementu otoki. Po zakończeniu `WriteXml` serializator zamknie element.

Podczas deserializacji elementu członkowskiego typu, który implementuje `IXmlSerializable` i jest typem zawartości, zgodnie z definicją wcześniej, Deserializator umieszcza obiekt odczytujący XML na elemencie otoki dla elementu członkowskiego danych i przekazuje kontrolę do <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metody. Metoda musi odczytywać cały element, łącznie ze znacznikiem początkowym i końcowym. Upewnij się `ReadXml` , że kod obsługuje przypadek, w którym element jest pusty. Ponadto `ReadXml` implementacja nie powinna opierać się na elemencie otoki o nazwie w określony sposób. Nazwa jest wybierana przez serializator może się różnić.

Istnieje możliwość przypisywania `IXmlSerializable` typów zawartości polimorficznie, na przykład do składowych danych typu <xref:System.Object> . Dozwolone jest również, aby wystąpienia typu miały wartość null. Na koniec można używać `IXmlSerializable` typów z włączoną funkcją zachowywania grafów obiektów i z <xref:System.Runtime.Serialization.NetDataContractSerializer> . Wszystkie te funkcje wymagają, aby serializator WCF dołączył pewne atrybuty do elementu otoki ("Nil" i "Type" w przestrzeni nazw wystąpienia schematu XML i "ID", "ref", "Type" i "Assembly" w przestrzeni nazw specyficznej dla programu WCF).

#### <a name="attributes-to-ignore-when-implementing-readxml"></a>Atrybuty do ignorowania podczas implementowania ReadXml

Przed przekazaniem kontroli do `ReadXml` kodu, Deserializator sprawdza element XML, wykrywa te specjalne atrybuty XML i wykonuje na nich działania. Na przykład jeśli "Nil" ma `true` wartość null, zostanie przeprowadzona deserializacja i `ReadXml` nie zostanie wywołana. W przypadku wykrycia polimorfizmu zawartość elementu jest deserializowana tak, jakby była innego typu. Implementacja typu "jest przypisana polimorficzna" `ReadXml` jest wywoływana. W każdym przypadku `ReadXml` implementacja powinna ignorować te atrybuty specjalne, ponieważ są one obsługiwane przez Deserializator.

### <a name="schema-considerations-for-ixmlserializable-content-types"></a>Zagadnienia dotyczące schematu dla typów zawartości interfejsu IXmlSerializable

Podczas eksportowania schematu i `IXmlSerializable` typu zawartości wywoływana jest metoda dostawcy schematu. <xref:System.Xml.Schema.XmlSchemaSet>Do metody dostawcy schematu jest przenoszona wartość. Metoda może dodać dowolny prawidłowy schemat do zestawu schematów. Zestaw schematu zawiera schemat, który jest już znany w chwili, gdy następuje eksport schematu. Gdy metoda dostawcy schematu musi dodać element do zestawu schematów, musi określić, czy <xref:System.Xml.Schema.XmlSchema> z odpowiednią przestrzenią nazw już istnieje w zestawie. Jeśli tak, Metoda dostawcy schematu musi dodać nowy element do istniejącego `XmlSchema` . W przeciwnym razie musi utworzyć nowe `XmlSchema` wystąpienie. Jest to ważne, jeśli tablice `IXmlSerializable` typów są używane. Na przykład, jeśli masz `IXmlSerializable` Typ, który zostanie wyeksportowany jako typ "A" w przestrzeni nazw "b", możliwe jest, że przez czas, gdy metoda dostawcy schematu jest wywoływana, zestaw schematu zawiera już schemat dla "B" w celu przechowywania typu "ArrayOfA".

Oprócz dodawania typów do <xref:System.Xml.Schema.XmlSchemaSet> , Metoda dostawcy schematu dla typów zawartości musi zwracać wartość różną od null. Może zwrócić element <xref:System.Xml.XmlQualifiedName> , który określa nazwę typu schematu do użycia dla danego `IXmlSerializable` typu. Ta kwalifikowana nazwa służy również jako nazwa kontraktu danych i przestrzeń nazw dla typu. Może zwrócić typ, który nie istnieje w zestawie schematu zaraz po powrocie metody dostawcy schematu. Jednak oczekuje się, że przez cały czas są eksportowane wszystkie powiązane typy ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> Metoda jest wywoływana dla wszystkich odpowiednich typów w <xref:System.Runtime.Serialization.XsdDataContractExporter> i <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> Właściwość jest dostępna), typ istnieje w zestawie schematów. Uzyskanie dostępu do `Schemas` Właściwości przed wykonaniem wszystkich odpowiednich `Export` wywołań może spowodować wystąpienie <xref:System.Xml.Schema.XmlSchemaException> . Aby uzyskać więcej informacji na temat procesu eksportowania, zobacz [Eksportowanie schematów z klas](exporting-schemas-from-classes.md).

Metoda dostawcy schematu może również zwrócić <xref:System.Xml.Schema.XmlSchemaType> do użycia. Typ może lub nie być anonimowy. Jeśli jest to anonimowe, schemat dla tego `IXmlSerializable` typu jest eksportowany jako typ anonimowy za każdym razem, gdy `IXmlSerializable` Typ jest używany jako element członkowski danych. `IXmlSerializable`Typ nadal ma nazwę kontraktu danych i przestrzeń nazw. (Ta wartość jest określana zgodnie z opisem w [nazwach kontraktów danych](data-contract-names.md) , z tą różnicą, że <xref:System.Runtime.Serialization.DataContractAttribute> nie można użyć atrybutu do dostosowania nazwy). Jeśli nie jest to anonimowe, musi być jednym z typów w `XmlSchemaSet` . Ten przypadek jest równoznaczny z zwróceniem `XmlQualifiedName` typu.

Ponadto globalna Deklaracja elementu jest eksportowana dla tego typu. Jeśli typ nie ma <xref:System.Xml.Serialization.XmlRootAttribute> zastosowanego atrybutu, element ma taką samą nazwę i przestrzeń nazw, co kontrakt danych i właściwość "nillable" ma wartość `true` . Jedynym wyjątkiem jest przestrzeń nazw schematu ( `http://www.w3.org/2001/XMLSchema` ) — Jeśli kontrakt danych typu znajduje się w tej przestrzeni nazw, odpowiadający element globalny znajduje się w pustej przestrzeni nazw, ponieważ jest zabroniony do dodawania nowych elementów do przestrzeni nazw schematu. Jeśli do typu został `XmlRootAttribute` zastosowany atrybut, Deklaracja elementu globalnego zostanie wyeksportowana przy użyciu następujących właściwości: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A> , <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> i <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> . Domyślnie `XmlRootAttribute` stosowane są nazwy kontraktu danych, pustej przestrzeni nazw i "nillable" `true` .

Te same reguły deklaracji elementu globalnego stosują się do typów starszych zestawów danych. Należy zauważyć, że `XmlRootAttribute` nie można przesłonić deklaracji elementu globalnego dodanych za pośrednictwem niestandardowego kodu, dodanej do `XmlSchemaSet` metody przy użyciu dostawcy schematu lub `GetSchema` w przypadku typów starszych zestawów danych.

### <a name="ixmlserializable-element-types"></a>Typy elementów IXmlSerializable

`IXmlSerializable`typy elementów mają `IsAny` ustawioną właściwość `true` lub mają zwracaną metodę dostawcy schematu `null` .

Serializacja i deserializacja typu elementu jest bardzo podobna do serializacji i deserializacji typu zawartości. Istnieją jednak pewne istotne różnice:

- `WriteXml`Implementacja powinna napisać dokładnie jeden element (który może oczywiście zawierać wiele elementów podrzędnych). Nie należy zapisywać atrybutów poza tym pojedynczym elementem, wielu elementów równorzędnych lub zawartości mieszanej. Element może być pusty.

- `ReadXml`Implementacja nie powinna odczytywać elementu otoki. Oczekiwane jest odczytanie jednego z elementów, które `WriteXml` tworzą.

- Podczas regularnego serializowania typu elementu (na przykład jako elementu członkowskiego danych w kontrakcie danych) serializator wyprowadza element otoki przed wywołaniem `WriteXml` , podobnie jak w przypadku typów zawartości. Jednak podczas serializowania typu elementu na najwyższego poziomu serializator nie zwykle wyprowadza element otoki wokół elementu, który `WriteXml` zapisuje, chyba że nazwa główna i przestrzeń nazw są jawnie określone podczas konstruowania serializatora w `DataContractSerializer` `NetDataContractSerializer` konstruktorach lub. Aby uzyskać więcej informacji, zobacz [serializacji i deserializacji](serialization-and-deserialization.md).

- Podczas serializowania typu elementu na najwyższym poziomie bez określania nazwy głównej i przestrzeni nazw w czasie konstruowania <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> i <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> zasadniczo nie rób niczego ani <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> wywołań `WriteXml` . W tym trybie serializacja obiektu nie może być `null` i nie może być przypisana do niego. Ponadto nie można włączyć zachowywania grafu obiektów i `NetDataContractSerializer` nie można go użyć.

- Podczas deserializacji typu elementu na najwyższym poziomie bez określania nazwy głównej i przestrzeni nazw w czasie konstruowania <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> Funkcja zwraca, `true` czy może znaleźć początek dowolnego elementu. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A>z `verifyObjectName` parametrem ustawionym na `true` zachowanie w taki sam sposób jak `IsStartObject` przed faktycznym odczytem obiektu. `ReadObject`następnie przekazuje sterowanie do `ReadXml` metody.

Schemat wyeksportowany dla typów elementów jest taki sam jak w przypadku `XmlElement` typu zgodnie z opisem w poprzedniej sekcji, z tą różnicą, że metoda dostawcy schematu może dodać dowolny schemat do <xref:System.Xml.Schema.XmlSchemaSet> elementów AS z typem zawartości. Używanie `XmlRootAttribute` atrybutu z typami elementów jest niedozwolone, a deklaracje elementu globalnego nigdy nie są emitowane dla tych typów.

### <a name="differences-from-the-xmlserializer"></a>Różnice od elementu XmlSerializer

`IXmlSerializable`Interfejs i `XmlSchemaProviderAttribute` `XmlRootAttribute` atrybuty i są również zrozumiałe dla <xref:System.Xml.Serialization.XmlSerializer> . Istnieją jednak pewne różnice w sposobie ich traktowania w modelu kontraktu danych. Istotne różnice przedstawiono na poniższej liście:

- Metoda dostawcy schematu musi być publiczna, aby mogła być używana w programie `XmlSerializer` , ale nie musi być publiczna, aby mogła być używana w modelu kontraktu danych.

- Metoda dostawcy schematu jest wywoływana, gdy `IsAny` znajduje się `true` w modelu kontraktu danych, ale nie z `XmlSerializer` .

- Jeśli `XmlRootAttribute` atrybut nie jest obecny dla typów zawartości lub starszego zestawu danych, `XmlSerializer` eksportuje deklarację elementu globalnego w pustej przestrzeni nazw. W modelu kontraktu danych używana przestrzeń nazw jest zwykle przestrzenią nazw kontraktu danych zgodnie z wcześniejszym opisem.

Należy pamiętać o tych różnicach podczas tworzenia typów, które są używane w przypadku obu technologii serializacji.

### <a name="importing-ixmlserializable-schema"></a>Importowanie schematu IXmlSerializable

Podczas importowania schematu wygenerowanego z `IXmlSerializable` typów, istnieje kilka możliwości:

- Wygenerowany schemat może być prawidłowym schematem kontraktu danych, zgodnie z opisem w temacie [Informacje o schemacie kontraktu danych](data-contract-schema-reference.md). W takim przypadku schemat można zaimportować w zwykły sposób, a generowane są zwykłe typy kontraktów danych.

- Wygenerowany schemat może nie być prawidłowym schematem kontraktu danych. Na przykład Metoda dostawcy schematu może generować schemat, który obejmuje atrybuty XML, które nie są obsługiwane w modelu kontraktu danych. W takim przypadku można zaimportować schemat jako `IXmlSerializable` typy. Ten tryb importu nie jest domyślnie włączony, ale może być łatwo włączony — na przykład przy użyciu `/importXmlTypes` wiersza polecenia do narzędzia do obsługi [metadanych ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Opisano to szczegółowo w temacie [Importowanie schematu do generowania klas](importing-schema-to-generate-classes.md). Należy pamiętać, że w przypadku wystąpień typów należy bezpośrednio korzystać z kodu XML. Możesz również rozważyć użycie innej technologii serializacji, która obsługuje szerszy zakres schematu — Zobacz temat dotyczący korzystania z programu `XmlSerializer` .

- Możesz chcieć ponownie użyć istniejących `IXmlSerializable` typów w serwerze proxy zamiast generować nowe. W takim przypadku funkcja typów odwołań opisana w temacie Importowanie schematu do generowania typów może być używana do wskazania typu do ponownego użycia. Odnosi się to do użycia `/reference` przełącznika na svcutil.exe, który określa zestaw, który zawiera typy do ponownego użycia.

### <a name="xmlserializer-legacy-behavior"></a>Starsze zachowanie funkcji XmlSerializer

W .NET Framework 4,0 i wcześniejszych element XmlSerializer wygenerował tymczasowe zestawy serializacji, pisząc kod w języku C# do pliku. Plik został następnie skompilowany w zestawie.  Takie zachowanie miało niepożądane konsekwencje, takie jak spowolnienie czasu uruchamiania programu szeregującego. W .NET Framework 4,5 to zachowanie zostało zmienione w celu wygenerowania zestawów bez konieczności używania kompilatora. Niektórzy deweloperzy mogą chcieć zobaczyć wygenerowany kod C#. Możesz określić, aby użyć tego starszego zachowania w następującej konfiguracji:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.xml.serialization>
    <xmlSerializer tempFilesLocation='e:\temp\XmlSerializerBug' useLegacySerializerGeneration="true" />
  </system.xml.serialization>
  <system.diagnostics>
    <switches>
      <add name="XmlSerialization.Compilation" value="1" />
    </switches>
  </system.diagnostics>
</configuration>
```

Jeśli występują problemy ze zgodnością, takie jak `XmlSerializer` Niepowodzenie serializacji klasy pochodnej z niepublicznym nowym przesłonięciem, można powrócić do `XMLSerializer` starszego zachowania przy użyciu następującej konfiguracji:

```xml
<configuration>
  <appSettings>
    <add key="System:Xml:Serialization:UseLegacySerializerGeneration" value="true" />
  </appSettings>
</configuration>
```

Alternatywą dla powyższej konfiguracji jest użycie poniższej konfiguracji na komputerze z systemem .NET Framework 4,5 lub nowszym:

```xml
<configuration>
  <system.xml.serialization>
    <xmlSerializer useLegacySerializerGeneration="true"/>
  </system.xml.serialization>
</configuration>
```

> [!NOTE]
> `<xmlSerializer useLegacySerializerGeneration="true"/>`Przełącznik działa tylko na maszynie z systemem .NET Framework 4,5 lub nowszym. Powyższe `appSettings` podejście działa na wszystkich wersjach .NET Framework.

## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.DataContractFormatAttribute>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.ServiceModel.MessageHeaderArrayAttribute>
- [Określanie transferu danych w kontraktach usług](specifying-data-transfer-in-service-contracts.md)
- [Używanie kontraktów danych](using-data-contracts.md)
- [Instrukcje: skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer](startup-time-of-wcf-client-applications-using-the-xmlserializer.md)

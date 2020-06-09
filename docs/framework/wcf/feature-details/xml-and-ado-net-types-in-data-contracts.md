---
title: Typy XML i ADO.NET w kontraktach danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2ce8461-3c15-4c41-8c81-1cb78f5b59a6
ms.openlocfilehash: 975d4f4f37bbbd895cab4e87686f15017e90f382
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600078"
---
# <a name="xml-and-adonet-types-in-data-contracts"></a>Typy XML i ADO.NET w kontraktach danych
Model kontraktu danych Windows Communication Foundation (WCF) obsługuje pewne typy, które reprezentują bezpośrednio dane XML. Gdy te typy są serializowane do formatu XML, serializator zapisuje zawartość XML tych typów bez żadnego dalszego przetwarzania. Obsługiwane typy to <xref:System.Xml.XmlElement> , tablice <xref:System.Xml.XmlNode> (ale nie `XmlNode` sam typ), a także typy, które implementują <xref:System.Xml.Serialization.IXmlSerializable> . <xref:System.Data.DataSet>Typ i <xref:System.Data.DataTable> , a także typy zestawów danych, są często używane w programowaniu bazy. Te typy implementują `IXmlSerializable` interfejs i w związku z tym są serializowane w modelu kontraktu danych. Niektóre specjalne zagadnienia dotyczące tych typów są wymienione na końcu tego tematu.  
  
## <a name="xml-types"></a>Typy XML  
  
### <a name="xml-element"></a>Element XML  
 `XmlElement`Typ jest serializowany przy użyciu jego zawartości XML. Na przykład, przy użyciu następującego typu.  
  
 [!code-csharp[DataContractAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#4)]
 [!code-vb[DataContractAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#4)]  
  
 Jest to serializowany do kodu XML w następujący sposób:  
  
```xml  
<MyDataContract xmlns="http://schemas.contoso.com">  
    <myDataMember>  
        <myElement xmlns="" myAttribute="myValue">  
            myContents  
        </myElement>  
    </myDataMember>  
</MyDataContract>  
```  
  
 Zauważ, że element członkowski danych otoki `<myDataMember>` wciąż istnieje. Nie ma możliwości usunięcia tego elementu w modelu kontraktu danych. Serializatory obsługujące ten model ( <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.NetDataContractSerializer> ) mogą emitować specjalne atrybuty do tego elementu otoki. Te atrybuty obejmują standardowy atrybut wystąpienia schematu XML "Nil" (zezwalanie na to `XmlElement` `null` ) i atrybut "Type" (Zezwalanie `XmlElement` na użycie polimorficzne). Ponadto następujące atrybuty XML są specyficzne dla WCF: "ID", "ref", "Type" i "Assembly". Te atrybuty mogą być emitowane do obsługi przy użyciu programu `XmlElement` z włączonym trybem zachowywania grafu obiektów lub z <xref:System.Runtime.Serialization.NetDataContractSerializer> . (Aby uzyskać więcej informacji na temat trybu zachowywania grafu obiektów, zobacz [serializacji i deserializacji](serialization-and-deserialization.md)).  
  
 Tablice lub kolekcje `XmlElement` są dozwolone i są obsługiwane jako każda inna tablica lub kolekcja. Oznacza to, że istnieje element otoki dla całej kolekcji i oddzielny element otoki (podobny do `<myDataMember>` powyższego przykładu) dla każdego `XmlElement` w tablicy.  
  
 Podczas deserializacji obiekt `XmlElement` jest tworzony przez Deserializator z przychodzącego kodu XML. Deserializator dostarcza prawidłowy element nadrzędny <xref:System.Xml.XmlDocument> .  
  
 Upewnij się, że fragment XML, który jest deserializowany do `XmlElement` definiuje wszystkie prefiksy, których używa, i nie bazuje na żadnych definicjach prefiksów z elementów nadrzędnych. Jest to problem tylko w przypadku korzystania z programu `DataContractSerializer` w celu uzyskiwania dostępu do pliku XML z innego źródła (innego niż `DataContractSerializer` ).  
  
 Gdy jest używany z `DataContractSerializer` , `XmlElement` może być przypisywana polimorficznie, ale tylko do składowej danych typu <xref:System.Object> . Mimo że implementuje <xref:System.Collections.IEnumerable> , `XmlElement` nie można użyć jako typu kolekcji i nie można go przypisać do <xref:System.Collections.IEnumerable> elementu członkowskiego danych. Podobnie jak w przypadku wszystkich przypisań polimorficznych, `DataContractSerializer` emituje nazwę kontraktu danych w powstającym kodzie XML — w tym przypadku jest to "XmlElement elementu" w http://schemas.datacontract.org/2004/07/System.Xml przestrzeni nazw "".  
  
 `NetDataContractSerializer`Jest obsługiwane każde prawidłowe przypisanie polimorficzne `XmlElement` (do `Object` lub `IEnumerable` ).  
  
 Nie należy próbować używać żadnego z serializatorów z typami pochodnymi od `XmlElement` , niezależnie od tego, czy są one przypisywane polimorficznie czy nie.  
  
### <a name="array-of-xmlnode"></a>Tablica elementów XmlNode  
 Korzystanie z tablic <xref:System.Xml.XmlNode> jest bardzo podobne do użycia `XmlElement` . Korzystanie z tablic `XmlNode` zapewnia większą elastyczność niż korzystanie z programu `XmlElement` . Można napisać wiele elementów wewnątrz elementu elementów członkowskich danych. Możesz również wstrzyknąć zawartość inną niż elementy wewnątrz elementu opakowującego składowej danych, takie jak Komentarze XML. Na koniec można umieścić atrybuty do elementu członkowskiego danych otoki. Wszystko to można osiągnąć, wypełniając tablicę `XmlNode` z określonymi klasami pochodnymi `XmlNode` , takimi jak <xref:System.Xml.XmlAttribute> , `XmlElement` lub <xref:System.Xml.XmlComment> . Na przykład, przy użyciu następującego typu.  
  
 [!code-csharp[DataContractAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#5)]
 [!code-vb[DataContractAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#5)]  
  
 Podczas serializacji, otrzymany kod XML jest podobny do następującego kodu.  
  
```xml  
<MyDataContract xmlns="http://schemas.contoso.com">  
  <myDataMember myAttribute="myValue">  
     <!--myComment-->  
     <myElement xmlns="" myAttribute="myValue">  
 myContents  
     </myElement>  
     <myElement xmlns="" myAttribute="myValue">  
       myContents  
     </myElement>  
  </myDataMember>  
</MyDataContract>  
```  
  
 Należy zauważyć, że element otoki składowej danych `<myDataMember>` zawiera atrybut, komentarz i dwa elementy. Są to cztery `XmlNode` wystąpienia, które zostały zserializowane.  
  
 `XmlNode`Nie można serializować tablicy z wynikami nieprawidłowego kodu XML. Na przykład tablica dwóch `XmlNode` wystąpień, gdzie pierwszy jest, `XmlElement` a drugi jest <xref:System.Xml.XmlAttribute> nieprawidłowa, ponieważ ta sekwencja nie odpowiada żadnemu prawidłowemu wystąpieniu XML (nie ma miejsca do dołączenia atrybutu do).  
  
 Podczas deserializacji tablicy `XmlNode` , węzły są tworzone i wypełniane informacjami z przychodzącego pliku XML. Deserializator dostarcza prawidłowy element nadrzędny <xref:System.Xml.XmlDocument> . Wszystkie węzły są deserializowane, łącznie z dowolnymi atrybutami elementu członkowskiego danych otoki, ale z wyłączeniem atrybutów umieszczonych przez serializatory WCF (na przykład atrybuty używane do wskazywania przypisania polimorficznego). Zastrzeżenie dotyczące definiowania wszystkich prefiksów przestrzeni nazw w fragmencie kodu XML ma zastosowanie do deserializacji tablic `XmlNode` tak samo jak w przypadku deserializacji `XmlElement` .  
  
 W przypadku korzystania z serializatorów z włączonym zachowywaniem grafu obiektów równość obiektów jest zachowywana tylko na poziomie `XmlNode` tablic, a nie w poszczególnych `XmlNode` wystąpieniach.  
  
 Nie należy próbować serializować tablicy, `XmlNode` w której co najmniej jeden węzeł jest ustawiony na `null` . Jest to dozwolone dla całego elementu członkowskiego tablicy `null` , ale nie dla żadnej osoby `XmlNode` zawartej w tablicy. Jeśli cały element członkowski tablicy ma wartość null, element członkowski danych otoki zawiera specjalny atrybut, który wskazuje, że ma wartość null. Podczas deserializacji cały element członkowski tablicy ma również wartość null.  
  
 Tylko regularne tablice `XmlNode` są traktowane specjalnie przez serializator. Elementy członkowskie danych zadeklarowane jako inne typy kolekcji `XmlNode` , które zawierają lub składowe danych zadeklarowane jako tablice typów pochodzących od `XmlNode` , nie są traktowane specjalnie. W ten sposób zwykle nie są możliwe do serializacji, chyba że spełniają one kryteria serializacji.  
  
 Tablice lub kolekcje tablic `XmlNode` są dozwolone. Istnieje element otoki dla całej kolekcji i oddzielny element otoki (podobny do `<myDataMember>` powyższego przykładu) dla każdej tablicy `XmlNode` w zewnętrznej tablicy lub kolekcji.  
  
 Wypełnianie składowej danych <xref:System.Array> typu `Object` lub `Array` z `IEnumerable` `XmlNode` wystąpieniami nie powoduje, że element członkowski danych jest traktowany jako `Array` `XmlNode` wystąpienia. Każdy element członkowski tablicy jest serializowany osobno.  
  
 W przypadku użycia z `DataContractSerializer` tablicami `XmlNode` można przypisywać polimorficznie, ale tylko do składowej danych typu `Object` . Mimo że implementuje `IEnumerable` tablicę `XmlNode` nie można używać jako typu kolekcji i są przypisane do `IEnumerable` elementu członkowskiego danych. Podobnie jak w przypadku wszystkich przypisań polimorficznych, `DataContractSerializer` emituje nazwę kontraktu danych w wyjściowym kodzie XML — w tym przypadku jest to "ArrayOfXmlNode" w http://schemas.datacontract.org/2004/07/System.Xml przestrzeni nazw "". W przypadku użycia z programem `NetDataContractSerializer` obsługiwane jest dowolne prawidłowe przypisanie `XmlNode` tablicy.  
  
### <a name="schema-considerations"></a>Zagadnienia dotyczące schematu  
 Aby uzyskać szczegółowe informacje na temat mapowania schematu typów XML, zobacz temat [Informacje o schemacie kontraktu danych](data-contract-schema-reference.md). Ta sekcja zawiera podsumowanie ważnych punktów.  
  
 Składowa danych typu `XmlElement` jest zamapowana na element zdefiniowany przy użyciu następującego typu anonimowego.  
  
```xml  
<xsd:complexType>  
   <xsd:sequence>  
      <xsd:any minOccurs="0" processContents="lax" />  
   </xsd:sequence>  
</xsd:complexType>  
```  
  
 Element członkowski danych typu Array `XmlNode` jest mapowany na element zdefiniowany przy użyciu następującego typu anonimowego.  
  
```xml  
<xsd:complexType mixed="true">  
   <xsd:sequence>  
      <xsd:any minOccurs="0" maxOccurs="unbounded" processContents="lax" />  
   </xsd:sequence>  
   <xsd:anyAttribute/>  
</xsd:complexType>  
```  
  
## <a name="types-implementing-the-ixmlserializable-interface"></a>Typy implementujące interfejs IXmlSerializable  
 Typy implementujące `IXmlSerializable` interfejs są w pełni obsługiwane przez `DataContractSerializer` . Ten <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybut powinien być zawsze stosowany do tych typów w celu sterowania ich schematem.  
  
 Istnieją trzy różne typy, które implementują `IXmlSerializable` : typy reprezentujące dowolną zawartość, typy reprezentujące pojedynczy element oraz starsze <xref:System.Data.DataSet> typy.  
  
- Typy zawartości używają metody dostawcy schematu określonej przez `XmlSchemaProviderAttribute` atrybut. Metoda nie zwraca `null` i <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> Właściwość w atrybucie ma wartość domyślną `false` . Jest to najbardziej typowe użycie `IXmlSerializable` typów.  
  
- Typy elementów są używane, gdy `IXmlSerializable` Typ musi kontrolować własną nazwę elementu głównego. Aby oznaczyć typ jako typ elementu, ustaw <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> Właściwość <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybutu na `true` lub Zwróć wartość null z metody dostawcy schematu. Posiadanie metody dostawcy schematu jest opcjonalne dla typów elementów — możesz określić wartość null zamiast nazwy metody w `XmlSchemaProviderAttribute` . Jednakże jeśli `IsAny` jest `true` i określono metodę dostawcy schematu, metoda musi zwracać wartość null.  
  
- Starsze <xref:System.Data.DataSet> typy to `IXmlSerializable` typy, które nie są oznaczone `XmlSchemaProviderAttribute` atrybutem. Zamiast tego korzystają one z <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> metody generowania schematu. Ten wzorzec jest używany dla `DataSet` typu i jego typ DataSet jest klasą we wcześniejszych wersjach .NET Framework, ale jest już przestarzały i jest obsługiwany tylko w przypadku starszych przyczyn. Nie należy polegać na tym wzorcu i zawsze stosować `XmlSchemaProviderAttribute` do Twoich `IXmlSerializable` typów.  
  
### <a name="ixmlserializable-content-types"></a>Typy zawartości interfejsu IXmlSerializable  
 Podczas serializacji elementu członkowskiego danych typu, który implementuje `IXmlSerializable` i jest typem zawartości zdefiniowanym wcześniej, serializator zapisuje element otoki dla elementu członkowskiego danych i przekazuje sterowanie do <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>Implementacja może napisać dowolny kod XML, łącznie z dodaniem atrybutów do elementu otoki. Po zakończeniu `WriteXml` serializator zamknie element.  
  
 Podczas deserializacji elementu członkowskiego typu, który implementuje `IXmlSerializable` i jest typem zawartości, zgodnie z definicją wcześniej, Deserializator umieszcza obiekt odczytujący XML na elemencie otoki dla elementu członkowskiego danych i przekazuje kontrolę do <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metody. Metoda musi odczytywać cały element, łącznie ze znacznikiem początkowym i końcowym. Upewnij się `ReadXml` , że kod obsługuje przypadek, w którym element jest pusty. Ponadto `ReadXml` implementacja nie powinna opierać się na elemencie otoki o nazwie w określony sposób. Nazwa jest wybierana przez serializator może się różnić.  
  
 Istnieje możliwość przypisywania `IXmlSerializable` typów zawartości polimorficznie, na przykład do składowych danych typu <xref:System.Object> . Dozwolone jest również, aby wystąpienia typu miały wartość null. Na koniec można używać `IXmlSerializable` typów z włączoną funkcją zachowywania grafów obiektów i z <xref:System.Runtime.Serialization.NetDataContractSerializer> . Wszystkie te funkcje wymagają, aby serializator WCF dołączył pewne atrybuty do elementu otoki ("Nil" i "Type" w przestrzeni nazw wystąpienia schematu XML i "ID", "ref", "Type" i "Assembly" w przestrzeni nazw specyficznej dla programu WCF).  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>Atrybuty do ignorowania podczas implementowania ReadXml  
 Przed przekazaniem kontroli do `ReadXml` kodu, Deserializator sprawdza element XML, wykrywa te specjalne atrybuty XML i wykonuje na nich działania. Na przykład jeśli "Nil" ma `true` wartość null, zostanie przeprowadzona deserializacja i `ReadXml` nie zostanie wywołana. W przypadku wykrycia polimorfizmu zawartość elementu jest deserializowana tak, jakby była innego typu. Implementacja z typem przypisanego do liczby polimorficznej `ReadXml` jest nazywana. W każdym przypadku `ReadXml` implementacja powinna ignorować te atrybuty specjalne, ponieważ są one obsługiwane przez Deserializator.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>Zagadnienia dotyczące schematu dla typów zawartości interfejsu IXmlSerializable  
 Podczas eksportowania schematu `IXmlSerializable` typu zawartości wywoływana jest metoda dostawcy schematu. <xref:System.Xml.Schema.XmlSchemaSet>Do metody dostawcy schematu jest przenoszona wartość. Metoda może dodać dowolny prawidłowy schemat do zestawu schematów. Zestaw schematu zawiera schemat, który jest już znany w chwili, gdy następuje eksport schematu. Gdy metoda dostawcy schematu musi dodać element do zestawu schematów, musi określić, czy <xref:System.Xml.Schema.XmlSchema> z odpowiednią przestrzenią nazw już istnieje w zestawie. Jeśli tak, Metoda dostawcy schematu musi dodać nowy element do istniejącego `XmlSchema` . W przeciwnym razie musi utworzyć nowe `XmlSchema` wystąpienie. Jest to ważne, jeśli tablice `IXmlSerializable` typów są używane. Na przykład, jeśli masz `IXmlSerializable` Typ, który zostanie wyeksportowany jako typ "A" w przestrzeni nazw "b", możliwe jest, że przez czas, gdy metoda dostawcy schematu jest wywoływana, zestaw schematu zawiera już schemat dla "B" w celu przechowywania typu "ArrayOfA".  
  
 Oprócz dodawania typów do <xref:System.Xml.Schema.XmlSchemaSet> , Metoda dostawcy schematu dla typów zawartości musi zwracać wartość różną od null. Może zwrócić element <xref:System.Xml.XmlQualifiedName> , który określa nazwę typu schematu do użycia dla danego `IXmlSerializable` typu. Ta kwalifikowana nazwa służy również jako nazwa kontraktu danych i przestrzeń nazw dla typu. Może zwrócić typ, który nie istnieje w zestawie schematu zaraz po powrocie metody dostawcy schematu. Jednak oczekuje się, że przez cały czas są eksportowane wszystkie powiązane typy ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> Metoda jest wywoływana dla wszystkich odpowiednich typów w <xref:System.Runtime.Serialization.XsdDataContractExporter> i <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> Właściwość jest dostępna), typ istnieje w zestawie schematów. Uzyskanie dostępu do `Schemas` Właściwości przed wykonaniem wszystkich odpowiednich `Export` wywołań może spowodować wystąpienie <xref:System.Xml.Schema.XmlSchemaException> . Aby uzyskać więcej informacji na temat procesu eksportowania, zobacz [Eksportowanie schematów z klas](exporting-schemas-from-classes.md).  
  
 Metoda dostawcy schematu może również zwrócić <xref:System.Xml.Schema.XmlSchemaType> do użycia. Typ może lub nie być anonimowy. Jeśli jest to anonimowe, schemat dla tego `IXmlSerializable` typu jest eksportowany jako typ anonimowy za każdym razem, gdy `IXmlSerializable` Typ jest używany jako element członkowski danych. `IXmlSerializable`Typ nadal ma nazwę kontraktu danych i przestrzeń nazw. (Ta wartość jest określana zgodnie z opisem w [nazwach kontraktów danych](data-contract-names.md) , z tą różnicą, że <xref:System.Runtime.Serialization.DataContractAttribute> nie można użyć atrybutu do dostosowania nazwy). Jeśli nie jest to anonimowe, musi być jednym z typów w `XmlSchemaSet` . Ten przypadek jest równoznaczny z zwróceniem `XmlQualifiedName` typu.  
  
 Ponadto globalna Deklaracja elementu jest eksportowana dla tego typu. Jeśli typ nie ma <xref:System.Xml.Serialization.XmlRootAttribute> zastosowanego atrybutu, element ma taką samą nazwę i przestrzeń nazw, co kontrakt danych i właściwość "nillable" ma wartość true. Jedynym wyjątkiem jest przestrzeń nazw schematu (" http://www.w3.org/2001/XMLSchema ") — Jeśli kontrakt danych typu znajduje się w tej przestrzeni nazw, odpowiedni element globalny znajduje się w pustej przestrzeni nazw, ponieważ jest zabroniony do dodawania nowych elementów do przestrzeni nazw schematu. Jeśli do typu został `XmlRootAttribute` zastosowany atrybut, Deklaracja elementu globalnego zostanie wyeksportowana przy użyciu następujących właściwości: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A> , <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> i <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> . Domyślnie `XmlRootAttribute` stosowane są nazwy kontraktu danych, pustej przestrzeni nazw i "nillable".  
  
 Te same reguły deklaracji elementu globalnego stosują się do typów starszych zestawów danych. Należy zauważyć, że `XmlRootAttribute` nie można przesłonić deklaracji elementu globalnego dodanych za pośrednictwem niestandardowego kodu, dodanej do `XmlSchemaSet` metody przy użyciu dostawcy schematu lub `GetSchema` w przypadku typów starszych zestawów danych.  
  
### <a name="ixmlserializable-element-types"></a>Typy elementów IXmlSerializable  
 `IXmlSerializable`typy elementów mają `IsAny` ustawioną właściwość `true` lub mają zwracaną metodę dostawcy schematu `null` .  
  
 Serializacja i deserializacja typu elementu jest bardzo podobna do serializacji i deserializacji typu zawartości. Istnieją jednak pewne istotne różnice:  
  
- `WriteXml`Implementacja powinna napisać dokładnie jeden element (który może oczywiście zawierać wiele elementów podrzędnych). Nie należy zapisywać atrybutów poza tym pojedynczym elementem, wielu elementów równorzędnych lub zawartości mieszanej. Element może być pusty.  
  
- `ReadXml`Implementacja nie powinna odczytywać elementu otoki. Oczekiwane jest odczytanie jednego z elementów, które `WriteXml` tworzą.  
  
- Podczas regularnego serializowania typu elementu (na przykład jako elementu członkowskiego danych w kontrakcie danych) serializator wyprowadza element otoki przed wywołaniem `WriteXml` , podobnie jak w przypadku typów zawartości. Jednak podczas serializowania typu elementu na najwyższego poziomu serializator nie zwykle wyprowadza element otoki wokół elementu, który `WriteXml` zapisuje, chyba że nazwa główna i przestrzeń nazw zostały jawnie określone podczas konstruowania serializatora w `DataContractSerializer` `NetDataContractSerializer` konstruktorach lub. Aby uzyskać więcej informacji, zobacz [serializacji i deserializacji](serialization-and-deserialization.md).  
  
- Podczas serializacji typu elementu na najwyższego poziomu bez określania głównej nazwy i przestrzeni nazw w czasie konstruowania <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> i <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> zasadniczo nie robi nic ani <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> wywołań `WriteXml` . W tym trybie serializacja obiektu nie może mieć wartości null i nie może być przypisana w sposób polimorficzny. Ponadto nie można włączyć zachowywania grafu obiektów i `NetDataContractSerializer` nie można go użyć.  
  
- Podczas deserializacji typu elementu na najwyższym poziomie bez określania nazwy głównej i przestrzeni nazw w czasie konstruowania <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> Funkcja zwraca, `true` czy może znaleźć początek dowolnego elementu. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A>z `verifyObjectName` parametrem ustawionym na `true` zachowanie w taki sam sposób jak `IsStartObject` przed faktycznym odczytem obiektu. `ReadObject`następnie przekazuje sterowanie do `ReadXml` metody.  
  
 Schemat wyeksportowany dla typów elementów jest taki sam jak w przypadku `XmlElement` typu zgodnie z opisem w poprzedniej sekcji, z tą różnicą, że metoda dostawcy schematu może dodać dowolny schemat do <xref:System.Xml.Schema.XmlSchemaSet> elementów AS z typem zawartości. Używanie `XmlRootAttribute` atrybutu z typami elementów jest niedozwolone, a deklaracje elementu globalnego nigdy nie są emitowane dla tych typów.  
  
### <a name="differences-from-the-xmlserializer"></a>Różnice od elementu XmlSerializer  
 `IXmlSerializable`Interfejs i `XmlSchemaProviderAttribute` `XmlRootAttribute` atrybuty i są również zrozumiałe dla <xref:System.Xml.Serialization.XmlSerializer> . Istnieją jednak pewne różnice w sposobie ich traktowania w modelu kontraktu danych. Ważne różnice są podsumowane w następujący sposób:  
  
- Metoda dostawcy schematu musi być publiczna, aby mogła być użyteczna w `XmlSerializer` , ale nie musi być publiczna, aby mogła być użyteczna w modelu kontraktu danych.  
  
- Metoda dostawcy schematu jest wywoływana, gdy `IsAny` ma wartość true w modelu kontraktu danych, ale nie z `XmlSerializer` .  
  
- Jeśli `XmlRootAttribute` atrybut nie jest obecny dla typów zawartości lub starszego zestawu danych, `XmlSerializer` eksportuje deklarację elementu globalnego w pustej przestrzeni nazw. W modelu kontraktu danych używana przestrzeń nazw jest zwykle przestrzenią nazw kontraktu danych zgodnie z wcześniejszym opisem.  
  
 Należy pamiętać o tych różnicach podczas tworzenia typów, które są używane w przypadku obu technologii serializacji.  
  
### <a name="importing-ixmlserializable-schema"></a>Importowanie schematu IXmlSerializable  
 Podczas importowania schematu wygenerowanego z `IXmlSerializable` typów, istnieje kilka możliwości:  
  
- Wygenerowany schemat może być prawidłowym schematem kontraktu danych, zgodnie z opisem w temacie [Informacje o schemacie kontraktu danych](data-contract-schema-reference.md). W takim przypadku schemat można zaimportować w zwykły sposób, a generowane są zwykłe typy kontraktów danych.  
  
- Wygenerowany schemat może nie być prawidłowym schematem kontraktu danych. Na przykład Metoda dostawcy schematu może generować schemat, który obejmuje atrybuty XML, które nie są obsługiwane w modelu kontraktu danych. W takim przypadku można zaimportować schemat jako `IXmlSerializable` typy. Ten tryb importu nie jest domyślnie włączony, ale może być łatwo włączony — na przykład przy użyciu `/importXmlTypes` wiersza polecenia do narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Opisano to szczegółowo w temacie [Importowanie schematu do generowania klas](importing-schema-to-generate-classes.md). Należy pamiętać, że w przypadku wystąpień typów należy bezpośrednio korzystać z kodu XML. Możesz również rozważyć użycie innej technologii serializacji, która obsługuje szerszy zakres schematu — Zobacz temat dotyczący korzystania z programu `XmlSerializer` .  
  
- Możesz chcieć ponownie użyć istniejących `IXmlSerializable` typów w serwerze proxy zamiast generować nowe. W takim przypadku funkcja typów odwołań opisana w temacie Importowanie schematu do generowania typów może być używana do wskazania typu do ponownego użycia. Odnosi się to do użycia `/reference` przełącznika w Svcutil. exe, który określa zestaw, który zawiera typy do ponownego użycia.  
  
## <a name="representing-arbitrary-xml-in-data-contracts"></a>Reprezentacja dowolnego kodu XML w kontraktach danych  
 `XmlElement`Tablica `XmlNode` i `IXmlSerializable` typy umożliwiają wprowadzanie dowolnych plików XML do modelu kontraktu danych. `DataContractSerializer`I `NetDataContractSerializer` przekazać tę zawartość XML do składnika zapisywania XML w użyciu, bez zakłócania procesu. Jednak moduły zapisujące XML mogą wymuszać pewne ograniczenia dotyczące zapisu w kodzie XML. Poniżej przedstawiono kilka ważnych przykładów:  
  
- Moduły zapisujące XML zazwyczaj nie zezwalają na deklarację dokumentu XML (na przykład \<?xml version=’1.0’ ?> ) w trakcie pisania innego dokumentu. Nie można wykonać pełnego dokumentu XML i serializować go jako `Array` `XmlNode` elementu członkowskiego danych. Aby to zrobić, musisz wykonać jedną z deklaracji dokumentu lub użyć własnego schematu kodowania do reprezentowania go.  
  
- Wszystkie moduły zapisujące XML dostarczone z usługą WCF odrzucają instrukcje przetwarzania XML ( \<? … ?> ) i definicje typów dokumentów ( \<! … > ), ponieważ nie są dozwolone w komunikatach protokołu SOAP. Aby obejść to ograniczenie, można użyć własnego mechanizmu kodowania. Jeśli musisz uwzględnić je w wynikowym kodzie XML, możesz napisać niestandardowy koder, który używa modułów zapisujących XML, które je obsługują.  
  
- Podczas implementowania `WriteXml` należy unikać wywoływania <xref:System.Xml.XmlWriter.WriteRaw%2A> metody w składniku zapisywania XML. Funkcja WCF korzysta z różnych kodowań XML (w tym plików binarnych), co jest bardzo trudne lub niemożliwe do użycia `WriteRaw` w celu użycia w dowolnym kodowaniu.  
  
- Podczas wdrażania `WriteXml` należy unikać używania <xref:System.Xml.XmlWriter.WriteEntityRef%2A> metod i <xref:System.Xml.XmlWriter.WriteNmToken%2A> , które nie są obsługiwane w modułach zapisujących XML dostarczanych z programem WCF.  
  
## <a name="using-dataset-typed-dataset-and-datatable"></a>Używanie zestawu danych, określonego zestawu danych i elementu DataTable  
 Korzystanie z tych typów jest w pełni obsługiwane w modelu kontraktu danych. Korzystając z tych typów, należy wziąć pod uwagę następujące kwestie:  
  
- Schemat tych typów (szczególnie <xref:System.Data.DataSet> i ich klasy pochodne) może nie być współdziałać z niektórymi platformami WCF lub mogą powodować słabą użyteczność, gdy jest używany z tymi platformami. Ponadto użycie tego `DataSet` typu może mieć wpływ na wydajność. Na koniec może być trudniejsze do aplikacji w przyszłości. Rozważ użycie jawnie zdefiniowanych typów kontraktu danych zamiast `DataSet` typów w umowach.  
  
- Podczas importowania `DataSet` lub `DataTable` schematu należy odwoływać się do tych typów. Za pomocą narzędzia wiersza polecenia Svcutil. exe można to osiągnąć, przekazując nazwę zestawu System. Data. dll do `/reference` przełącznika. W przypadku importowania schematu określonego zestawu danych należy odwołać się do typu określonego zestawu danych. W programie Svcutil. exe Przekaż lokalizację zestawu zestawu danych o określonym typie do `/reference` przełącznika. Aby uzyskać więcej informacji na temat odwołań do typów, zobacz [Importowanie schematu do generowania klas](importing-schema-to-generate-classes.md).  
  
 Obsługa wpisanych zestawów danych w modelu kontraktu dane jest ograniczona. Typy zestawów danych mogą być serializowane i deserializowane i mogą eksportować ich schematy. Jednak importowanie schematu kontraktu danych nie jest w stanie generować nowych typów zestawów danych z schematu, ponieważ mogą one ponownie używać istniejących. Możesz wskazać istniejący zestaw danych przy użyciu `/r` przełącznika w Svcutil. exe. Jeśli spróbujesz użyć Svcutil. exe bez `/r` przełącznika w usłudze, która używa określonego zestawu danych, zostanie automatycznie wybrany alternatywny serializator (XmlSerializer). Jeśli konieczne jest użycie elementu DataContractSerializer i musi on generować zestawy danych ze schematu, można użyć następującej procedury: Wygeneruj typy DataSet typów (za pomocą narzędzia XSD. exe z `/d` przełącznikiem w usłudze), skompiluj typy, a następnie wskaż je za pomocą `/r` przełącznika w Svcutil. exe.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>
- [Używanie kontraktów danych](using-data-contracts.md)
- [Typy obsługiwane przez serializator kontraktu danych](types-supported-by-the-data-contract-serializer.md)

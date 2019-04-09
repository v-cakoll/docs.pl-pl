---
title: Typy XML i ADO.NET w kontraktach danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2ce8461-3c15-4c41-8c81-1cb78f5b59a6
ms.openlocfilehash: 1053a543a23ed36a5c06c45044c8fdbe25a60538
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073965"
---
# <a name="xml-and-adonet-types-in-data-contracts"></a>Typy XML i ADO.NET w kontraktach danych
Model kontraktu danych Windows Communication Foundation (WCF) obsługuje niektóre typy, które reprezentują XML bezpośrednio. Gdy te typy są serializacji XML, serializator dokonuje zapisu zawartość XML na typy bez dalszego przetwarzania. Obsługiwane typy to <xref:System.Xml.XmlElement>, tablice <xref:System.Xml.XmlNode> (, ale nie `XmlNode` wpisz sam), jak również jako typami, które implementują <xref:System.Xml.Serialization.IXmlSerializable>. <xref:System.Data.DataSet> i <xref:System.Data.DataTable> typu, a także typizowanych zestawów danych, są często używane w programowaniu bazy danych. Te typy implementują `IXmlSerializable` interfejsu i w związku z tym możliwy do serializacji w danych są kontraktu modelu. Pewne specjalne zagadnienia dotyczące tych typów są wymienione na końcu tego tematu.  
  
## <a name="xml-types"></a>Typy XML  
  
### <a name="xml-element"></a>Xml Element  
 `XmlElement` Typ jest serializowana, za pomocą jego zawartości XML. Na przykład za pomocą następującego typu.  
  
 [!code-csharp[DataContractAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#4)]
 [!code-vb[DataContractAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#4)]  
  
 To jest serializowany do XML w następujący sposób:  
  
```xml  
<MyDataContract xmlns="http://schemas.contoso.com">  
    <myDataMember>  
        <myElement xmlns="" myAttribute="myValue">  
            myContents  
        </myElement>  
    </myDataMember>  
</MyDataContract>  
```  
  
 Należy zauważyć, że element członkowski danych otoki `<myDataMember>` nadal występuje. Nie ma sposobu usunięcia tego elementu w modelu kontraktu danych. Serializatory, obsługujące ten model ( <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.NetDataContractSerializer>) może emitować specjalnych atrybutów do tego elementu otoki. Te atrybuty zawierają atrybut "zero" standardowy wystąpienia schematu XML (co `XmlElement` jako `null`) i atrybutu "type" (dzięki czemu `XmlElement` ma być używany polymorphically). Ponadto następujące atrybuty XML są specyficzne dla usługi WCF: "Id", "Ref", "Type" i "Assembly". Te atrybuty mogą być emitowane do obsługi przy użyciu `XmlElement` z włączonym trybem reprezentatywność wykres obiektu lub za pomocą <xref:System.Runtime.Serialization.NetDataContractSerializer>. (Aby uzyskać więcej informacji o trybie konserwacji wykresu obiektu, zobacz [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).)  
  
 Tablice i kolekcje `XmlElement` są dozwolone i są obsługiwane jako dowolnej tablicy lub kolekcji. Oznacza to, że istnieje element otoki dla całej kolekcji, a element otoki oddzielne (podobnie jak `<myDataMember>` w powyższym przykładzie) dla każdego `XmlElement` w tablicy.  
  
 Na deserializacji `XmlElement` jest tworzony przez Deserializator z przychodzącego pliku XML. Prawidłowego elementu nadrzędnego <xref:System.Xml.XmlDocument> odbywa się przy deserializacji.  
  
 Upewnij się, że XML fragment to po deserializacji do `XmlElement` definiuje wszystkie prefiksy, które używa i nie zależą inne definicje prefiks z elementów nadrzędnych. Jest to niepożądane, tylko wtedy, gdy za pomocą `DataContractSerializer` dostępu do XML w innym (non -`DataContractSerializer`) źródła.  
  
 Gdy jest używane z `DataContractSerializer`, `XmlElement` może być przypisana polymorphically, ale tylko element członkowski danych typu <xref:System.Object>. Mimo że implementuje <xref:System.Collections.IEnumerable>, `XmlElement` nie można używać jako typ kolekcji, a nie można przypisać do <xref:System.Collections.IEnumerable> element członkowski danych. Podobnie jak w przypadku wszystkich przypisań polimorficznych, `DataContractSerializer` emituje nazwie kontraktu danych w wynikowy kod XML — w tym przypadku jest "XmlElement" w "http://schemas.datacontract.org/2004/07/System.Xml" przestrzeni nazw.  
  
 Za pomocą `NetDataContractSerializer`, wszystkie prawidłowe przypisanie polimorficznych `XmlElement` (Aby `Object` lub `IEnumerable`) jest obsługiwana.  
  
 Nie należy próbować użyć jednej z serializatory z typów pochodnych typu `XmlElement`na to, czy są przypisane polymorphically czy nie.  
  
### <a name="array-of-xmlnode"></a>Tablica elementów XmlNode  
 Przy użyciu tablic <xref:System.Xml.XmlNode> jest bardzo podobne do `XmlElement`. Przy użyciu tablic `XmlNode` zapewnia większą elastyczność niż przy użyciu `XmlElement`. Można napisać wiele elementów wewnątrz składowej danych, które zawijania elementu. Może również wprowadzać zawartość inna niż elementy wewnątrz składowej danych, które zawijania elementu, takiego jak komentarze XML. Na koniec można umieścić atrybutów w opakowywania element członkowski danych. Można to osiągnąć przez wypełnianie tablicy `XmlNode` z określonymi pochodne klasy `XmlNode` takich jak <xref:System.Xml.XmlAttribute>, `XmlElement` lub <xref:System.Xml.XmlComment>. Na przykład za pomocą następującego typu.  
  
 [!code-csharp[DataContractAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#5)]
 [!code-vb[DataContractAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#5)]  
  
 Po serializacji, wynikowy kod XML jest podobny do następującego kodu.  
  
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
  
 Należy pamiętać, że element otoki element członkowski danych `<myDataMember>` zawiera atrybut, komentarz i dwa elementy. Oto cztery `XmlNode` wystąpień, które są serializowane.  
  
 Tablica `XmlNode` skutkuje nieprawidłowy kod XML nie może być serializowany. Na przykład tablica dwa `XmlNode` wystąpień, w którym pierwsza z nich jest `XmlElement` , a drugi jest <xref:System.Xml.XmlAttribute> jest nieprawidłowa, ponieważ ta sekwencja nie odpowiada dowolne prawidłowe wystąpienie XML (ma miejsce, nie można dołączyć atrybut do).  
  
 Na deserializacji tablicy `XmlNode`, węzły są tworzone i wypełniane informacjami z przychodzącego pliku XML. Prawidłowego elementu nadrzędnego <xref:System.Xml.XmlDocument> odbywa się przy deserializacji. Wszystkie węzły są deserializacji, w tym wszelkie atrybuty na element członkowski danych otoki, ale z wyłączeniem atrybutów umieszczone w nim przez serializatory WCF (np. atrybuty, używany do wskazania polimorficznego przypisania). Ostrzeżenie o definiowaniu wszystkie prefiksy przestrzeni nazw w XML fragment, który ma zastosowanie do deserializacji tablic `XmlNode` tak samo, jak robi deserializacji `XmlElement`.  
  
 Jeśli serializatory z zachowania wykresu obiektu włączona, równość obiektu tylko zostaną zachowane na poziom `XmlNode` tablic, nie do poszczególnych `XmlNode` wystąpień.  
  
 Nie należy podejmować próby serializacji tablicę `XmlNode` których co najmniej jeden z węzłów ustawiono `null`. Jest dozwolona dla elementu całej tablicy, aby można `null`, ale nie dla każdej osoby `XmlNode` znajdujących się w tablicy. Jeśli cały element członkowski ma wartość null, element członkowski danych otoki zawiera specjalne atrybut, który wskazuje, że ma wartość null. Na deserializacji elementu członkowskiego tablicy całego staje się również o wartości null.  
  
 Tylko regularnych tablic `XmlNode` są traktowane specjalnie przez element serializujący. Elementy członkowskie danych zadeklarowany jako inne typy kolekcji, które zawierają `XmlNode`, lub elementy członkowskie danych zadeklarowany jako tablic typów pochodnych `XmlNode`, nie jest traktowany specjalnie. W związku z tym nie są one zazwyczaj serializacji, chyba że one również spełniać jeden z innych kryteriów dla serializacji.  
  
 Tablice lub kolekcji tablic `XmlNode` są dozwolone. Istnieje element otoki dla całej kolekcji, a element otoki oddzielne (podobnie jak `<myDataMember>` w powyższym przykładzie) dla każdej macierzy z `XmlNode` zewnętrzne tablicy lub kolekcji.  
  
 Wypełnianie składowej danych typu <xref:System.Array> z `Object` lub `Array` z `IEnumerable` z `XmlNode` wystąpień nie powoduje składowej danych, które są traktowane jako `Array` z `XmlNode` wystąpień. Każdego elementu członkowskiego tablicy jest serializowany oddzielnie.  
  
 Gdy jest używane z `DataContractSerializer`, tablice `XmlNode` można przypisać polymorphically, ale tylko do składowej danych typu `Object`. Mimo że implementuje `IEnumerable`, tablicę `XmlNode` nie można używać jako typ kolekcji, a następnie można przypisać do `IEnumerable` element członkowski danych. Podobnie jak w przypadku wszystkich przypisań polimorficznych, `DataContractSerializer` emituje nazwie kontraktu danych w wynikowy kod XML — w tym przypadku jest "ArrayOfXmlNode" w "http://schemas.datacontract.org/2004/07/System.Xml" przestrzeni nazw. Gdy jest używane z `NetDataContractSerializer`, wszystkie prawidłowe przypisanie `XmlNode` tablica jest obsługiwana.  
  
### <a name="schema-considerations"></a>Zagadnienia dotyczące schematu  
 Aby uzyskać szczegółowe informacje dotyczące schematu mapowania typów danych XML, zobacz [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Ta sekcja zawiera podsumowanie przedstawienie ważnych punktów.  
  
 Element członkowski danych typu `XmlElement` jest mapowany na element zdefiniowane przy użyciu następującego typu anonimowego.  
  
```xml  
<xsd:complexType>  
   <xsd:sequence>  
      <xsd:any minOccurs="0" processContents="lax" />  
   </xsd:sequence>  
</xsd:complexType>  
```  
  
 Element członkowski danych z typu tablicy `XmlNode` jest mapowany na element zdefiniowane przy użyciu następującego typu anonimowego.  
  
```xml  
<xsd:complexType mixed="true">  
   <xsd:sequence>  
      <xsd:any minOccurs="0" maxOccurs="unbounded" processContents="lax" />  
   </xsd:sequence>  
   <xsd:anyAttribute/>  
</xsd:complexType>  
```  
  
## <a name="types-implementing-the-ixmlserializable-interface"></a>Implementacja interfejsu IXmlSerializable typów  
 Typami, które implementują `IXmlSerializable` interfejsu są w pełni obsługiwane przez `DataContractSerializer`. <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> Zawsze można zastosować atrybutu do tych typów w celu kontrolowania swoich schematu.  
  
 Istnieją trzy różne typy typy, które implementują `IXmlSerializable`: typy, które reprezentują arbitralnie wybrane typy zawartości, reprezentujących pojedynczy element, a starsza wersja <xref:System.Data.DataSet> typów.  
  
-   Typy zawartości, użyj metody dostawcy schemat określony przez `XmlSchemaProviderAttribute` atrybutu. Metoda nie zwraca `null`i <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> właściwości w atrybucie pozostanie ustawiony na wartość domyślną `false`. Jest to najbardziej typowe użycie `IXmlSerializable` typów.  
  
-   Typy elementów są używane podczas `IXmlSerializable` typu musi kontrolować własną nazwą elementu głównego. Aby oznaczyć typu jako typu elementu, ustaw wartość <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> właściwość <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybutu `true` lub zwróć wartość null przez metodę dostawcy schematu. Posiadanie metody dostawcy schematu jest opcjonalne dla typów elementów — można określić wartość null zamiast nazwy metody w `XmlSchemaProviderAttribute`. Jednak jeśli `IsAny` jest `true` i metody dostawcy schemat jest określony, metoda musi zwracać wartość null.  
  
-   Starsza wersja <xref:System.Data.DataSet> typy są `IXmlSerializable` typy, które nie są oznaczone przez `XmlSchemaProviderAttribute` atrybutu. Zamiast tego opierają się na <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> metody do generowania schemat. Ten wzorzec jest używany dla `DataSet` typu i jego typizowany zestaw danych pochodzi z klasy we wcześniejszych wersjach programu .NET Framework, ale teraz jest przestarzały i nie jest obsługiwana tylko dla starszych powodów. Nie zależą od tego wzorca i zawsze stosuj `XmlSchemaProviderAttribute` do Twojej `IXmlSerializable` typów.  
  
### <a name="ixmlserializable-content-types"></a>Typy zawartości IXmlSerializable  
 Podczas serializacji typu, który implementuje element członkowski danych `IXmlSerializable` i typu zawartości jako zdefiniowano wcześniej, serializator zapisuje element otoki dla formantu elementu członkowskiego i przekazać dane do <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Implementacji może zapisywać żadnych XML, w tym dodawania atrybutów do element otoki. Po `WriteXml` jest wykonywane, serializator zamyka element.  
  
 Podczas deserializacji składowej danych typu, który implementuje `IXmlSerializable` i typ zawartości zgodnie z definicją wcześniej pozycji Deserializator odczytującego XML na element otoki dla element członkowski danych i przekazać sterowanie do <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metody. Metoda musi odczytać cały element, w tym tagiem początkowym i końcowym. Upewnij się, że Twoje `ReadXml` kod obsługuje przypadek, w której element jest pusty. Ponadto usługi `ReadXml` wdrożenia nie należy polegać na element otoki jest o nazwie określony sposób. Nazwa jest wybierany przez serializator może się różnić.  
  
 Dopuszcza się przypisać `IXmlSerializable` zawartości typów polymorphically, na przykład, aby dane elementy członkowskie typu <xref:System.Object>. Jest również dozwolony w przypadku wystąpień typu to null. Na koniec istnieje możliwość użycia `IXmlSerializable` typów z zachowania wykresu obiektu włączone i <xref:System.Runtime.Serialization.NetDataContractSerializer>. Wszystkie te funkcje wymagają serializator WCF można dołączyć niektóre atrybuty do element otoki ("zero" i "type" w przestrzeni nazw z wystąpienia schematu XML i "Id", "Ref", "Type" i "Assembly" w przestrzeni nazw specyficzne dla programu WCF).  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>Atrybuty do zignorowania podczas implementowania ReadXml  
 Przed przekazaniem kontroli do Twojej `ReadXml` kod, Deserializator sprawdza, czy XML element, wykrywa te atrybuty specjalne XML i działa na nich. Na przykład, jeśli jest "zero" `true`, wartość null jest przeprowadzona i `ReadXml` nie zostanie wywołana. W przypadku wykrycia polimorfizm zawartość elementu są deserializacji, tak jakby znajdowała się innego typu. Implementacja polymorphically przypisanego typu `ReadXml` jest wywoływana. W każdym przypadku `ReadXml` wdrożenia powinien ignorować te atrybuty specjalne, ponieważ są one obsługiwane przez deserializacji.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>Zagadnienia schematu dla typów IXmlSerializable zawartości  
 Podczas eksportowania schematu `IXmlSerializable` typ zawartości, wywoływana jest metoda dostawcy schematu. <xref:System.Xml.Schema.XmlSchemaSet> Jest przekazywany do metody dostawcy schematu. Metoda można dodać żadnych prawidłowego schematu do zestawu schematów. Zestaw schematów zawiera schemat, który jest już znany w czasie, gdy wystąpi eksportu schematu. Gdy metoda dostawcy schematu musi dodać element do zestawu schematów, musisz określić w przypadku <xref:System.Xml.Schema.XmlSchema> przy użyciu odpowiedniego obszaru nazw już istnieje w zestawie. Jeśli tak jest, metody dostawcy schemat, należy dodać nowy element do istniejącej `XmlSchema`. W przeciwnym razie należy utworzyć nowy `XmlSchema` wystąpienia. Jest to ważne, jeśli tablice `IXmlSerializable` typów są używane. Na przykład, jeśli masz `IXmlSerializable` typ, który pobiera wyeksportowany jako typu "A" w przestrzeni nazw "B", możliwe, że do czasu, wywoływana jest metoda dostawcy schematu, schemat już skonfigurowane zawiera schemat "B" pomieścić typu "ArrayOfA".  
  
 Oprócz dodawania typów <xref:System.Xml.Schema.XmlSchemaSet>, metodę dostawcy schematu dla typów zawartości musi zwracać wartość inną niż null. Może zwracać <xref:System.Xml.XmlQualifiedName> określający nazwę typu schematu do użycia dla danego `IXmlSerializable` typu. Ta nazwa kwalifikowana służy również jako dane kontraktu nazwy i przestrzeni nazw dla typu. Dozwolone jest zwracany typ, który nie istnieje w schemacie zestawu natychmiast, po powrocie z metody dostawcy schematu. Jednak oczekuje się, że po czasie wszystkie powiązane typy są eksportowane ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> metoda jest wywoływana dla wszystkich odpowiednich typów w <xref:System.Runtime.Serialization.XsdDataContractExporter> i <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> dostępu do właściwości), typ istnieje w zestawie schematów. Uzyskiwanie dostępu do `Schemas` właściwości przed wszystkimi odpowiednimi `Export` wprowadzono wywołań może spowodować <xref:System.Xml.Schema.XmlSchemaException>. Aby uzyskać więcej informacji na temat procesu eksportu, zobacz [eksportowanie schematów z klas](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
 Metoda dostawcy schemat może również zwracać <xref:System.Xml.Schema.XmlSchemaType> do użycia. Typ może być lub może nie być anonimowy. Jeśli jest anonimowe, schemat `IXmlSerializable` typu jest eksportowana jako typ anonimowy w każdym `IXmlSerializable` typ jest używany jako element członkowski danych. `IXmlSerializable` Typu środki, nieopłacone nazwie kontraktu danych i przestrzeni nazw. (To jest określana zgodnie z opisem w [nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md) z tą różnicą, że <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu nie można dostosować nazwę.) Jeśli nie jest anonimowe, musi być jednym z typów w `XmlSchemaSet`. Ten przypadek jest odpowiednikiem zwracanie `XmlQualifiedName` tego typu.  
  
 Ponadto deklaracji element globalny jest eksportowany dla typu. Jeśli typ nie ma <xref:System.Xml.Serialization.XmlRootAttribute> zastosowany do niego element ma taką samą nazwę i obszaru nazw kontraktu danych, a jego właściwość "nillable" ma wartość true. Jedynym wyjątkiem jest przestrzeń nazw schematu ("http://www.w3.org/2001/XMLSchema") — w przypadku typu kontraktu danych w tej przestrzeni nazw, odpowiedni element globalny jest w pustej przestrzeni nazw, ponieważ jest zabroniona Dodawanie nowych elementów do przestrzeni nazw schematu. Jeśli typ ma `XmlRootAttribute` zastosowany do jego deklaracji elementu globalnego jest eksportowana za pomocą następujących: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>, <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> i <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> właściwości. Ustawienia domyślne przy użyciu `XmlRootAttribute` stosowane są nazwie kontraktu danych, pustą przestrzeń nazw i "nillable" o wartości true.  
  
 Te same reguły element globalny w deklaracji mają zastosowanie do zestawu danych w starszej wersji typów. Należy pamiętać, że `XmlRootAttribute` nie może przesłonić element globalny deklaracje dodane poprzez kod niestandardowy być dodany do `XmlSchemaSet` przy użyciu metody dostawcy schematu lub za pomocą `GetSchema` dla typów starszej wersji zestawu danych.  
  
### <a name="ixmlserializable-element-types"></a>Typy elementów interfejsu IXmlSerializable  
 `IXmlSerializable` typy elementów mieć `IsAny` właściwością `true` lub ich dostawcy schematu, metoda zwraca `null`.  
  
 Serializacja i deserializacja typ elementu jest bardzo podobny do serializacji i deserializacji typu zawartości. Jednak istnieją pewne ważne różnice:  
  
-   `WriteXml` Implementacji oczekuje się, można zapisać dokładnie jeden element (który z kolei może zawierać wiele elementów podrzędnych). Nie powinien być wpisywanie atrybutów poza ten pojedynczy element wielu elementów równorzędnych lub zawartość mieszana. Element może być pusty.  
  
-   `ReadXml` Implementacji element otoki nie powinny do odczytu. Oczekuje się, aby przeczytać jeden element, `WriteXml` tworzy.  
  
-   Podczas serializacji typu elementu regularnie (na przykład, jako element członkowski danych w kontraktu danych), serializator danych wyjściowych element otoki przed wywołaniem `WriteXml`, podobnie jak w przypadku typów zawartości. Jednak podczas serializacji typu elementu na najwyższym poziomie, Serializator nie zwykle wyświetla element otoki w ogóle wokół elementu, `WriteXml` zapisuje, chyba że podczas tworzenia serializator jawnie określono nazwę główną i przestrzeni nazw w `DataContractSerializer` lub `NetDataContractSerializer` konstruktorów. Aby uzyskać więcej informacji, zobacz [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
-   Podczas serializacji typu elementu na najwyższym poziomie bez określania nazwy głównej i przestrzeni nazw w czasie tworzenia <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> i <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> zasadniczo nic nie robi i <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> wywołania `WriteXml`. W tym trybie obiektu poddawanego serializacji nie może mieć wartości null i nie można przypisać polymorphically. Ponadto nie można włączyć zachowania wykresu obiektu i `NetDataContractSerializer` nie mogą być używane.  
  
-   Podczas deserializacji typ elementu na najwyższym poziomie bez określania nazwy głównej i przestrzeni nazw w czasie tworzenia <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> zwraca `true` jeśli znajdzie uruchamiania dowolnego elementu. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> za pomocą `verifyObjectName` parametr `true` zachowuje się w taki sam sposób jak `IsStartObject` przed faktycznie odczytu obiektu. `ReadObject` następnie przekazuje sterowanie do `ReadXml` metody.  
  
 Schemat eksportowany dla typów elementów jest taki sam, jak w przypadku `XmlElement` wpisz zgodnie z opisem w sekcji wcześniej, z tą różnicą, że metoda dostawcy schematu można dodać dodatkowe schematu w celu <xref:System.Xml.Schema.XmlSchemaSet> podobnie jak w przypadku typów zawartości. Za pomocą `XmlRootAttribute` atrybut z typami elementu nie jest dozwolony, a element globalny deklaracje nigdy nie są emitowane dla tych typów.  
  
### <a name="differences-from-the-xmlserializer"></a>Różnice w stosunku do elementu XmlSerializer  
 `IXmlSerializable` Interfejsu i `XmlSchemaProviderAttribute` i `XmlRootAttribute` atrybuty są także zrozumiałe <xref:System.Xml.Serialization.XmlSerializer> . Jednak istnieją pewne różnice w jaki sposób są one traktowane w modelu kontraktu danych. Istotne różnice przedstawiono poniżej:  
  
-   Metody dostawcy schematu muszą być publiczne, może być używany w `XmlSerializer`, ale nie musi być publiczna może być używany w modelu kontraktu danych.  
  
-   Metoda dostawcy schematu jest wywoływana, gdy `IsAny` ma wartość true w modelu kontraktu danych, ale nie z `XmlSerializer`.  
  
-   Gdy `XmlRootAttribute` atrybut nie jest obecny do zawartości lub typy zestawów danych w starszej wersji, `XmlSerializer` eksportuje deklaracji element globalny w pustej przestrzeni nazw. W modelu kontraktu danych przestrzeń nazw używaną zwykle jest przestrzeń nazw kontraktu danych, zgodnie z wcześniejszym opisem.  
  
 Należy pamiętać o tych różnic, podczas tworzenia typów, które są używane w obu technologii serializacji.  
  
### <a name="importing-ixmlserializable-schema"></a>Importowanie schematu interfejsu IXmlSerializable  
 Podczas importowania schematu wygenerowany na podstawie `IXmlSerializable` typów, istnieje kilka możliwości:  
  
-   Wygenerowany schemat może być schematu kontraktu prawidłowych danych, zgodnie z opisem w [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). W takim przypadku schematu, które mogą być importowane w zwykły sposób, i są generowane typy kontraktu danych regularne.  
  
-   Wygenerowany schemat może nie być poprawne dane schematu kontraktu. Na przykład metoda dostawcy schematu może wygenerować schematu, która obejmuje atrybutów XML, które nie są obsługiwane w modelu kontraktu danych. W takim przypadku można zaimportować schematu jako `IXmlSerializable` typów. Domyślnie nie jest w ten tryb importu, ale można łatwo można włączyć — na przykład za pomocą `/importXmlTypes` przełącznik wiersza polecenia, aby [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Jest to opisane szczegółowo w temacie [Importowanie schematu do generowania klasy](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md). Należy pamiętać, że należy skontaktować się bezpośrednio z pliku XML dla wystąpień typu. Można także rozważyć użycie innej technologii serializacji, który obsługuje szerszy zakres schematów — zobacz temat w przy użyciu `XmlSerializer`.  
  
-   Może zajść potrzeba ponownego użycia istniejącej `IXmlSerializable` typów serwera proxy zamiast generować nową. W takim przypadku funkcja przywoływane typy opisana w schemacie importowanie do tematu wygenerować typy można wskazać typ do ponownego użycia. Odpowiada to użyciu `/reference` Włącz svcutil.exe, który określa zestaw, który zawiera typy do ponownego użycia.  
  
## <a name="representing-arbitrary-xml-in-data-contracts"></a>Reprezentuje dowolny kod XML w kontraktach danych  
 `XmlElement`, Tablica `XmlNode` i `IXmlSerializable` typy pozwala na iniekcję dowolny kod XML do modelu kontraktu danych. `DataContractSerializer` i `NetDataContractSerializer` przekazać plik XML zawartości do składnika zapisywania XML w użyciu, bez wywierania wpływu w procesie. Jednak autorzy XML może wymuszać pewne ograniczenia dotyczące plik XML, który zapisują. Ściślej mówiąc poniżej przedstawiono kilka przykładów ważnych:  
  
-   Autorzy XML zazwyczaj nie zezwala na deklaracji dokumentu XML (na przykład \<? wersji xml = "1.0'? >) w trakcie wpisywania innego dokumentu. Nie można wykonać pełnego dokumentu XML i serializować go jako `Array` z `XmlNode` element członkowski danych. Aby to zrobić, musisz albo usuń deklaracji dokumentu lub użyć schemat kodowania, aby oznaczyć go.  
  
-   Odrzuć wszystkie moduły zapisujące XML dostarczone z programem WCF instrukcji przetwarzania XML (\<? … ? >) i zarządzania dokumentami, definicje typów (\<! … >), ponieważ nie są dozwolone w komunikaty protokołu SOAP. Ponownie można użyć własnego mechanizmu kodowania, aby obejść to ograniczenie. Jeśli należy uwzględnić je w wynikowy kod XML, można napisać niestandardowego kodera, który używa autorzy XML, które je obsługują.  
  
-   Podczas implementowania `WriteXml`, należy unikać wywoływania <xref:System.Xml.XmlWriter.WriteRaw%2A> metody edytora XML. Usługi WCF używa różnych kodowań XML (w tym pliku binarnego), jest bardzo trudne lub niemożliwe do użycia `WriteRaw` taki sposób, że wynik nie będzie można używać w dowolnym kodowania.  
  
-   Podczas implementowania `WriteXml`, należy unikać <xref:System.Xml.XmlWriter.WriteEntityRef%2A> i <xref:System.Xml.XmlWriter.WriteNmToken%2A> metody, które nie są obsługiwane w autorzy XML dostarczone z programem WCF.  
  
## <a name="using-dataset-typed-dataset-and-datatable"></a>Przy użyciu zestawu danych, Typizowany zestaw danych i elementu DataTable  
 Używanie tych typów jest w pełni obsługiwany w modelu kontraktu danych. Korzystając z tych typów, należy wziąć pod uwagę następujące kwestie:  
  
-   Schemat dla tych typów (szczególnie <xref:System.Data.DataSet> i jego typizowanych klas pochodnych) może nie być współpracujący z niektórych platform innych niż WCF lub może spowodować niską użyteczności w przypadku korzystania z tych platform. Ponadto za pomocą `DataSet` typ może mieć wpływ na wydajność. Na koniec go może utrudnić służących do wersji aplikacji w przyszłości. Należy rozważyć użycie typy kontraktu danych jawnie zdefiniowanych zamiast `DataSet` typy w kontraktach usługi.  
  
-   Podczas importowania `DataSet` lub `DataTable` schematu, ważne jest, aby odwoływać się do tych typów. Za pomocą narzędzia wiersza polecenia Svcutil.exe, można to osiągnąć przez przekazanie nazwy zestawu System.Data.dll, aby `/reference` przełącznika. W przypadku importowania danych wpisywanych schematu musi odwoływać się typ typizowany zestaw danych. Za pomocą Svcutil.exe, przekazać lokalizację zestawu typizowany zestaw danych do `/reference` przełącznika. Aby uzyskać więcej informacji na temat odwołujące się do typów, zobacz [Importowanie schematu do generowania klasy](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 Obsługa typizowanych zestawów danych w modelu danych umowy jest ograniczona. Typizowanych zestawów danych może być serializowany i deserializować i wyeksportować ich schematu. Jednak kontraktu danych, import schematu nie może wygenerować nowe wpisane typy zestawów danych ze schematu, jak tylko można użyć ponownie już istniejących. Możesz wskazać istniejące typizowany zestaw danych za pomocą `/r` Włącz Svcutil.exe. Jeśli spróbujesz użyć Svcutil.exe bez `/r` przełącznika od usługi, która używa typizowany zestaw danych, alternatywnych serializatora (XmlSerializer) to opcja wybrana automatycznie. Jeśli należy użyć elementu DataContractSerializer, należy wygenerować zestawy danych ze schematu można użyć poniższej procedury: generowania typizowanych typy zestawów danych (za pomocą narzędzia Xsd.exe z `/d` przełączyć się na usługę), skompilować typów, a następnie wskaż je przy użyciu `/r` Włącz Svcutil.exe.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>
- [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)

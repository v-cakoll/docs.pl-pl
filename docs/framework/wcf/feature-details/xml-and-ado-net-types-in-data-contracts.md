---
title: Typy XML i ADO.NET w kontraktach danych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c2ce8461-3c15-4c41-8c81-1cb78f5b59a6
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7efef63668bb78bdc9a7d66654c9e33ef6c0138c
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="xml-and-adonet-types-in-data-contracts"></a>Typy XML i ADO.NET w kontraktach danych
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Modelu kontraktu danych obsługuje pewnych typów, które reprezentują XML bezpośrednio. Gdy te typy są serializowane do pliku XML, serializator zapisuje poza zawartość XML w typach bez dalszego przetwarzania. Obsługiwane typy to <xref:System.Xml.XmlElement>, tablic <xref:System.Xml.XmlNode> (, ale nie `XmlNode` samego typu), a także jako typy które implementują <xref:System.Xml.Serialization.IXmlSerializable>. <xref:System.Data.DataSet> i <xref:System.Data.DataTable> typu, a także typizowane zbiory danych, są często używane w programowania bazy danych. Implementuje te typy `IXmlSerializable` interfejsu i dlatego możliwy do serializacji w danych są kontraktu modelu. Niektóre uwagi dotyczące tych typów są wyświetlane na końcu tego tematu.  
  
## <a name="xml-types"></a>Typy XML  
  
### <a name="xml-element"></a>XML Element  
 `XmlElement` Zserializować typu przy użyciu jego zawartość XML. Na przykład za pomocą następującego typu.  
  
 [!code-csharp[DataContractAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#4)]
 [!code-vb[DataContractAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#4)]  
  
 To jest serializowany do formatu XML w następujący sposób:  
  
```xml  
<MyDataContract xmlns="http://schemas.contoso.com">  
    <myDataMember>  
        <myElement xmlns="" myAttribute="myValue">  
            myContents  
        </myElement>  
    </myDataMember>  
</MyDataContract>  
```  
  
 Zwróć uwagę, że element otoki danych elementu członkowskiego `<myDataMember>` nadal występuje. Nie istnieje sposób usuwania tego elementu w modelu kontraktu danych. Serializatorów, które obsługują ten model ( <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.NetDataContractSerializer>) może emitować specjalne atrybuty do tego elementu otoki. Te atrybuty obejmują standardowe wystąpienie schematu XML atrybut "zero" (co `XmlElement` za `null`) i atrybutu "type" (dzięki czemu `XmlElement` używanego polymorphically). Ponadto następujące atrybuty XML są specyficzne dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: "Id", "Ref", "Type" i "Zestawu". Te atrybuty mogą wysyłanego do obsługi przy użyciu `XmlElement` z trybu konserwacji obiektu wykresu włączona lub <xref:System.Runtime.Serialization.NetDataContractSerializer>. (Aby uzyskać więcej informacji o trybie konserwacji wykres obiektu, zobacz [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).)  
  
 Tablice lub kolekcje `XmlElement` dozwolone są i będą obsługiwane jako inne tablicą lub kolekcją. Jest element otoki dla całej kolekcji, a element otoki oddzielne (podobnie jak `<myDataMember>` w poprzednim przykładzie) dla każdego `XmlElement` w tablicy.  
  
 Podczas deserializacji `XmlElement` jest tworzona przy deserializacji przychodzącego pliku XML. Prawidłowego elementu nadrzędnego <xref:System.Xml.XmlDocument> odbywa się przy deserializacji.  
  
 Upewnij się, że XML fragment, która jest zdeserializowany do `XmlElement` definiuje wszystkie prefiksy, które używa i nie zależą inne definicje prefiks z elementów nadrzędnych. Jest to niepożądane tylko w przypadku używania `DataContractSerializer` dostępu do XML z inną (z systemem innym niż`DataContractSerializer`) źródła.  
  
 W przypadku użycia z `DataContractSerializer`, `XmlElement` mogły zostać przypisane polymorphically, ale tylko do elementu członkowskiego danych typu <xref:System.Object>. Mimo że implementuje <xref:System.Collections.IEnumerable>, `XmlElement` nie może być używany jako typ kolekcji i nie można przypisać do <xref:System.Collections.IEnumerable> element członkowski danych. Podobnie jak w przypadku wszystkich przypisań polimorficznym, `DataContractSerializer` emituje nazwie kontraktu danych XML wynikowy — w tym przypadku jest "XmlElement" w "http://schemas.datacontract.org/2004/07/System.Xml" przestrzeni nazw.  
  
 Z `NetDataContractSerializer`, wszystkie prawidłowe przypisanie polimorficznym `XmlElement` (do `Object` lub `IEnumerable`) jest obsługiwana.  
  
 Nie należy próbować użyć dowolnej z serializatorów z typami pochodnymi `XmlElement`, czy polymorphically lub nie są przypisane.  
  
### <a name="array-of-xmlnode"></a>Tablica XmlNode  
 Używanie tablic z <xref:System.Xml.XmlNode> jest bardzo podobny do sposobu używania `XmlElement`. Używanie tablic z `XmlNode` zapewnia większą elastyczność niż przy użyciu `XmlElement`. Można zapisywać wiele elementów wewnątrz elementu członkowskiego danych zawijania elementu. Można również wstrzyknąć zawartości innego niż elementy wewnątrz elementu członkowskiego danych zawijania elementu, takiego jak komentarze XML. Na koniec można umieścić atrybutów w opakowywania elementu członkowskiego danych. Wszystko to można osiągnąć dzięki wprowadzaniu tablica `XmlNode` z określonymi pochodnej klasy `XmlNode` takich jak <xref:System.Xml.XmlAttribute>, `XmlElement` lub <xref:System.Xml.XmlComment>. Na przykład za pomocą następującego typu.  
  
 [!code-csharp[DataContractAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#5)]
 [!code-vb[DataContractAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#5)]  
  
 Podczas serializacji, wynikowy kod XML jest podobny do następującego kodu.  
  
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
  
 Należy pamiętać, że element otoki elementu członkowskiego danych `<myDataMember>` zawiera atrybut komentarz i dwa elementy. Są cztery `XmlNode` wystąpień, które przeprowadzono serializacji.  
  
 Tablica `XmlNode` powoduje nieprawidłowe dane XML nie może być serializowany. Na przykład macierzy dwa `XmlNode` pierwsza z nich jest `XmlElement` , a drugi jest <xref:System.Xml.XmlAttribute> jest nieprawidłowy, ponieważ ta sekwencja nie odpowiada na dowolne prawidłowe wystąpienie XML (Brak miejsca nie można dołączyć atrybut do).  
  
 Przy deserializacji tablicy `XmlNode`, węzły są tworzone i wypełniane przy użyciu informacji z przychodzącego pliku XML. Prawidłowego elementu nadrzędnego <xref:System.Xml.XmlDocument> odbywa się przy deserializacji. Rozszeregować we wszystkich węzłach, w tym wszystkie atrybuty w elemencie członkowskim otoki danych, ale z wyłączeniem atrybutów umieszczone w nim przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serializatorów (takich jak atrybuty służy do wskazania przypisania polimorficznych). Ostrzeżenie o definiujący wszystkie prefiksy przestrzeni nazw w fragmentu XML ma zastosowanie do deserializacji tablice `XmlNode` tak samo jak robi deserializacji `XmlElement`.  
  
 Przy użyciu serializatorów z zachowywania wykres obiektu włączona, równość obiektu tylko zostaną zachowane na poziomie `XmlNode` tablice nie poszczególnych `XmlNode` wystąpień.  
  
 Nie należy próbować serializować tablicę `XmlNode` których co najmniej jeden z nich jest wartość `null`. Jest dozwolone w przypadku cały element członkowski jako `null`, ale nie dla każdej osoby `XmlNode` zawartych w tablicy. Jeśli cały element członkowski ma wartość null, elementu członkowskiego danych otoki zawiera specjalne atrybut, który wskazuje, że jest ona pusta. Podczas deserializacji cały element członkowski staje się również wartość null.  
  
 Tylko regularne tablice `XmlNode` są traktowane specjalnie przez serializator. Elementy członkowskie danych jest zadeklarowany jako inne typy kolekcji, które zawierają `XmlNode`, lub elementy członkowskie danych deklarowane jako tablice typów pochodnych `XmlNode`, nie są traktowane specjalnie. W związku z tym nie są one zazwyczaj serializacji chyba że spełniają również jednego z innych kryteriów dla serializacji.  
  
 Tablice lub kolekcji tablic `XmlNode` są dozwolone. Istnieje element otoki dla całej kolekcji, a element otoki oddzielne (podobnie jak `<myDataMember>` w poprzednim przykładzie) dla każdej macierzy z `XmlNode` w zewnętrznym tablicy lub kolekcji.  
  
 Podczas wypełniania elementu członkowskiego danych typu <xref:System.Array> z `Object` lub `Array` z `IEnumerable` z `XmlNode` wystąpień nie powoduje, są traktowane jako element członkowski danych `Array` z `XmlNode` wystąpień. Każdy element członkowski tablicy jest serializowany oddzielnie.  
  
 W przypadku użycia z `DataContractSerializer`, tablic `XmlNode` można przypisać polymorphically, ale tylko do elementu członkowskiego danych typu `Object`. Mimo że implementuje `IEnumerable`, tablicę `XmlNode` nie może być używany jako typ kolekcji, a następnie przypisać do `IEnumerable` element członkowski danych. Podobnie jak w przypadku wszystkich przypisań polimorficznym, `DataContractSerializer` emituje nazwie kontraktu danych XML wynikowy — w tym przypadku jest "ArrayOfXmlNode" w "http://schemas.datacontract.org/2004/07/System.Xml" przestrzeni nazw. W przypadku użycia z `NetDataContractSerializer`, wszystkie prawidłowe przypisanie `XmlNode` tablica jest obsługiwana.  
  
### <a name="schema-considerations"></a>Zagadnienia dotyczące schematu  
 Aby uzyskać szczegółowe informacje dotyczące mapowania schematu typów danych XML, zobacz [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Ta sekcja zawiera podsumowanie ważnych punktów.  
  
 Element członkowski danych typu `XmlElement` jest zamapowany do elementu zdefiniowane przy użyciu następującego typu anonimowego.  
  
```xml  
<xsd:complexType>  
   <xsd:sequence>  
      <xsd:any minOccurs="0" processContents="lax" />  
   </xsd:sequence>  
</xsd:complexType>  
```  
  
 Element członkowski danych klasy typu tablicy `XmlNode` jest zamapowany do elementu zdefiniowane przy użyciu następującego typu anonimowego.  
  
```xml  
<xsd:complexType mixed="true">  
   <xsd:sequence>  
      <xsd:any minOccurs="0" maxOccurs="unbounded" processContents="lax" />  
   </xsd:sequence>  
   <xsd:anyAttribute/>  
</xsd:complexType>  
```  
  
## <a name="types-implementing-the-ixmlserializable-interface"></a>Implementacja interfejsu IXmlSerializable typów  
 Typy, które implementują `IXmlSerializable` interfejsu są w pełni obsługiwane przez `DataContractSerializer`. <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> Zawsze można zastosować atrybutu do tych typów, aby kontrolować ich schematu.  
  
 Istnieją trzy różne typy typów, które implementują `IXmlSerializable`: typy, które reprezentują dowolne typy zawartości, które reprezentują pojedynczy element i starszych <xref:System.Data.DataSet> typów.  
  
-   Typy zawartości należy użyć metody dostawcy schematu, określony przez `XmlSchemaProviderAttribute` atrybutu. Metoda nie zwraca `null`i <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> właściwości atrybutu pozostanie ustawiony na wartość domyślną `false`. Jest to najbardziej typowe użycie `IXmlSerializable` typów.  
  
-   Typy elementów są używane podczas `IXmlSerializable` typu musi kontrolować własną nazwę elementu głównego. Aby oznaczyć typu jako typu elementu, ustawić <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> właściwość <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybutu `true` lub zwróć wartość null z metody dostawcy schematu. Posiadanie metody dostawcy schematu jest opcjonalny w przypadku typów elementów — można określić wartości null, a nie nazwę metody w `XmlSchemaProviderAttribute`. Jednak jeśli `IsAny` jest `true` i metody dostawcy schematu jest określony, metoda musi zwracać wartość null.  
  
-   Starsza wersja <xref:System.Data.DataSet> typy są `IXmlSerializable` typy, które nie są oznaczone ikoną z `XmlSchemaProviderAttribute` atrybutu. Zamiast tego opierają się na <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> metodę generowania schematu. Ten wzorzec jest używana do `DataSet` typu i jego typizowanego obiektu dataset pochodzi z klasy w starszych wersjach programu .NET Framework, ale teraz jest przestarzały i nie jest obsługiwana tylko w przypadku starszych powodów. Nie zależą od tego wzorca i zawsze stosuj `XmlSchemaProviderAttribute` do Twojej `IXmlSerializable` typów.  
  
### <a name="ixmlserializable-content-types"></a>Typy zawartości interfejsu IXmlSerializable  
 Podczas serializowania element członkowski danych klasy typu, który implementuje `IXmlSerializable` i typu zawartości, jak zdefiniowano wcześniej, serializator zapisuje element otoki kontrolki elementu członkowskiego i przekazać dane do <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Implementacja może zapisywać żadnych XML, takie jak dodawanie atrybutów do elementu otoki. Po `WriteXml` jest gotowe, serializator zamyka element.  
  
 Podczas deserializacji element członkowski danych klasy typu, który implementuje `IXmlSerializable` i typu zawartości zgodnie z definicją wcześniej, pozycje Deserializator modułu odczytującego XML na element otoki dla elementu członkowskiego danych i przekazać do kontrolować <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metody. Metoda musi odczytu cały element, w tym tagiem początkowym i końcowym. Upewnij się, że Twoje `ReadXml` kod obsługi w przypadku, gdy element jest pusty. Ponadto sieci `ReadXml` wdrożenia nie należy traktować element otoki jest o nazwie określony sposób. Nazwa jest wybierany przez serializator może się różnić.  
  
 Dozwolone jest przypisanie `IXmlSerializable` typy zawartości polymorphically, na przykład do danych elementów członkowskich typu <xref:System.Object>. Dopuszczalne jest również wystąpień typu mieć wartości null. Na koniec jest możliwość użycia `IXmlSerializable` typy z zachowywania wykres obiektu włączone i <xref:System.Runtime.Serialization.NetDataContractSerializer>. Tych funkcji wymaga [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serializator dołączyć niektóre atrybuty w element otoki ("zero" i "type" w przestrzeni nazw XML schematu wystąpienia i "Id", "Ref", "Type" i "Zestawu" w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-określonych przestrzeni nazw).  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>Atrybuty, aby zignorować podczas implementowania ReadXml  
 Przed przekazaniem kontroli do Twojej `ReadXml` kodu, Deserializator sprawdza, czy XML element, wykrywa te specjalne atrybuty XML i działa na nich. Na przykład, jeśli jest "zero" `true`, deserializowany jest wartość null i `ReadXml` nie jest wywoływany. W przypadku wykrycia polimorfizm zawartość elementu są rozszeregować tak, jakby była innego typu. Implementacja typu polymorphically przypisanej `ReadXml` jest wywoływana. W każdym przypadku `ReadXml` implementacji ignorować te atrybuty specjalne, ponieważ są one obsługiwane przez deserializacji.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>Zagadnienia dotyczące schematu dla typów IXmlSerializable zawartości  
 Podczas eksportowania schematu `IXmlSerializable` typu zawartości, wywoływana jest metoda dostawcy schematu. <xref:System.Xml.Schema.XmlSchemaSet> Jest przekazywany do metody dostawcy schematu. Metoda można dodać żadnych prawidłowego schematu do zestawu schematów. Zestaw schematu zawiera schemat, który został już określony w momencie, gdy wystąpi eksportowania schematu. Gdy metoda dostawcy schematu należy dodać element do zestawu schematów, musi ustalić w przypadku <xref:System.Xml.Schema.XmlSchema> z odpowiedni obszar nazw już istnieje w zestawie. Jeśli tak, metody dostawcy schematu należy dodać nowy element do istniejącej `XmlSchema`. W przeciwnym razie należy utworzyć nowy `XmlSchema` wystąpienia. Jest to ważne, jeśli tablice `IXmlSerializable` typy są używane. Na przykład, jeśli masz `IXmlSerializable` typu, który pobiera wyeksportowany jako typu "A" w przestrzeni nazw "B", możliwe, że do czasu wywołania metody dostawcy schematu schematu już ustawione zawiera schemat "B" typu "ArrayOfA".  
  
 Oprócz dodania typów do <xref:System.Xml.Schema.XmlSchemaSet>, metody dostawcy schematu dla typów zawartości musi zwracać wartość inną niż null. Może on zwrócić <xref:System.Xml.XmlQualifiedName> , który określa nazwę typu schematu dla podanego `IXmlSerializable` typu. Ta nazwa kwalifikowana służy również jako dane umowy, nazwę i przestrzeń nazw dla typu. Dozwolone jest zwracany typ, który nie istnieje w zestawie natychmiast, gdy metoda dostawcy schematu zwraca schematów. Jednak oczekuje się, że w czasie wszystkie powiązane typy są eksportowane ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> metoda jest wywoływana dla wszystkich odpowiednich typów na <xref:System.Runtime.Serialization.XsdDataContractExporter> i <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> dostępu do właściwości), typ istnieje w zestawie schematów. Uzyskiwanie dostępu do `Schemas` właściwości przed wszystkimi odpowiednimi `Export` wprowadzono wywołania może spowodować <xref:System.Xml.Schema.XmlSchemaException>. Aby uzyskać więcej informacji na temat procesu eksportu, zobacz [eksportowanie schematów z klas](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
 Metoda dostawcy schematu może także zwracać <xref:System.Xml.Schema.XmlSchemaType> do użycia. Tego typu może lub nie może być anonimowy. Jeśli jest anonimowy, schemat `IXmlSerializable` typu jest eksportowane jako typu anonimowego zawsze `IXmlSerializable` typ jest używany jako element członkowski danych. `IXmlSerializable` Typ ma nadal nazwie kontraktu danych i przestrzeni nazw. (Jest to określane zgodnie z opisem w [nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md) z tą różnicą, że <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu nie można dostosować nazwę.) Jeśli nie jest anonimowy, musi być jednego z typów w `XmlSchemaSet`. Ten przypadek jest odpowiednikiem zwracanie `XmlQualifiedName` typu.  
  
 Ponadto deklaracji element globalny są eksportowane dla typu. Jeśli typ nie ma <xref:System.Xml.Serialization.XmlRootAttribute> atrybut zastosowany do niego element ma taką samą nazwę i przestrzeń nazw jako kontraktu danych i jego właściwość "nillable" ma wartość true. Jedynym wyjątkiem jest przestrzeń nazw schematu ("http://www.w3.org/2001/XMLSchema") — w przypadku typu kontraktu danych w tej przestrzeni nazw, jest odpowiedni element globalny w przestrzeni nazw puste, ponieważ dodawanie nowych elementów do przestrzeni nazw schematu jest zabronione. Jeśli typ ma `XmlRootAttribute` atrybut zastosowany do jego deklaracji element globalny został wyeksportowany z następującym: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>, <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> i <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> właściwości. Wartości domyślne z `XmlRootAttribute` stosowane są nazwie kontraktu danych, pustą przestrzeń nazw i "nillable" o wartości true.  
  
 Te same zasady deklaracji element globalny dotyczą typów starszej wersji zestawu danych. Należy pamiętać, że `XmlRootAttribute` nie może zastąpić element globalny deklaracje dodane za pomocą kodu niestandardowego, albo dodać do `XmlSchemaSet` przy użyciu metody dostawcy schematu lub za pomocą `GetSchema` dla typów starszej wersji zestawu danych.  
  
### <a name="ixmlserializable-element-types"></a>Typy elementów interfejsu IXmlSerializable  
 `IXmlSerializable` Element typów ma albo `IsAny` ustawioną właściwość `true` lub ma ich zwracać metoda dostawcy schematu `null`.  
  
 Serializację i deserializację typu elementu jest bardzo podobny do serializację i deserializację typu zawartości. Istnieje jednak kilka istotnych różnic:  
  
-   `WriteXml` Implementacji powinien zapisać dokładnie jeden element (który oczywiście może zawierać wielu elementów podrzędnych). Nie powinna być zapisaniem atrybutów poza tym pojedynczy element wielu elementów równorzędnych lub zawartości mieszanej. Element może być pusty.  
  
-   `ReadXml` Implementacji element otoki nie powinny do odczytu. Oczekuje się, aby przeczytać jeden element który `WriteXml` tworzy.  
  
-   Podczas serializowania typu elementu regularnie (na przykład jako element członkowski danych kontraktu danych), serializator danych wyjściowych element otoki przed wywołaniem `WriteXml`, podobnie jak w przypadku typów zawartości. Jednak podczas serializacji typu elementu najwyższego poziomu, Serializator nie zwykle wyprowadza element otoki cały wokół elementu który `WriteXml` zapisuje, chyba że podczas konstruowania serializator jawnie określono nazwę głównej i przestrzeni nazw w `DataContractSerializer` lub `NetDataContractSerializer` konstruktorów. Aby uzyskać więcej informacji, zobacz [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
-   Podczas serializowania typu elementu na najwyższym poziomie bez określania nazwy głównego i przestrzeni nazw podczas konstruowania <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> i <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> zasadniczo nie działa i <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> wywołania `WriteXml`. W tym trybie obiektu poddawanego serializacji nie może mieć wartości null i nie można przypisać polymorphically. Ponadto zachowywania wykres obiektu nie może być włączone i `NetDataContractSerializer` nie można użyć.  
  
-   Podczas deserializacji typu elementu na najwyższym poziomie bez określania nazwy głównego i przestrzeni nazw podczas konstruowania <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> zwraca `true` Jeśli można znaleźć uruchomienia dowolnego elementu. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> z `verifyObjectName` ustawiona `true` działa w taki sam sposób jak `IsStartObject` przed faktycznie czytania obiektu. `ReadObject` następnie przekazuje formantu `ReadXml` metody.  
  
 Schemat wyeksportowane dla typów elementów jest taka sama, jak w przypadku `XmlElement` wpisz zgodnie z opisem w sekcji wcześniej, z wyjątkiem tego, że metoda dostawcy schematu można dodać dodatkowe schematu w celu <xref:System.Xml.Schema.XmlSchemaSet> jako z typami zawartości. Przy użyciu `XmlRootAttribute` atrybutu z typem elementu jest niedozwolone, a element globalny deklaracje nigdy nie są emitowane w przypadku tych typów.  
  
### <a name="differences-from-the-xmlserializer"></a>Różnice z elementu XmlSerializer  
 `IXmlSerializable` Interfejsu i `XmlSchemaProviderAttribute` i `XmlRootAttribute` atrybuty są również zrozumiałe <xref:System.Xml.Serialization.XmlSerializer> . Istnieją pewne różnice w jaki sposób są one traktowane w modelu kontraktu danych. Istotne różnice przedstawiono poniżej:  
  
-   Metoda dostawcy schematu muszą być publiczne, może być używany w `XmlSerializer`, ale nie muszą być publiczne można używać w modelu kontraktu danych.  
  
-   Metoda dostawcy schematu jest wywoływane, gdy `IsAny` ma wartość true w modelu kontraktu danych, lecz nie `XmlSerializer`.  
  
-   Gdy `XmlRootAttribute` atrybut nie ma zawartości lub starszej wersji zestawu danych typów, `XmlSerializer` eksportuje deklaracji element globalny w przestrzeni nazw puste. W modelu danych kontraktu przestrzeni nazw używany jest zwykle przestrzeń nazw kontraktu danych, zgodnie z wcześniejszym opisem.  
  
 Należy pamiętać o tych różnic podczas tworzenia typów, które są używane w obu tych technologii serializacji.  
  
### <a name="importing-ixmlserializable-schema"></a>Importowanie schematu interfejsu IXmlSerializable  
 Podczas importowania schematu wygenerowanego z `IXmlSerializable` typów, istnieje kilka możliwości:  
  
-   Wygenerowany schematu może być schematu kontraktu danych, zgodnie z opisem w [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). W takim przypadku schemat, które mogą być importowane w zwykły sposób i typy kontraktu danych regularne są generowane.  
  
-   Wygenerowany schematu nie może być schematu kontraktu prawidłowe dane. Na przykład schemat metodę dostawca może generować schematu, która obejmuje atrybutów XML, które nie są obsługiwane w modelu kontraktu danych. W takim przypadku można zaimportować schematu jako `IXmlSerializable` typów. Ten tryb importu nie znajduje się na domyślnie, ale można łatwo włączyć — na przykład z `/importXmlTypes` przełącznik wiersza polecenia do [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). To jest szczegółowo opisane w [Importowanie schematu do generowania klasy](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md). Należy pamiętać, że należy skontaktować się bezpośrednio z pliku XML dla swoich wystąpień typu. Można także rozważyć przy użyciu innego serializacji technologia, która obsługuje szerszego zakresu schematu — zobacz temat przy użyciu `XmlSerializer`.  
  
-   Może zajść potrzeba ponownego użycia istniejącą `IXmlSerializable` typy serwera proxy zamiast generowania nowych. W takim przypadku funkcja wskazanych typów opisana w schemacie importowania do generowania typów tematu można wskazać typ do ponownego użycia. Odpowiada to przy użyciu `/reference` Włącz svcutil.exe, który określa zestaw, który zawiera typy do ponownego użycia.  
  
## <a name="representing-arbitrary-xml-in-data-contracts"></a>Reprezentujący swobodną zawartością XML w kontraktach danych  
 `XmlElement`, Tablica `XmlNode` i `IXmlSerializable` typy pozwala na iniekcję swobodną zawartością XML do modelu kontraktu danych. `DataContractSerializer` i `NetDataContractSerializer` przekazać plik XML zawartości do edytora XML w użyciu, bez zakłóceń w procesie. Jednak zapisywania XML może wymusić pewne ograniczenia dotyczące XML, które zapisują. W szczególności Oto kilka przykładów ważne:  
  
-   Autorzy XML nie zezwalaj zwykle deklaracji dokumentu XML (na przykład \<? wersji xml = "1.0"? >) w trakcie wpisywania innego dokumentu. Nie można wykonać pełnego dokumentu XML i serializować go jako `Array` z `XmlNode` element członkowski danych. Aby to zrobić, masz do każdej taśmy w deklaracji dokumentu lub użyj własny schemat kodowania do reprezentowania go.  
  
-   Wszystkie składniki zapisywania XML dostarczony wraz z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Odrzuć instrukcji przetwarzania XML (\<? … ? >) i zarządzania dokumentami definicje typów (\<! … >), ponieważ nie są dozwolone w wiadomości SOAP. Ponownie można użyć własnych kodowania mechanizmu Aby uniknąć problemów tego ograniczenia. Jeśli należy uwzględnić je w wynikowy kod XML, można napisać niestandardowego kodera, który używa zapisywania XML, które je obsługują.  
  
-   Podczas implementowania `WriteXml`, należy unikać wywoływania <xref:System.Xml.XmlWriter.WriteRaw%2A> metoda edytora XML. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa różnych kodowań XML (takie jak dane binarne), jest bardzo trudne lub niemożliwe do użycia `WriteRaw` tak, aby można go użyć w kodowanie był wynik.  
  
-   Podczas implementowania `WriteXml`, należy unikać <xref:System.Xml.XmlWriter.WriteEntityRef%2A> i <xref:System.Xml.XmlWriter.WriteNmToken%2A> metod, które nie są obsługiwane na zapisywania XML dostarczony wraz z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="using-dataset-typed-dataset-and-datatable"></a>Przy użyciu zestawu danych, Typizowanego obiektu DataSet i DataTable  
 Używanie tych typów jest w pełni obsługiwany w modelu kontraktu danych. Korzystając z tych typów, należy wziąć pod uwagę następujące kwestie:  
  
-   Schemat dla typu (szczególnie <xref:System.Data.DataSet> i jego typu klasy pochodne) nie może być współdziała z niektórych z systemem innym niż[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] platformy, lub mogą skutkować niską użyteczność, gdy jest używany z tych platform. Ponadto przy użyciu `DataSet` typ może mieć wpływ na wydajność. Na koniec go może utrudnić automatycznie do wersji aplikacji w przyszłości. Należy rozważyć użycie jawnie zdefiniowanych typów kontraktu zamiast `DataSet` typy w kontraktach użytkownika.  
  
-   Podczas importowania `DataSet` lub `DataTable` schematu, ważne jest, aby te typy referencyjne. Za pomocą narzędzia wiersza polecenia Svcutil.exe, można to zrobić przez przekazanie nazwę zestawu System.Data.dll `/reference` przełącznika. W przypadku importowania schematu typizowanego obiektu dataset musi odwoływać się typ typizowanego obiektu dataset. Z Svcutil.exe, Przekaż lokalizacji zestawu typizowany zestaw danych do `/reference` przełącznika. Aby uzyskać więcej informacji na temat odwoływanie do typów, zobacz [Importowanie schematu do generowania klasy](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 Obsługa typizowane zbiory danych w modelu kontraktu danych jest ograniczona. Typizowane zbiory danych może być Zserializowany deserializacji i wyeksportować schematu. Jednak kontraktu danych importowania schematu nie może wygenerować nowe wpisane typy zestawu danych ze schematu, jak tylko można użyć ponownie już istniejących. Możesz wskazać istniejący zestaw danych typu przy użyciu `/r` Włącz Svcutil.exe. Jeśli próba użycia Svcutil.exe bez `/r` przełącznika od usługi, która używa typizowanego obiektu dataset, alternatywne serializator (XmlSerializer) jest automatycznie wybierany. Jeśli należy użyć elementu DataContractSerializer i należy wygenerować zestawów danych ze schematu, można użyć poniższej procedury: generowania typizowanych typów zestawu danych (za pomocą narzędzia Xsd.exe z `/d` Włącz usługę), skompilować typów, a następnie wskaż pozycję je przy użyciu `/r` Włącz Svcutil.exe.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Typy obsługiwane przez serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)

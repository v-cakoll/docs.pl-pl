---
title: Używanie klasy XmlSerializer
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XmlSerializer [WCF], using
ms.assetid: c680602d-39d3-44f1-bf22-8e6654ad5069
ms.openlocfilehash: 29ce9b165c3823d7d06008431294f67716ccf8e1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105446"
---
# <a name="using-the-xmlserializer-class"></a>Używanie klasy XmlSerializer
Windows Communication Foundation (WCF) można użyć dwóch technologii serializacji w różnych, aby przekształcać dane w aplikacji do formatu XML, które są przesyłane między klientami i usług, w procesie zwanym serializacji.  
  
## <a name="datacontractserializer-as-the-default"></a>DataContractSerializer jako domyślny  
 Domyślnie używa WCF <xref:System.Runtime.Serialization.DataContractSerializer> klasy do serializacji typów danych. Przez ten serializator obsługuje następujące typy:  
  
-   Typy pierwotne (na przykład liczby całkowite, ciągi i bajtów tablice), a także niektóre typy specjalne, takie jak <xref:System.Xml.XmlElement> i <xref:System.DateTime>, które są traktowane jako elementów podstawowych.  
  
-   Typy kontraktów danych (typy oznaczone <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu).  
  
-   Typy oznaczone <xref:System.SerializableAttribute> atrybut, który zawierają typami, które implementują <xref:System.Runtime.Serialization.ISerializable> interfejsu.  
  
-   Typami, które implementują <xref:System.Xml.Serialization.IXmlSerializable> interfejsu.  
  
-   Wiele typowych kolekcji typów, które obejmują wiele typów kolekcji ogólnej.  
  
 Wiele [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów można podzielić na dwie ostatnie kategorie i dlatego są możliwe do serializacji. Tablice typów możliwych do serializacji są również możliwe do serializacji. Aby uzyskać pełną listę, zobacz [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>, Używana wraz z danymi typy kontraktu, jest zalecanym sposobem pisania nowych usług WCF. Aby uzyskać więcej informacji, zobacz [za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## <a name="when-to-use-the-xmlserializer-class"></a>Kiedy należy używać klasy XmlSerializer  
 Obsługuje również WCF <xref:System.Xml.Serialization.XmlSerializer> klasy. <xref:System.Xml.Serialization.XmlSerializer> Klasy nie jest unikatowy dla usługi WCF. Serializacja tego samego aparatu, który jest [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] użycia usług sieci Web. <xref:System.Xml.Serialization.XmlSerializer> Klasa obsługuje znacznie mniejszą niż zestaw typów niż <xref:System.Runtime.Serialization.DataContractSerializer> klasy, ale zapewnia większą kontrolę nad wynikowy kod XML i obsługuje znacznie więcej język definicji schematu XML (XSD) standardowa. Ponadto nie wymaga żadnych deklaratywne atrybuty typów możliwych do serializacji. Aby uzyskać więcej informacji, zobacz temat serializacji XML w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dokumentacji. <xref:System.Xml.Serialization.XmlSerializer> Klasa nie obsługuje typy kontraktu danych.  
  
 Korzystając z Svcutil.exe lub **Dodaj odwołanie do usługi** funkcji w programie Visual Studio do generowania kodu klienta dla usługi innych firm oraz do schematów innych firm, odpowiedni element serializujący została wybrana automatycznie. Jeśli schemat nie jest zgodny z <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Xml.Serialization.XmlSerializer> jest zaznaczone.  
  
## <a name="manually-switching-to-the-xmlserializer"></a>Ręczne przełączanie się do elementu XmlSerializer  
 Czasami może być konieczne ręcznie przełączysz się do <xref:System.Xml.Serialization.XmlSerializer>. Dzieje się tak, na przykład w następujących przypadkach:  
  
-   Podczas migracji aplikacji z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usług sieci Web WCF, może zajść potrzeba ponownego użycia istniejącej, <xref:System.Xml.Serialization.XmlSerializer>— typy kontraktów zgodnych typów, zamiast tworzyć nowe dane.  
  
-   Gdy precyzyjną kontrolę nad tym XML, który pojawia się w wiadomościach jest ważne, ale dokument usługi sieci Web Services Description Language (WSDL) nie jest dostępny, na przykład podczas tworzenia usługi przy użyciu typów, które mają się pewnych standardowych, opublikowanych schematu to nie jest zgodna z elementu DataContractSerializer.  
  
-   Podczas tworzenia usługi, które są zgodne ze standardem starszych kodowaniem SOAP.  
  
 W tych i innych przypadkach, można ręcznie przełączysz się do <xref:System.Xml.Serialization.XmlSerializer> klasy, stosując `XmlSerializerFormatAttribute` atrybutu do swojej usługi, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_XmlSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#1)]
 [!code-vb[c_XmlSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#1)]  
  
## <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
  
> [!NOTE]
>  Koniecznie należy zachować ostrożność podczas przełączania aparatów serializacji. Ten sam typ może wykonywać serializację do pliku XML inaczej w zależności od serializator używany. Korzystając z przypadkiem niewłaściwy serializator, może być ujawnieniu informacji z typu, który nie ma konieczności ujawnienia.  
  
 Na przykład <xref:System.Runtime.Serialization.DataContractSerializer> klasy serializuje tylko składowe oznaczone za pomocą <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu podczas serializacji typy kontraktu danych. <xref:System.Xml.Serialization.XmlSerializer> Klasy serializuje żadnego publicznego elementu członkowskiego. Zobacz typ w poniższym kodzie.  
  
 [!code-csharp[c_XmlSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#2)]
 [!code-vb[c_XmlSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#2)]  
  
 Jeśli typ jest nieodwracalnie używany w kontrakcie usługi gdzie <xref:System.Xml.Serialization.XmlSerializer> wybrano klasy `creditCardNumber` elementu członkowskiego jest serializowana, który prawdopodobnie nie jest przeznaczony.  
  
 Mimo że <xref:System.Runtime.Serialization.DataContractSerializer> klasy jest ustawieniem domyślnym, możesz jawnie wybrać go dla usługi (mimo że to nigdy nie powinno być wymagane), stosując <xref:System.ServiceModel.DataContractFormatAttribute> atrybutu typu kontraktu usługi.  
  
 Serializator używany przez usługę jest integralną częścią kontraktu i nie można zmienić, wybierając inne powiązanie lub zmieniając innych ustawień konfiguracyjnych.  
  
 Inne ważne zagadnienia dotyczące bezpieczeństwa dotyczą <xref:System.Xml.Serialization.XmlSerializer> klasy. Po pierwsze, zdecydowanie zaleca się że każda aplikacja usługi WCF, używa <xref:System.Xml.Serialization.XmlSerializer> klasy jest podpisany za pomocą klucza, które są chronione przed ujawnieniem. To zalecenie dotyczy zarówno podczas ręcznego przełączenia do <xref:System.Xml.Serialization.XmlSerializer> jest wykonywane i kiedy przełącznik automatyczne jest wykonywane (przez Svcutil.exe, Dodaj odwołanie do usługi lub podobnego narzędzia). Jest to spowodowane <xref:System.Xml.Serialization.XmlSerializer> mechanizm serializacji obsługuje ładowanie *wstępnie wygenerowane zestawy serializacji* tak długo, jak są one podpisane za pomocą tego samego klucza, co aplikacja. Niepodpisana aplikacja nie jest całkowicie chroniony, z możliwością złośliwemu zestawowi pasującą do oczekiwanej nazwy zestawu wstępnie wygenerowanego serializacji, są umieszczane w folderze aplikacji lub w globalnej pamięci podręcznej. Oczywiście osoba atakująca musi najpierw uzyskać dostęp do zapisu do jednej z tych dwóch lokalizacjach próby tej akcji.  
  
 Istnieje zawsze wtedy, gdy używasz innego zagrożenia <xref:System.Xml.Serialization.XmlSerializer> powiązany jest dostęp do zapisu do folderu tymczasowego systemu. <xref:System.Xml.Serialization.XmlSerializer> Mechanizm serializacji tworzenia i tymczasowego *zestawy serializacji* w tym folderze. Należy pamiętać, że żaden proces z dostępem do zapisu do folderu tymczasowego może zastąpić te zestawy serializacji złośliwego kodu.  
  
## <a name="rules-for-xmlserializer-support"></a>Obsługuje reguły dla elementu XmlSerializer  
 Nie można zastosować bezpośrednio <xref:System.Xml.Serialization.XmlSerializer>-niezgodne atrybuty kontrakt operacji parametrów lub zwracanych wartości. Jednak one mogą być stosowane do wpisane wiadomości (części treści kontraktu komunikatu,) jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_XmlSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#3)]
 [!code-vb[c_XmlSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#3)]  
  
 Gdy jest stosowany do elementów członkowskich wpisany komunikat, te atrybuty zastąpić właściwości, które powodują konflikt w atrybutach wpisany komunikat. Na przykład w poniższym kodzie `ElementName` zastępuje `Name`.  
  
 [!code-csharp[c_XmlSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#4)]
 [!code-vb[c_XmlSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#4)]  
  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute> Atrybut nie jest obsługiwany w przypadku korzystania z <xref:System.Xml.Serialization.XmlSerializer>.  
  
> [!NOTE]
>  W tym przypadku <xref:System.Xml.Serialization.XmlSerializer> zgłasza następujący wyjątek, który jest wydane przed WCF: "Element zadeklarowany na najwyższym poziomie schematu nie może mieć `maxOccurs` > 1. Dostarcz element otoki, aby uzyskać więcej, korzystając z `XmlArray` lub `XmlArrayItem` zamiast `XmlElementAttribute`, lub używając stylu parametru Wrapped. "  
>   
>  Jeśli wystąpi wyjątek od tej zasady należy zbadać, czy w takiej sytuacji.  
  
 Usługi WCF nie obsługuje <xref:System.Xml.Serialization.SoapIncludeAttribute> i <xref:System.Xml.Serialization.XmlIncludeAttribute> umów dotyczących atrybutów w kontrakty komunikatów i operacji; użyj <xref:System.Runtime.Serialization.KnownTypeAttribute> zamiast tego atrybutu.  
  
## <a name="types-that-implement-the-ixmlserializable-interface"></a>Typy implementujące interfejs IXmlSerializable  
 Typami, które implementują `IXmlSerializable` interfejsu są w pełni obsługiwane przez `DataContractSerializer`. <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> Zawsze można zastosować atrybutu do tych typów w celu kontrolowania swoich schematu.  
  
> [!WARNING]
>  Jeśli są serializacji polimorficzne typy należy zastosować <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> do typu, aby zapewnić poprawny typ jest serializowana.  
  
 Istnieją trzy różne typy typy, które implementują `IXmlSerializable`: typy, które reprezentują arbitralnie wybrane typy zawartości, reprezentujących pojedynczy element, a starsza wersja <xref:System.Data.DataSet> typów.  
  
-   Typy zawartości, użyj metody dostawcy schemat określony przez `XmlSchemaProviderAttribute` atrybutu. Metoda nie zwraca `null` i <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> właściwości w atrybucie pozostanie ustawiony na wartość domyślną `false`. Jest to najbardziej typowe użycie `IXmlSerializable` typów.  
  
-   Typy elementów są używane podczas `IXmlSerializable` typu musi kontrolować własną nazwą elementu głównego. Aby oznaczyć typu jako typu elementu, ustaw wartość <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> właściwość <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybutu `true` lub je zwracają `null` z metody dostawcy schematu. Posiadanie metody dostawcy schematu jest opcjonalne dla typów elementów — użytkownik może określić `null` zamiast nazwy metody w `XmlSchemaProviderAttribute`. Jednak jeśli `IsAny` jest `true` i metody dostawcy schemat jest określony, metoda musi zwracać `null`.  
  
-   Starsza wersja <xref:System.Data.DataSet> typy są `IXmlSerializable` typy, które nie są oznaczone przez `XmlSchemaProviderAttribute` atrybutu. Zamiast tego opierają się na <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> metody do generowania schemat. Ten wzorzec jest używany dla `DataSet` typu i jego typizowany zestaw danych pochodzi z klasy we wcześniejszych wersjach programu .NET Framework, ale teraz jest przestarzały i nie jest obsługiwana tylko dla starszych powodów. Nie zależą od tego wzorca i zawsze stosuj `XmlSchemaProviderAttribute` do Twojej `IXmlSerializable` typów.  
  
### <a name="ixmlserializable-content-types"></a>Typy zawartości IXmlSerializable  
 Podczas serializacji typu, który implementuje element członkowski danych `IXmlSerializable` jest typ zawartości zdefiniowany wcześniej serializator zapisuje element otoki dla składowej danych i przekazuje kontrolę <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Implementacji może zapisywać żadnych XML, który obejmuje dodawanie atrybutów do elementu otoki. Po `WriteXml` jest wykonywane, serializator zamyka element.  
  
 Podczas deserializacji składowej danych typu, który implementuje `IXmlSerializable` jest typ zawartości zdefiniowany wcześniej, Deserializator umieszcza odczytującego XML element otoki dla składowej danych i przekazuje kontrolę <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metody. Metoda musi odczytać cały element, w tym tagiem początkowym i końcowym. Upewnij się, że Twoje `ReadXml` kod obsługuje przypadek, w której element jest pusty. Ponadto usługi `ReadXml` wdrożenia nie należy polegać na element otoki jest o nazwie określony sposób. Nazwa jest wybierany przez serializator może się różnić.  
  
 Dopuszcza się przypisać `IXmlSerializable` zawartości typów polymorphically, na przykład, aby dane elementy członkowskie typu <xref:System.Object>. Jest również dozwolony w przypadku wystąpień typu to null. Na koniec istnieje możliwość użycia `IXmlSerializable` typów z zachowania wykresu obiektu włączone i <xref:System.Runtime.Serialization.NetDataContractSerializer>. Wszystkie te funkcje wymagają serializator WCF można dołączyć niektóre atrybuty do element otoki ("zero" i "type" w przestrzeni nazw z wystąpienia schematu XML i "Id", "Ref", "Type" i "Assembly" w przestrzeni nazw specyficzne dla programu WCF).  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>Atrybuty do zignorowania podczas implementowania ReadXml  
 Przed przekazaniem kontroli do Twojej `ReadXml` kod, Deserializator sprawdza, czy XML element, wykrywa te atrybuty specjalne XML i działa na nich. Na przykład, jeśli jest "zero" `true`, wartość null jest przeprowadzona i `ReadXml` nie zostanie wywołana. W przypadku wykrycia polimorfizm zawartość elementu są deserializacji, tak jakby znajdowała się innego typu. Implementacja typu polymorphically przypisane `ReadXml` jest wywoływana. W każdym przypadku `ReadXml` wdrożenia powinien ignorować te atrybuty specjalne, ponieważ są one obsługiwane przez deserializacji.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>Zagadnienia schematu dla typów IXmlSerializable zawartości  
 Podczas eksportowania schematu i `IXmlSerializable` typ zawartości, wywoływana jest metoda dostawcy schematu. <xref:System.Xml.Schema.XmlSchemaSet> Jest przekazywany do metody dostawcy schematu. Metoda można dodać żadnych prawidłowego schematu do zestawu schematów. Zestaw schematów zawiera schemat, który jest już znany w czasie, gdy wystąpi eksportu schematu. Gdy metoda dostawcy schematu musi dodać element do zestawu schematów, należy określić czy <xref:System.Xml.Schema.XmlSchema> przy użyciu odpowiedniego obszaru nazw już istnieje w zestawie. Jeśli tak jest, metody dostawcy schemat, należy dodać nowy element do istniejącej `XmlSchema`. W przeciwnym razie należy utworzyć nowy `XmlSchema` wystąpienia. Jest to ważne, jeśli tablice `IXmlSerializable` typów są używane. Na przykład, jeśli masz `IXmlSerializable` typ, który pobiera wyeksportowany jako typu "A" w przestrzeni nazw "B", możliwe, że do czasu, wywoływana jest metoda dostawcy schematu, schemat już skonfigurowane zawiera schemat "B" pomieścić typu "ArrayOfA".  
  
 Oprócz dodawania typów <xref:System.Xml.Schema.XmlSchemaSet>, metodę dostawcy schematu dla typów zawartości musi zwracać wartość inną niż null. Może zwracać <xref:System.Xml.XmlQualifiedName> określający nazwę typu schematu do użycia dla danego `IXmlSerializable` typu. Ta nazwa kwalifikowana służy również jako dane kontraktu nazwy i przestrzeni nazw dla typu. Dozwolone jest zwracany typ, który nie istnieje w schemacie zestawu natychmiast, po powrocie z metody dostawcy schematu. Jednak oczekuje się, że po czasie wszystkie powiązane typy są eksportowane ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> metoda jest wywoływana dla wszystkich odpowiednich typów w <xref:System.Runtime.Serialization.XsdDataContractExporter> i <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> dostępu do właściwości), typ istnieje w zestawie schematów. Uzyskiwanie dostępu do `Schemas` właściwości przed wszystkimi odpowiednimi `Export` wprowadzono wywołań może spowodować <xref:System.Xml.Schema.XmlSchemaException>. Aby uzyskać więcej informacji na temat procesu eksportu, zobacz [eksportowanie schematów z klas](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
 Metoda dostawcy schemat może również zwracać <xref:System.Xml.Schema.XmlSchemaType> do użycia. Typ może być lub może nie być anonimowy. Jeśli jest anonimowe, schemat `IXmlSerializable` typu jest eksportowana jako typ anonimowy w każdym `IXmlSerializable` typ jest używany jako element członkowski danych. `IXmlSerializable` Typu środki, nieopłacone nazwie kontraktu danych i przestrzeni nazw. (To jest określana zgodnie z opisem w [nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md) z tą różnicą, że <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu nie można dostosować nazwę.) Jeśli nie jest anonimowe, musi być jednym z typów w `XmlSchemaSet`. Ten przypadek jest odpowiednikiem zwracanie `XmlQualifiedName` tego typu.  
  
 Ponadto deklaracji element globalny jest eksportowany dla typu. Jeśli typ nie ma <xref:System.Xml.Serialization.XmlRootAttribute> zastosowany do niego element ma taką samą nazwę i obszaru nazw kontraktu danych, a jego właściwość "nillable" ma `true`. Jedynym wyjątkiem jest przestrzeń nazw schematu (`http://www.w3.org/2001/XMLSchema`) — w przypadku typu kontraktu danych w tej przestrzeni nazw, odpowiedni element globalny jest w pustej przestrzeni nazw, ponieważ jest zabroniona Dodawanie nowych elementów do przestrzeni nazw schematu. Jeśli typ ma `XmlRootAttribute` zastosowany do jego deklaracji elementu globalnego jest eksportowana za pomocą następujących: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>, <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> i <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> właściwości. Ustawienia domyślne przy użyciu `XmlRootAttribute` stosowane są nazwie kontraktu danych, pustą przestrzeń nazw, a jest "nillable" `true`.  
  
 Te same reguły element globalny w deklaracji mają zastosowanie do zestawu danych w starszej wersji typów. Należy pamiętać, że `XmlRootAttribute` nie może przesłonić element globalny deklaracje dodane poprzez kod niestandardowy być dodany do `XmlSchemaSet` przy użyciu metody dostawcy schematu lub za pomocą `GetSchema` dla typów starszej wersji zestawu danych.  
  
### <a name="ixmlserializable-element-types"></a>Typy elementów interfejsu IXmlSerializable  
 `IXmlSerializable` typy elementów mieć `IsAny` właściwością `true` lub ich dostawcy schematu, metoda zwraca `null`.  
  
 Serializacja i deserializacja typ elementu jest bardzo podobny do serializacji i deserializacji typu zawartości. Jednak istnieją pewne ważne różnice:  
  
-   `WriteXml` Implementacji oczekuje się, można zapisać dokładnie jeden element (który z kolei może zawierać wiele elementów podrzędnych). Nie powinien być wpisywanie atrybutów poza ten pojedynczy element wielu elementów równorzędnych lub zawartość mieszana. Element może być pusty.  
  
-   `ReadXml` Implementacji element otoki nie powinny do odczytu. Oczekuje się, aby przeczytać jeden element, `WriteXml` tworzy.  
  
-   Podczas serializacji typu elementu regularnie (na przykład, jako element członkowski danych w kontraktu danych), serializator danych wyjściowych element otoki przed wywołaniem `WriteXml`, podobnie jak w przypadku typów zawartości. Jednak podczas serializacji typu elementu na najwyższym poziomie, Serializator nie zwykle wyświetla element otoki w ogóle wokół elementu, `WriteXml` zapisuje, chyba że nazwę główną i przestrzeni nazw są jawnie określone podczas tworzenia serializatora w `DataContractSerializer` lub `NetDataContractSerializer` konstruktorów. Aby uzyskać więcej informacji, zobacz [serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
-   Podczas serializacji typu elementu na najwyższym poziomie bez określania nazwy głównej i przestrzeni nazw w czasie tworzenia <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> i <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> zasadniczo nic nie rób i <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> wywołania `WriteXml`. W tym trybie nie może być obiektu poddawanego serializacji `null` i nie można przypisać polymorphically. Ponadto nie można włączyć zachowania wykresu obiektu i `NetDataContractSerializer` nie mogą być używane.  
  
-   Podczas deserializacji typ elementu na najwyższym poziomie bez określania nazwy głównej i przestrzeni nazw w czasie tworzenia <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> zwraca `true` jeśli znajdzie uruchamiania dowolnego elementu. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> za pomocą `verifyObjectName` parametr `true` zachowuje się w taki sam sposób jak `IsStartObject` przed faktycznie odczytu obiektu. `ReadObject` następnie przekazuje sterowanie do `ReadXml` metody.  
  
 Schemat eksportowany dla typów elementów jest taki sam, jak w przypadku `XmlElement` wpisz zgodnie z opisem w sekcji wcześniej, z tą różnicą, że metoda dostawcy schematu można dodać dodatkowe schematu w celu <xref:System.Xml.Schema.XmlSchemaSet> podobnie jak w przypadku typów zawartości. Za pomocą `XmlRootAttribute` atrybut z typami elementu nie jest dozwolony, a element globalny deklaracje nigdy nie są emitowane dla tych typów.  
  
### <a name="differences-from-the-xmlserializer"></a>Różnice w stosunku do elementu XmlSerializer  
 `IXmlSerializable` Interfejsu i `XmlSchemaProviderAttribute` i `XmlRootAttribute` atrybuty są także zrozumiałe <xref:System.Xml.Serialization.XmlSerializer> . Jednak istnieją pewne różnice w jaki sposób są one traktowane w modelu kontraktu danych. Istotne różnice przedstawiono na poniższej liście:  
  
-   Metody dostawcy schematu muszą być publiczne, które zostaną użyte w `XmlSerializer`, ale nie musi być publiczne, które zostaną użyte w modelu kontraktu danych.  
  
-   Metoda dostawcy schematu jest wywoływana, gdy `IsAny` jest `true` w modelu kontraktu danych, ale nie z `XmlSerializer`.  
  
-   Gdy `XmlRootAttribute` atrybut nie jest obecny do zawartości lub typy zestawów danych w starszej wersji, `XmlSerializer` eksportuje deklaracji element globalny w pustej przestrzeni nazw. W modelu kontraktu danych przestrzeń nazw używaną zwykle jest przestrzeń nazw kontraktu danych, zgodnie z wcześniejszym opisem.  
  
 Należy pamiętać o tych różnic, podczas tworzenia typów, które są używane w obu technologii serializacji.  
  
### <a name="importing-ixmlserializable-schema"></a>Importowanie schematu interfejsu IXmlSerializable  
 Podczas importowania schematu wygenerowany na podstawie `IXmlSerializable` typów, istnieje kilka możliwości:  
  
-   Wygenerowany schemat może być schematu kontraktu prawidłowych danych, zgodnie z opisem w [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). W takim przypadku schematu, które mogą być importowane w zwykły sposób, i są generowane typy kontraktu danych regularne.  
  
-   Wygenerowany schemat może nie być poprawne dane schematu kontraktu. Na przykład metoda dostawcy schematu może wygenerować schematu, która obejmuje atrybutów XML, które nie są obsługiwane w modelu kontraktu danych. W takim przypadku można zaimportować schematu jako `IXmlSerializable` typów. Domyślnie nie jest w ten tryb importu, ale można łatwo można włączyć — na przykład za pomocą `/importXmlTypes` przełącznik wiersza polecenia, aby [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Jest to opisane szczegółowo w temacie [Importowanie schematu do generowania klasy](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md). Należy pamiętać, że należy skontaktować się bezpośrednio z pliku XML dla wystąpień typu. Można także rozważyć użycie innej technologii serializacji, który obsługuje szerszy zakres schematów — zobacz temat w przy użyciu `XmlSerializer`.  
  
-   Może zajść potrzeba ponownego użycia istniejącej `IXmlSerializable` typów serwera proxy zamiast generować nową. W takim przypadku funkcja przywoływane typy opisana w schemacie importowanie do tematu wygenerować typy można wskazać typ do ponownego użycia. Odpowiada to użyciu `/reference` Włącz svcutil.exe, który określa zestaw, który zawiera typy do ponownego użycia.  
  
### <a name="xmlserializer-legacy-behavior"></a>Zachowanie elementu XmlSerializer starszej wersji  
 W .NET Framework 4.0 i starszych elementu XmlSerializer wygenerowane zestawy serializacji tymczasowych przez napisanie kodu języka C# do pliku. Plik został następnie kompilowane do zestawu.  To zachowanie ma niektórych niepożądanych skutków, takich jak spowalnianiu czas uruchamiania dla serializatora. W programie .NET Framework 4.5 to zachowanie została zmieniona na generowanie zestawów bez konieczności użycia kompilatora. Niektórzy deweloperzy mogą chcieć wyświetlić wygenerowany kod C#. Możesz określić to starsze zachowanie za pomocą następującej konfiguracji:  
  
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
  
 Jeśli napotkasz problemy ze zgodnością, takich jak `XmlSerializer` kończy się niepowodzeniem do serializacji klasę pochodną z możliwością zmiany nowych niepublicznych, możesz przełączyć się ponownie do `XMLSerializer` starsze zachowanie za pomocą następującej konfiguracji:  
  
```xml  
<configuration>  
<appSettings>   
<add key="System:Xml:Serialization:UseLegacySerializerGeneration" value="true" />  
               </appSettings>  
</configuration>  
```  
  
 Jako alternatywę do powyższych konfiguracji można użyć następującej konfiguracji na komputerze z systemem .NET Framework 4.5 lub nowszej wersji:  
  
```xml  
<configuration>  
<system.xml.serialization>  
<xmlSerializer useLegacySerializerGeneration="true"/>  
</system.xml.serialization>  
</configuration>  
```  
  
> [!NOTE]
>  `<xmlSerializer useLegacySerializerGeneration="true"/>` Przełącznika działa tylko na komputerze z systemem .NET Framework 4.5 lub nowszej wersji. Powyższe `appSettings` podejście działa we wszystkich wersjach systemu .NET Framework.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.DataContractFormatAttribute>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.ServiceModel.MessageHeaderArrayAttribute>
- [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
- [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Instrukcje: skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)

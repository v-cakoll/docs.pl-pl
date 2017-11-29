---
title: "Używanie klasy XmlSerializer"
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
helpviewer_keywords: XmlSerializer [WCF], using
ms.assetid: c680602d-39d3-44f1-bf22-8e6654ad5069
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5adcf8e6e992d0ae6f6de487b8e671a0b2db16f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-the-xmlserializer-class"></a>Używanie klasy XmlSerializer
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]można użyć dwóch różnych serializacji technologii włączyć danych w aplikacji w formacie XML, który są przesyłane między klientami i usług, w procesie nazywanym serializacji.  
  
## <a name="datacontractserializer-as-the-default"></a>DataContractSerializer jako domyślny  
 Domyślnie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa <xref:System.Runtime.Serialization.DataContractSerializer> klasy do serializacji typów danych. Serializator obsługuje następujące typy:  
  
-   Typy pierwotne (na przykład, liczb całkowitych, ciągów i bajtów tablic), a także niektóre typy specjalne, takie jak <xref:System.Xml.XmlElement> i <xref:System.DateTime>, które są traktowane jako typów podstawowych.  
  
-   Typy kontraktu danych (oznaczonej jako typy <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu).  
  
-   Typy oznaczone <xref:System.SerializableAttribute> atrybut, który obejmują typy, które implementują <xref:System.Runtime.Serialization.ISerializable> interfejsu.  
  
-   Typy, które implementują <xref:System.Xml.Serialization.IXmlSerializable> interfejsu.  
  
-   Wiele typowych kolekcji typów, która obejmuje wiele typy kolekcji ogólnych.  
  
 Wiele [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typów można podzielić na dwie ostatnie kategorie i w związku z tym jest możliwy do serializacji. Tablice typów możliwych do serializacji są również do serializacji. Aby uzyskać pełną listę, zobacz [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>, Używać razem z danych typy kontraktu, jest to zalecany sposób, aby zapisać nowe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Za pomocą kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## <a name="when-to-use-the-xmlserializer-class"></a>Kiedy należy używać klasy XmlSerializer  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje również <xref:System.Xml.Serialization.XmlSerializer> klasy. <xref:System.Xml.Serialization.XmlSerializer> Klasa nie jest unikatowa dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Serializacja tego samego silnika, który jest [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] użycia usług sieci Web. <xref:System.Xml.Serialization.XmlSerializer> Klasa obsługuje znacznie mniejszą niż zestaw typów niż <xref:System.Runtime.Serialization.DataContractSerializer> klasy, ale zapewnia większą kontrolę nad wynikowy kod XML i obsługuje większą schematu XML definicji języka (XSD) standardowa. Ponadto nie wymaga żadnych atrybutów deklaratywne dla typów możliwych do serializacji. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]w temacie serializacja XML [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dokumentacji. <xref:System.Xml.Serialization.XmlSerializer> Klasa nie obsługuje typy kontraktu danych.  
  
 Korzystając z Svcutil.exe lub **Dodaj odwołanie do usługi** w narzędziu [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] generowanie kodu klienta dla usługi innej firmy, lub uzyskiwania dostępu do innych firm schematu, odpowiedni serializator jest automatycznie wybrana. Jeśli schemat nie jest zgodny z <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Xml.Serialization.XmlSerializer> jest zaznaczone.  
  
## <a name="manually-switching-to-the-xmlserializer"></a>Ręczne przełączanie dla elementu XmlSerializer  
 Czasami może być konieczne ręczne przełączanie do <xref:System.Xml.Serialization.XmlSerializer>. Dzieje się tak, na przykład w następujących przypadkach:  
  
-   Podczas migracji aplikacji z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] usług sieci Web do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], może zajść potrzeba ponownego użycia istniejącej, <xref:System.Xml.Serialization.XmlSerializer>— typy kontraktu niezgodne typy zamiast tworzyć nowe dane.  
  
-   Jeśli ważne jest ścisła kontrola nad XML, która jest wyświetlana w wiadomości, ale nie jest dokumentem usługi sieci Web Services Description Language (WSDL), na przykład podczas tworzenia usługi przy użyciu typów, które mają się niektórych standardowych, opublikowanych schematu to nie jest zgodne z elementu DataContractSerializer.  
  
-   Podczas tworzenia usługi, które są zgodne ze standardem starszych kodowania protokołu SOAP.  
  
 W tych i innych przypadkach można ręcznie przełączyć <xref:System.Xml.Serialization.XmlSerializer> przy zastosowaniu `XmlSerializerFormatAttribute` atrybutu z usługą, jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_XmlSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#1)]
 [!code-vb[c_XmlSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#1)]  
  
## <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
  
> [!NOTE]
>  Należy zachować ostrożność podczas przełączania aparaty serializacji. Tego samego typu można szeregować do XML inaczej w zależności od serializator używany. Użycie przypadkowo niewłaściwy serializator może być ujawnieniu informacji z typu, który nie ma ujawnić.  
  
 Na przykład <xref:System.Runtime.Serialization.DataContractSerializer> klasy serializuje tylko elementy członkowskie oznaczone <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutu podczas serializacji typy kontraktu danych. <xref:System.Xml.Serialization.XmlSerializer> Klasy serializuje żadnego członka publicznego. Zobacz typ w poniższym kodzie.  
  
 [!code-csharp[c_XmlSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#2)]
 [!code-vb[c_XmlSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#2)]  
  
 Jeśli typ przypadkowo jest używany w kontrakcie usługi gdzie <xref:System.Xml.Serialization.XmlSerializer> wybrano klasy `creditCardNumber` serializować elementu członkowskiego, który prawdopodobnie nie jest przeznaczony.  
  
 Mimo że <xref:System.Runtime.Serialization.DataContractSerializer> klasy jest ustawieniem domyślnym, jawnie wybrać go usługi (mimo że ten sposób nigdy nie należy wymagać), stosując <xref:System.ServiceModel.DataContractFormatAttribute> atrybutu typu kontraktu usługi.  
  
 Serializator używany przez usługę jest integralną częścią kontraktu i nie można zmienić, wybierając inne powiązanie lub zmieniając innych ustawień konfiguracyjnych.  
  
 Inne ważne zagadnienia dotyczące zabezpieczeń dotyczą <xref:System.Xml.Serialization.XmlSerializer> klasy. Po pierwsze, zalecane jest aby każda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji, która używa <xref:System.Xml.Serialization.XmlSerializer> klasy jest podpisany przy użyciu klucza, który jest chronione przed ujawnieniem. To zalecenie dotyczy zarówno ręczne przełączenie do <xref:System.Xml.Serialization.XmlSerializer> jest wykonywane podczas automatycznego przełącznik jest przeprowadzane (przez Svcutil.exe, Dodaj odwołanie do usługi lub podobnego narzędzia). Jest to spowodowane <xref:System.Xml.Serialization.XmlSerializer> aparat serializacji obsługuje ładowania *wstępnie wygenerowanego zestawów serializacji* tak długo, jak są podpisane przy użyciu tego samego klucza aplikacji. Niepodpisana aplikacja jest całkowicie chroniony z możliwości złośliwego zestawu pasującego do oczekiwanej nazwy zestawu serializacji wstępnie wygenerowane znajdują się w folderze aplikacji lub w globalnej pamięci podręcznej zestawów. Oczywiście osoba atakująca musi najpierw uzyskać dostęp do zapisu do jednej z tych dwóch lokalizacjach próba ta akcja.  
  
 Inny zagrożeń, czy istnieje zawsze, gdy używasz <xref:System.Xml.Serialization.XmlSerializer> powiązany jest dostęp do zapisu do folderu tymczasowego systemu. <xref:System.Xml.Serialization.XmlSerializer> Mechanizm serializacji tworzone i używane tymczasowego *zestawów serializacji* w tym folderze. Należy zwrócić uwagę, czy każdy proces z prawem do zapisu do folderu tymczasowego może zastąpić te zestawy serializacji złośliwego kodu.  
  
## <a name="rules-for-xmlserializer-support"></a>Zasady pomocy technicznej XmlSerializer  
 Nie można zastosować bezpośrednio <xref:System.Xml.Serialization.XmlSerializer>-niezgodne atrybuty kontraktu operacji parametrów lub zwracanych wartości. Jednak ich można można zastosować do typu wiadomości (części treści kontraktu komunikatu,) jak pokazano w poniższym kodzie.  
  
 [!code-csharp[c_XmlSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#3)]
 [!code-vb[c_XmlSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#3)]  
  
 Gdy jest stosowany do elementów członkowskich komunikatu o określonym typie, te atrybuty zastąpienie właściwości, które powodują konflikt w atrybutach komunikatu o określonym typie. Na przykład w poniższym kodzie `ElementName` zastępuje `Name`.  
  
 [!code-csharp[c_XmlSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#4)]
 [!code-vb[c_XmlSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#4)]  
  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute> Atrybut nie jest obsługiwany w przypadku korzystania z <xref:System.Xml.Serialization.XmlSerializer>.  
  
> [!NOTE]
>  W takim przypadku <xref:System.Xml.Serialization.XmlSerializer> następujące wyjątek, który zostanie zwolniony przed [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: "element zadeklarowany na najwyższym poziomie schematu nie może mieć `maxOccurs` > 1. Określ element otoki dla więcej, za pomocą `XmlArray` lub `XmlArrayItem` zamiast `XmlElementAttribute`, lub używając stylu parametru Wrapped. "  
>   
>  Jeśli zostanie wyświetlony taki wyjątek, sprawdź, czy w takiej sytuacji.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]nie obsługuje <xref:System.Xml.Serialization.SoapIncludeAttribute> i <xref:System.Xml.Serialization.XmlIncludeAttribute> umów atrybutów w kontraktach komunikat i operację; użyj <xref:System.Runtime.Serialization.KnownTypeAttribute> zamiast tego atrybutu.  
  
## <a name="types-that-implement-the-ixmlserializable-interface"></a>Typy implementujące interfejs IXmlSerializable  
 Typy, które implementują `IXmlSerializable` interfejsu są w pełni obsługiwane przez `DataContractSerializer`. <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> Zawsze można zastosować atrybutu do tych typów, aby kontrolować ich schematu.  
  
> [!WARNING]
>  Jeśli są serializacji typach polimorficznych należy zastosować <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> do typu w celu zapewnienia poprawnego typu jest serializowany.  
  
 Istnieją trzy różne typy typów, które implementują `IXmlSerializable`: typy, które reprezentują dowolne typy zawartości, które reprezentują pojedynczy element i starszych <xref:System.Data.DataSet> typów.  
  
-   Typy zawartości należy użyć metody dostawcy schematu, określony przez `XmlSchemaProviderAttribute` atrybutu. Metoda nie zwraca `null` i <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> właściwości atrybutu pozostanie ustawiony na wartość domyślną `false`. Jest to najbardziej typowe użycie `IXmlSerializable` typów.  
  
-   Typy elementów są używane podczas `IXmlSerializable` typu musi kontrolować własną nazwę elementu głównego. Aby oznaczyć typu jako typu elementu, ustawić <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> właściwość <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atrybutu `true` lub zwróć `null` przez metodę dostawcy schematu. Posiadanie metody dostawcy schematu jest opcjonalny w przypadku typów elementów — można określić `null` zamiast nazwy metody w `XmlSchemaProviderAttribute`. Jednak jeśli `IsAny` jest `true` i metody dostawcy schematu jest określony, metoda musi zwracać `null`.  
  
-   Starsza wersja <xref:System.Data.DataSet> typy są `IXmlSerializable` typy, które nie są oznaczone ikoną z `XmlSchemaProviderAttribute` atrybutu. Zamiast tego opierają się na <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> metodę generowania schematu. Ten wzorzec jest używana do `DataSet` typu i jego typizowanego obiektu dataset pochodzi z klasy w starszych wersjach programu .NET Framework, ale teraz jest przestarzały i nie jest obsługiwana tylko w przypadku starszych powodów. Nie zależą od tego wzorca i zawsze stosuj `XmlSchemaProviderAttribute` do Twojej `IXmlSerializable` typów.  
  
### <a name="ixmlserializable-content-types"></a>Typy zawartości interfejsu IXmlSerializable  
 Podczas serializowania element członkowski danych klasy typu, który implementuje `IXmlSerializable` jest typem zawartości zgodnie z definicją wcześniej serializator zapisuje element otoki dla elementu członkowskiego danych i przekazuje do kontrolować <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> metody. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Implementacja może zapisywać żadnych XML, który obejmuje dodawanie atrybutów do elementu otoki. Po `WriteXml` jest gotowe, serializator zamyka element.  
  
 Podczas deserializacji element członkowski danych klasy typu, który implementuje `IXmlSerializable` i jest typu zawartości, zgodnie z definicją wcześniej, Deserializator umieszcza modułu odczytującego XML na element otoki dla elementu członkowskiego danych i przekazuje kontrolę do <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> metody. Metoda musi odczytu cały element, w tym tagiem początkowym i końcowym. Upewnij się, że Twoje `ReadXml` kod obsługi w przypadku, gdy element jest pusty. Ponadto sieci `ReadXml` wdrożenia nie należy traktować element otoki jest o nazwie określony sposób. Nazwa jest wybierany przez serializator może się różnić.  
  
 Dozwolone jest przypisanie `IXmlSerializable` typy zawartości polymorphically, na przykład do danych elementów członkowskich typu <xref:System.Object>. Dopuszczalne jest również wystąpień typu mieć wartości null. Na koniec jest możliwość użycia `IXmlSerializable` typy z zachowywania wykres obiektu włączone i <xref:System.Runtime.Serialization.NetDataContractSerializer>. Tych funkcji wymaga [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serializator dołączyć niektóre atrybuty w element otoki ("zero" i "type" w przestrzeni nazw XML schematu wystąpienia i "Id", "Ref", "Type" i "Zestawu" w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-określonych przestrzeni nazw).  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>Atrybuty, aby zignorować podczas implementowania ReadXml  
 Przed przekazaniem kontroli do Twojej `ReadXml` kodu, Deserializator sprawdza, czy XML element, wykrywa te specjalne atrybuty XML i działa na nich. Na przykład, jeśli jest "zero" `true`, deserializowany jest wartość null i `ReadXml` nie jest wywoływany. W przypadku wykrycia polimorfizm zawartość elementu są rozszeregować tak, jakby była innego typu. Implementacja typu polymorphically przypisane `ReadXml` jest wywoływana. W każdym przypadku `ReadXml` implementacji ignorować te atrybuty specjalne, ponieważ są one obsługiwane przez deserializacji.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>Zagadnienia dotyczące schematu dla typów IXmlSerializable zawartości  
 Podczas eksportowania schematu i `IXmlSerializable` typu zawartości, wywoływana jest metoda dostawcy schematu. <xref:System.Xml.Schema.XmlSchemaSet> Jest przekazywany do metody dostawcy schematu. Metoda można dodać żadnych prawidłowego schematu do zestawu schematów. Zestaw schematu zawiera schemat, który został już określony w momencie, gdy wystąpi eksportowania schematu. Gdy metoda dostawcy schematu należy dodać element do zestawu schematów, należy określić czy <xref:System.Xml.Schema.XmlSchema> z odpowiedni obszar nazw już istnieje w zestawie. Jeśli tak, metody dostawcy schematu należy dodać nowy element do istniejącej `XmlSchema`. W przeciwnym razie należy utworzyć nowy `XmlSchema` wystąpienia. Jest to ważne, jeśli tablice `IXmlSerializable` typy są używane. Na przykład, jeśli masz `IXmlSerializable` typu, który pobiera wyeksportowany jako typu "A" w przestrzeni nazw "B", możliwe, że do czasu wywołania metody dostawcy schematu schematu już ustawione zawiera schemat "B" typu "ArrayOfA".  
  
 Oprócz dodania typów do <xref:System.Xml.Schema.XmlSchemaSet>, metody dostawcy schematu dla typów zawartości musi zwracać wartość inną niż null. Może on zwrócić <xref:System.Xml.XmlQualifiedName> , który określa nazwę typu schematu dla podanego `IXmlSerializable` typu. Ta nazwa kwalifikowana służy również jako dane umowy, nazwę i przestrzeń nazw dla typu. Dozwolone jest zwracany typ, który nie istnieje w zestawie natychmiast, gdy metoda dostawcy schematu zwraca schematów. Jednak oczekuje się, że w czasie wszystkie powiązane typy są eksportowane ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> metoda jest wywoływana dla wszystkich odpowiednich typów na <xref:System.Runtime.Serialization.XsdDataContractExporter> i <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> dostępu do właściwości), typ istnieje w zestawie schematów. Uzyskiwanie dostępu do `Schemas` właściwości przed wszystkimi odpowiednimi `Export` wprowadzono wywołania może spowodować <xref:System.Xml.Schema.XmlSchemaException>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]w ramach procesu eksportu zobacz [eksportowanie schematów z klas](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
 Metoda dostawcy schematu może także zwracać <xref:System.Xml.Schema.XmlSchemaType> do użycia. Tego typu może lub nie może być anonimowy. Jeśli jest anonimowy, schemat `IXmlSerializable` typu jest eksportowane jako typu anonimowego zawsze `IXmlSerializable` typ jest używany jako element członkowski danych. `IXmlSerializable` Typ ma nadal nazwie kontraktu danych i przestrzeni nazw. (Jest to określane zgodnie z opisem w [nazwy kontraktów danych](../../../../docs/framework/wcf/feature-details/data-contract-names.md) z tą różnicą, że <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu nie można dostosować nazwę.) Jeśli nie jest anonimowy, musi być jednego z typów w `XmlSchemaSet`. Ten przypadek jest odpowiednikiem zwracanie `XmlQualifiedName` typu.  
  
 Ponadto deklaracji element globalny są eksportowane dla typu. Jeśli typ nie ma <xref:System.Xml.Serialization.XmlRootAttribute> atrybut zastosowany do niego element ma taką samą nazwę i przestrzeń nazw jako kontraktu danych, a jest jego właściwość "nillable" `true`. Jedynym wyjątkiem jest przestrzeń nazw schematu ("http://www.w3.org/2001/XMLSchema") — Jeśli jest typu kontraktu danych w tej przestrzeni nazw, odpowiedni element globalny jest w przestrzeni nazw puste, ponieważ jest zabroniony Dodawanie nowych elementów do schematu przestrzeń nazw. Jeśli typ ma `XmlRootAttribute` atrybut zastosowany do jego deklaracji element globalny został wyeksportowany z następującym: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>, <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> i <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> właściwości. Wartości domyślne z `XmlRootAttribute` stosowane są nazwie kontraktu danych, pustą przestrzeń nazw i Trwa "nillable" `true`.  
  
 Te same zasady deklaracji element globalny dotyczą typów starszej wersji zestawu danych. Należy pamiętać, że `XmlRootAttribute` nie może zastąpić element globalny deklaracje dodane za pomocą kodu niestandardowego, albo dodać do `XmlSchemaSet` przy użyciu metody dostawcy schematu lub za pomocą `GetSchema` dla typów starszej wersji zestawu danych.  
  
### <a name="ixmlserializable-element-types"></a>Typy elementów interfejsu IXmlSerializable  
 `IXmlSerializable`Element typów ma albo `IsAny` ustawioną właściwość `true` lub ma ich zwracać metoda dostawcy schematu `null`.  
  
 Serializację i deserializację typu elementu jest bardzo podobny do serializację i deserializację typu zawartości. Istnieje jednak kilka istotnych różnic:  
  
-   `WriteXml` Implementacji powinien zapisać dokładnie jeden element (który oczywiście może zawierać wielu elementów podrzędnych). Nie powinna być zapisaniem atrybutów poza tym pojedynczy element wielu elementów równorzędnych lub zawartości mieszanej. Element może być pusty.  
  
-   `ReadXml` Implementacji element otoki nie powinny do odczytu. Oczekuje się, aby przeczytać jeden element który `WriteXml` tworzy.  
  
-   Podczas serializowania typu elementu regularnie (na przykład jako element członkowski danych kontraktu danych), serializator danych wyjściowych element otoki przed wywołaniem `WriteXml`, podobnie jak w przypadku typów zawartości. Jednak podczas serializacji typu elementu najwyższego poziomu, Serializator nie zwykle wyprowadza element otoki cały wokół elementu który `WriteXml` zapisuje, chyba że nazwa głównego i przestrzeni nazw zostały jawnie określone podczas tworzenia serializator w `DataContractSerializer` lub `NetDataContractSerializer` konstruktorów. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Serializacji i deserializacji](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
-   Podczas serializowania typu elementu na najwyższym poziomie bez określania nazwy głównego i przestrzeni nazw podczas konstruowania <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> i <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> zasadniczo nic nie rób i <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> wywołania `WriteXml`. W tym trybie nie może być obiektu poddawanego serializacji `null` i nie można przypisać polymorphically. Ponadto zachowywania wykres obiektu nie może być włączone i `NetDataContractSerializer` nie można użyć.  
  
-   Podczas deserializacji typu elementu na najwyższym poziomie bez określania nazwy głównego i przestrzeni nazw podczas konstruowania <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> zwraca `true` Jeśli można znaleźć uruchomienia dowolnego elementu. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A>z `verifyObjectName` ustawiona `true` działa w taki sam sposób jak `IsStartObject` przed faktycznie czytania obiektu. `ReadObject`następnie przekazuje formantu `ReadXml` metody.  
  
 Schemat wyeksportowane dla typów elementów jest taka sama, jak w przypadku `XmlElement` wpisz zgodnie z opisem w sekcji wcześniej, z wyjątkiem tego, że metoda dostawcy schematu można dodać dodatkowe schematu w celu <xref:System.Xml.Schema.XmlSchemaSet> jako z typami zawartości. Przy użyciu `XmlRootAttribute` atrybutu z typem elementu jest niedozwolone, a element globalny deklaracje nigdy nie są emitowane w przypadku tych typów.  
  
### <a name="differences-from-the-xmlserializer"></a>Różnice z elementu XmlSerializer  
 `IXmlSerializable` Interfejsu i `XmlSchemaProviderAttribute` i `XmlRootAttribute` atrybuty są również zrozumiałe <xref:System.Xml.Serialization.XmlSerializer> . Istnieją pewne różnice w jaki sposób są one traktowane w modelu kontraktu danych. Istotne różnice przedstawiono na poniższej liście:  
  
-   Metoda dostawcy schematu muszą być publiczne do użycia w `XmlSerializer`, ale nie muszą być publiczne do użycia w modelu kontraktu danych.  
  
-   Metoda dostawcy schematu jest wywoływane, gdy `IsAny` jest `true` w modelu kontraktu danych, lecz nie `XmlSerializer`.  
  
-   Gdy `XmlRootAttribute` atrybut nie ma zawartości lub starszej wersji zestawu danych typów, `XmlSerializer` eksportuje deklaracji element globalny w przestrzeni nazw puste. W modelu danych kontraktu przestrzeni nazw używany jest zwykle przestrzeń nazw kontraktu danych, zgodnie z wcześniejszym opisem.  
  
 Należy pamiętać o tych różnic podczas tworzenia typów, które są używane w obu tych technologii serializacji.  
  
### <a name="importing-ixmlserializable-schema"></a>Importowanie schematu interfejsu IXmlSerializable  
 Podczas importowania schematu wygenerowanego z `IXmlSerializable` typów, istnieje kilka możliwości:  
  
-   Wygenerowany schematu może być schematu kontraktu danych, zgodnie z opisem w [odwołanie do schematu kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). W takim przypadku schemat, które mogą być importowane w zwykły sposób i typy kontraktu danych regularne są generowane.  
  
-   Wygenerowany schematu nie może być schematu kontraktu prawidłowe dane. Na przykład schemat metodę dostawca może generować schematu, która obejmuje atrybutów XML, które nie są obsługiwane w modelu kontraktu danych. W takim przypadku można zaimportować schematu jako `IXmlSerializable` typów. Ten tryb importu nie znajduje się na domyślnie, ale można łatwo włączyć — na przykład z `/importXmlTypes` przełącznik wiersza polecenia do [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). To jest szczegółowo opisane w [Importowanie schematu do generowania klasy](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md). Należy pamiętać, że należy skontaktować się bezpośrednio z pliku XML dla swoich wystąpień typu. Można także rozważyć przy użyciu innego serializacji technologia, która obsługuje szerszego zakresu schematu — zobacz temat przy użyciu `XmlSerializer`.  
  
-   Może zajść potrzeba ponownego użycia istniejącą `IXmlSerializable` typy serwera proxy zamiast generowania nowych. W takim przypadku funkcja wskazanych typów opisana w schemacie importowania do generowania typów tematu można wskazać typ do ponownego użycia. Odpowiada to przy użyciu `/reference` Włącz svcutil.exe, który określa zestaw, który zawiera typy do ponownego użycia.  
  
### <a name="xmlserializer-legacy-behavior"></a>Zachowanie starszych XmlSerializer  
 W .NET Framework 4.0 i starszych XmlSerializer generowane zestawy tymczasowe serializacji pisanie kodu C# do pliku. Plik następnie został skompilowany w zestawie.  To zachowanie było niektórych niepożądane skutki takich jak spowalniając czas uruchamiania dla serializatora. W programie .NET Framework 4.5 to zachowanie została zmieniona na generowanie zestawów bez konieczności użycia kompilatora. Niektórzy deweloperzy mogą chcieć Zobacz wygenerowanego kodu C#. Można określić, to zachowanie starszej wersji za pomocą następującej konfiguracji:  
  
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
  
 Jeśli wystąpiły problemy ze zgodnością, takich jak `XmlSerializer` nie może serializować klasy pochodnej z nowe zastąpienie niepubliczne, można przełączyć do `XMLSerializer` starsze zachowanie przy użyciu następującej konfiguracji:  
  
```xml  
<configuration>  
<appSettings>   
<add key="System:Xml:Serialization:UseLegacySerializerGeneration" value="true" />  
               </appSettings>  
</configuration>  
```  
  
 Jako alternatywę do powyższej konfiguracji można użyć następującej konfiguracji na maszynie z systemem .NET Framework 4.5 lub nowszej wersji:  
  
```xml  
<configuration>  
<system.xml.serialization>  
<xmlSerializer useLegacySerializerGeneration="true"/>  
</system.xml.serialization>  
</configuration>  
```  
  
> [!NOTE]
>  `<xmlSerializer useLegacySerializerGeneration="true"/>` Przełącznika działa tylko na maszynie z systemem .NET Framework 4.5 lub nowszej wersji. Powyższe `appSettings` podejście działa we wszystkich wersjach systemu .NET Framework.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.DataContractFormatAttribute>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute>  
 [Określanie transferu danych w kontraktach usług](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 [Używanie kontraktów danych](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Porady: poprawy uruchamiania czasu programu WCF aplikacje klienckie przy użyciu elementu XmlSerializer](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)

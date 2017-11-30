---
title: Edytowanie schematy XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b9505f60b2000ef227463404dab051ecb7fa3cc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="editing-xml-schemas"></a>Edytowanie schematy XML
Edytowanie schematu XML jest jednym z najważniejszych elementów z modelu obiektu schematu (SOM). Wszystkie właściwości wstępnie przygotowany schema kompilacji SOM można zmienić istniejące wartości w schemacie XML. Schemat XML można następnie ponownie skompilowana, aby odzwierciedlić zmiany.  
  
 Pierwszym krokiem w schemacie ładowane do SOM edycji jest przechodzenia schematu. Należy zapoznać się z przechodzących przez schemat przy użyciu interfejsu API SOM, przed przystąpieniem do edytowania schematu. Należy także zapoznać się z właściwości przed i po schema kompilacji po-schema-kompilacji-typu Infoset (PSCI).  
  
## <a name="editing-an-xml-schema"></a>Edytowanie schematu XML  
 W tej sekcji podano dwa przykłady kodu, które Edytowanie schematu klienta utworzone w [schematów XML budynku](../../../../docs/standard/data/xml/building-xml-schemas.md) tematu. W pierwszym przykładzie kodu dodaje nowy `PhoneNumber` elementu `Customer` dodaje nowy element, a w drugim przykładzie kodu `Title` atrybutu `FirstName` elementu. Pierwszym przykładzie użyto również po-schema-kompilacji <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekcji jako środek przechodzących przez schemat klienta podczas drugi przykład kodu wykorzystuje wstępnie przygotowany-schema-kompilacji <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekcji.  
  
### <a name="phonenumber-element-example"></a>Przykład elementu numer telefonu  
 W tym przykładzie pierwsze kodu dodaje nowy `PhoneNumber` elementu `Customer` elementu schematu klienta. Przykładowy kod edytuje schematu klienta w kolejnych krokach.  
  
1.  Dodaje do nowego schematu klienta <xref:System.Xml.Schema.XmlSchemaSet> obiekt, a następnie kompiluje go. Wszelkie ostrzeżenia dotyczące sprawdzania poprawności schematu i błędów napotkanych odczytu lub kompilowania schematu są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler> delegowanie.  
  
2.  Pobiera skompilowanych <xref:System.Xml.Schema.XmlSchema> obiekt z <xref:System.Xml.Schema.XmlSchemaSet> przez Iterowanie po <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości. Ponieważ skompilować schematu, po-Schema-kompilacji-typu Infoset właściwości (PSCI) są dostępne.  
  
3.  Tworzy `PhoneNumber` przy użyciu elementu <xref:System.Xml.Schema.XmlSchemaElement> klasy `xs:string` za pomocą ograniczenia typu prostego <xref:System.Xml.Schema.XmlSchemaSimpleType> i <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> klas, dodaje zestaw reguł wzorca do <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> właściwości ograniczenia i dodaje ograniczenia <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> właściwość typu prostego i typu prostego do <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> z `PhoneNumber` elementu.  
  
4.  Wykonuje iterację na każdym <xref:System.Xml.Schema.XmlSchemaElement> w <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekcji po-schema-kompilacji <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekcji.  
  
5.  Jeśli <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> elementu jest `"Customer"`, pobiera typ złożony `Customer` przy użyciu elementu <xref:System.Xml.Schema.XmlSchemaComplexType> klasy i cząstka sequence użycia typu złożonego <xref:System.Xml.Schema.XmlSchemaSequence> klasy.  
  
6.  Dodaje nowy `PhoneNumber` element zawierający istniejącej sekwencji `FirstName` i `LastName` elementów za pomocą wstępnie przygotowany-schema-kompilacji <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> kolekcji sekwencji.  
  
7.  Na koniec ponownego przetwarzania i kompiluje zmodyfikowanych <xref:System.Xml.Schema.XmlSchema> przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> i <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> klasy i zapisuje go w konsoli.  
  
 Poniżej znajduje się pełny przykład kodu.  
  
 [!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
 [!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
 [!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]  
  
 Poniżej przedstawiono schematu klienta zmodyfikowane utworzone w [schematów XML budynku](../../../../docs/standard/data/xml/building-xml-schemas.md) tematu.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="xs:string" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
        <xs:element name="PhoneNumber">           <xs:simpleType>             <xs:restriction base="xs:string">               <xs:pattern value="\d{3}-\d{3}-\d(4)" />             </xs:restriction>           </xs:simpleType>         </xs:element>  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /  
>  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
### <a name="title-attribute-example"></a>Przykład atrybutu tytułu  
 W tym drugim przykładzie kodu dodaje nowy `Title` atrybutu `FirstName` elementu schematu klienta. W pierwszym przykładzie kodu typu `FirstName` jest element `xs:string`. Aby uzyskać `FirstName` element ma atrybut wraz z ciągu zawartości, należy zmienić jego typ do typu złożone o prostym rozszerzeniu zawartości modelu zawartości.  
  
 Przykładowy kod edytuje schematu klienta w kolejnych krokach.  
  
1.  Dodaje do nowego schematu klienta <xref:System.Xml.Schema.XmlSchemaSet> obiekt, a następnie kompiluje go. Wszelkie ostrzeżenia dotyczące sprawdzania poprawności schematu i błędów napotkanych odczytu lub kompilowania schematu są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler> delegowanie.  
  
2.  Pobiera skompilowanych <xref:System.Xml.Schema.XmlSchema> obiekt z <xref:System.Xml.Schema.XmlSchemaSet> przez Iterowanie po <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości. Ponieważ skompilować schematu, po-Schema-kompilacji-typu Infoset właściwości (PSCI) są dostępne.  
  
3.  Tworzy nowy typ złożony dla `FirstName` przy użyciu elementu <xref:System.Xml.Schema.XmlSchemaComplexType> klasy.  
  
4.  Tworzy nowy prostym rozszerzeniu zawartości, z podstawowym typem `xs:string`za pomocą <xref:System.Xml.Schema.XmlSchemaSimpleContent> i <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> klasy.  
  
5.  Tworzy nowy `Title` atrybutu przy użyciu <xref:System.Xml.Schema.XmlSchemaAttribute> klasy, z <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> z `xs:string` i dodaje atrybut do prostym rozszerzeniu zawartości.  
  
6.  Ustawia model zawartości prostej zawartości prostym rozszerzeniu zawartości i model zawartości typu złożonego do prostej zawartości.  
  
7.  Dodaje nowy typ złożony do wstępnie przygotowany-schema-kompilacji <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekcji.  
  
8.  Wykonuje iterację na każdym <xref:System.Xml.Schema.XmlSchemaObject> w próbnej-schema-kompilacji <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekcji.  
  
> [!NOTE]
>  Ponieważ `FirstName` element nie jest element globalny w schemacie, nie jest dostępna w <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> lub <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekcji. Przykładowy kod lokalizuje `FirstName` element dzięki umieszczeniu pierwszy `Customer` elementu.  
>   
>  W pierwszym przykładzie kodu przechodzić schematu za pomocą po-schema-kompilacji <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekcji. W tym przykładzie, wstępnie przygotowany-schema-kompilacji <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekcja jest używana do przechodzenia schematu. Gdy obie kolekcje zapewniają dostęp do globalnego elementy w schemacie, iteracji <xref:System.Xml.Schema.XmlSchema.Items%2A> kolekcji jest bardziej czasochłonne, ponieważ musi przejść przez wszystkie elementy globalny w schemacie i nie ma żadnych właściwości PSCI. Kolekcje PSCI (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>i tak dalej) zapewniać bezpośredni dostęp do ich globalne elementy, atrybuty i typy oraz ich właściwości PSCI.  
  
1.  Jeśli <xref:System.Xml.Schema.XmlSchemaObject> to element, którego <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> jest `"Customer"`, pobiera typ złożony `Customer` przy użyciu elementu <xref:System.Xml.Schema.XmlSchemaComplexType> klasy i cząstka sequence użycia typu złożonego <xref:System.Xml.Schema.XmlSchemaSequence> klasy.  
  
2.  Wykonuje iterację na każdym <xref:System.Xml.Schema.XmlSchemaParticle> w próbnej-schema-kompilacji <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> kolekcji.  
  
3.  Jeśli <xref:System.Xml.Schema.XmlSchemaParticle> jest elementem, który w <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> jest `"FirstName"`, ustawia <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> z `FirstName` element do nowego `FirstName` typu złożonego.  
  
4.  Na koniec ponownego przetwarzania i kompiluje zmodyfikowanych <xref:System.Xml.Schema.XmlSchema> przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> i <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> klasy i zapisuje go w konsoli.  
  
 Poniżej znajduje się pełny przykład kodu.  
  
 [!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
 [!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
 [!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]  
  
 Poniżej przedstawiono schematu klienta zmodyfikowane utworzone w [schematów XML budynku](../../../../docs/standard/data/xml/building-xml-schemas.md) tematu.  
  
```xml  
<?xml version="1.0" encoding=" utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /  
>  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:complexType name="FirstNameComplexType">     <xs:simpleContent>       <xs:extension base="xs:string">         <xs:attribute name="Title" type="xs:string" />       </xs:extension>     </xs:simpleContent>   </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie modelu obiektu schematu XML](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [Odczytywanie i zapisywanie schematy XML](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [Tworzenie schematów XML](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [Przechodzenie przez schematy XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [W tym lub importowanie schematy XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [Zestaw XmlSchemaSet schematu kompilacji](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Obiekt typu Infoset schematu po kompilacji](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)

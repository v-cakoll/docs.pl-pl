---
title: Tworzenie schematów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ed02680831302880e2bfc02b21ea61303b92a3c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="building-xml-schemas"></a>Tworzenie schematów XML
Klasy w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeń nazw mapowania do struktury zdefiniowane w sieci World Wide Web konsorcjum W3C zalecenie schematu XML i może służyć do tworzenia XML schematów w pamięci.  
  
## <a name="building-an-xml-schema"></a>Tworzenie schematu XML  
 W kolejnych przykłady kodu interfejsu API SOM jest używany do tworzenia klienta XML schematu w pamięci.  
  
### <a name="creating-element-and-attributes"></a>Tworzenie elementów i atrybutów  
 Przykłady kodu kompilacji klienta schematu od dołu do góry, tworzenie podrzędne elementy, atrybuty i jako odpowiednie typy najpierw, a następnie elementów najwyższego poziomu.  
  
 W poniższym przykładzie kodu `FirstName` i `LastName` elementów, jak również `CustomerId` atrybut schematu klienta są tworzone przy użyciu <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaAttribute> klasy SOM. Z wyjątkiem <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> właściwości <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaAttribute> klasy, które odnoszą się do atrybutu "name" `<xs:element />` i `<xs:attribute />` elementy w schemacie XML z wszystkimi innymi atrybutami dozwolona przez schemat (`defaultValue`, `fixedValue`, `form`i tak dalej) ma w odpowiednich właściwościach <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaAttribute> klasy.  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a>Tworzenie typów schematów  
 Zawartość elementów i atrybutów zdefiniowano według ich typów. Tworzenie elementów i atrybutów, których typy są jednego z typów wbudowanego schematu <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> właściwość <xref:System.Xml.Schema.XmlSchemaElement> lub <xref:System.Xml.Schema.XmlSchemaAttribute> klas są konfigurowane przy użyciu odpowiedniego nazwa kwalifikowana za pomocą typu wbudowanego <xref:System.Xml.XmlQualifiedName> klasy. Aby utworzyć typ zdefiniowany przez użytkownika dla elementów i atrybutów, nowy typ prostymi lub złożonymi jest tworzony przy użyciu <xref:System.Xml.Schema.XmlSchemaSimpleType> lub <xref:System.Xml.Schema.XmlSchemaComplexType> klasy.  
  
> [!NOTE]
>  Do tworzenia bez nazwy prostej lub złożonych typów, które są anonimowe elementami podrzędnymi elementu lub atrybutu (dotyczy tylko proste typy dla atrybutów), ustaw <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> właściwość <xref:System.Xml.Schema.XmlSchemaElement> lub <xref:System.Xml.Schema.XmlSchemaAttribute> klasy bez nazwy typu prostego lub złożonych, zamiast <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> właściwość <xref:System.Xml.Schema.XmlSchemaElement> lub <xref:System.Xml.Schema.XmlSchemaAttribute> klasy.  
  
 Schematy XML zezwolić na oba anonimowego i nazwane proste typy dziedziczyć przez ograniczenia z innych typów prostych (wbudowanych i zdefiniowanych przez użytkownika) lub wykonywane w formie listy lub union innych typów prostych. <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> Klasy jest używany do tworzenia typu prostego ograniczając wbudowane `xs:string` typu. Można również użyć <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> lub <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> klasy do tworzenia listy lub union. <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> Właściwość wskazuje, czy jest on ograniczenie typu prostego, lista lub union.  
  
 W poniższym przykładzie kodu `FirstName` elementu typem jest typ wbudowany `xs:string`, `LastName` typ elementu jest typem prostym nazwanego jest ograniczeniem typu wbudowanego `xs:string`, z `MaxLength` wartość aspektu 20, i `CustomerId` typ atrybutu jest typu wbudowanego `xs:positiveInteger`. `Customer` Element jest złożone typu anonimowego, w których jest sekwencja z `FirstName` i `LastName` elementów i atrybutów, których zawiera `CustomerId` atrybutu.  
  
> [!NOTE]
>  Można również użyć <xref:System.Xml.Schema.XmlSchemaChoice> lub <xref:System.Xml.Schema.XmlSchemaAll> klas jako cząstek typu złożonego do replikowania `<xs:choice />` lub `<xs:all />` semantyki.  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a>Tworzenie i kompilowania schematów  
 Ten punkt, elementy podrzędne i atrybuty, jako odpowiednie typy i najwyższego poziomu `Customer` element zostały utworzone przy użyciu interfejsu API SOM w pamięci. W poniższym przykładzie kodu element schematu jest tworzony przy użyciu <xref:System.Xml.Schema.XmlSchema> klas, elementów najwyższego poziomu i typy są dodawane do go za pomocą <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> właściwości i pełne schematu została skompilowana przy użyciu <xref:System.Xml.Schema.XmlSchemaSet> klasy i zapisywania ich w w konsoli.  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> Metoda sprawdza poprawność schematu klienta względem reguły dla schematu XML i udostępnia właściwości po schema kompilacji.  
  
> [!NOTE]
>  Wszystkie właściwości po schema kompilacji w interfejsie API SOM różnią się od po-schema-weryfikacji-obiekt typu Infoset.  
  
 <xref:System.Xml.Schema.ValidationEventHandler> Dodane do <xref:System.Xml.Schema.XmlSchemaSet> jest delegata, który wywołuje metodę wywołania zwrotnego `ValidationCallback` do obsługi schemat sprawdzania poprawności ostrzeżeń i błędów.  
  
 Poniżej znajduje się pełny przykład kodu i schematu klienta wyświetlony w konsoli.  
  
 [!code-cpp[XmlSchemaCreateExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#1)]
 [!code-csharp[XmlSchemaCreateExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#1)]
 [!code-vb[XmlSchemaCreateExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#1)]  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name="Customer">  
      <xs:complexType>  
         <xs:sequence>  
            <xs:element name="FirstName" type="xs:string" />  
            <xs:element name="LastName" type="tns:LastNameType" />  
         </xs:sequence>  
         <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" />  
      </xs:complexType>  
   </xs:element>  
   <xs:simpleType name="LastNameType">  
      <xs:restriction base="xs:string">  
         <xs:maxLength value="20" />  
      </xs:restriction>  
   </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Model SOM (XML Schema Object Model) ― omówienie](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [Odczytywanie i zapisywanie schematów XML](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [Przechodzenie schematów XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [Edytowanie schematów XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 [Uwzględnianie lub importowanie schematów XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Zestaw informacji po kompilacji schematu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)

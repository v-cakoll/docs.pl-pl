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
ms.openlocfilehash: 10b2471d13d410826cec3404725117649442297b
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842622"
---
# <a name="building-xml-schemas"></a>Tworzenie schematów XML
Klasy w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw mapowania do struktur, zdefiniowane w zaleceniem schematu XML World Wide Web Consortium (W3C) i może służyć do tworzenia XML schematów w pamięci.  
  
## <a name="building-an-xml-schema"></a>Tworzenie schematu XML  
 W przykładach kodu, które należy wykonać interfejs API SOM jest używany do tworzenia klienta XML schematu w pamięci.  
  
### <a name="creating-element-and-attributes"></a>Tworzenie elementów i atrybutów  
 Przykłady kodu kompilacji klienta schematu od dołu do góry, tworzenie podrzędnych elementów, atrybutów i ich odpowiednie typy najpierw, a następnie elementów najwyższego poziomu.  
  
 W poniższym przykładzie kodu `FirstName` i `LastName` elementów, jak również `CustomerId` atrybut schematu klienta są tworzone przy użyciu <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaAttribute> klasy SOM. Z wyjątkiem <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> właściwości <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaAttribute> klas, które odnoszą się do atrybutu "name" `<xs:element />` i `<xs:attribute />` elementów schematu XML, a wszystkie inne atrybuty dozwolona przez schemat (`defaultValue`, `fixedValue`, `form`i tak dalej) mają odpowiednie właściwości w <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaAttribute> klasy.  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a>Tworzenie typów schematu  
 Zawartość elementów i atrybutów jest definiowany przez ich typy. Do tworzenia elementów i atrybutów, których typy są jednym z typów wbudowanych schematu <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> właściwość <xref:System.Xml.Schema.XmlSchemaElement> lub <xref:System.Xml.Schema.XmlSchemaAttribute> klasy są konfigurowane przy użyciu odpowiedniego kwalifikowana nazwa typu wbudowanego przy użyciu <xref:System.Xml.XmlQualifiedName> klasy. Aby utworzyć typ zdefiniowany przez użytkownika, dla elementów i atrybutów, nowy typ proste lub złożone jest tworzony przy użyciu <xref:System.Xml.Schema.XmlSchemaSimpleType> lub <xref:System.Xml.Schema.XmlSchemaComplexType> klasy.  
  
> [!NOTE]
>  Do tworzenia nienazwane prostych lub złożonych typów, które są anonimowe elementy podrzędne elementu lub atrybutu (dotyczy tylko proste typy dla atrybutów), ustaw <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> właściwość <xref:System.Xml.Schema.XmlSchemaElement> lub <xref:System.Xml.Schema.XmlSchemaAttribute> klasy bez nazwy typów prostych lub złożonych, zamiast <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> właściwość <xref:System.Xml.Schema.XmlSchemaElement> lub <xref:System.Xml.Schema.XmlSchemaAttribute> klasy.  
  
 Schematów XML Zezwalaj na obu anonimowych i nazwanych proste typy pochodzić przez ograniczenia z innych typów prostych (wbudowane lub zdefiniowanych przez użytkownika) lub skonstruowany jako listy lub Unii innych typów prostych. <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> Klasa jest używana do tworzenia prostego typu przez ograniczenie możliwości wykonywania wbudowanej `xs:string` typu. Można również użyć <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> lub <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> klasy, aby utworzyć typy listy lub Unii. <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> Właściwość wskazuje, czy jest ograniczenie prostego typu, listy lub Unii.  
  
 W poniższym przykładzie kodu `FirstName` typ elementu to typ wbudowany `xs:string`, `LastName` typ elementu jest nazwane prosty typ, który jest ograniczeniem typu wbudowanego `xs:string`, za pomocą `MaxLength` wartość aspektu 20, a `CustomerId` typ atrybutu jest typu wbudowanego `xs:positiveInteger`. `Customer` Element jest anonimowy typ złożony, w których cząstką jest sekwencja z `FirstName` i `LastName` elementy i atrybuty, których zawiera `CustomerId` atrybutu.  
  
> [!NOTE]
>  Można również użyć <xref:System.Xml.Schema.XmlSchemaChoice> lub <xref:System.Xml.Schema.XmlSchemaAll> klasy jako cząstek typu złożonego do replikowania `<xs:choice />` lub `<xs:all />` semantyki.  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a>Tworzenie i kompilowania schematów  
 W tym punkcie, elementy podrzędne i atrybuty, jako odpowiednie typy i najwyższego poziomu `Customer` element zostały utworzone przy użyciu interfejsu API SOM w pamięci. W poniższym przykładzie kodu elementu schematu jest tworzony przy użyciu <xref:System.Xml.Schema.XmlSchema> klasy, elementów najwyższego poziomu i typy są dodawane do niego przy użyciu <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> właściwości i pełne schematu jest skompilowana przy użyciu <xref:System.Xml.Schema.XmlSchemaSet> klasy i zapisywane w Konsola.  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> Metoda sprawdza poprawność schematu klienta względem reguły dla schematu XML i udostępnia właściwości po schema kompilacji.  
  
> [!NOTE]
>  Wszystkie właściwości po schema kompilacji w interfejsie API SOM różnią się od odniesienie-schema-weryfikacji — zestaw informacji.  
  
 <xref:System.Xml.Schema.ValidationEventHandler> Dodane do <xref:System.Xml.Schema.XmlSchemaSet> jest delegat, który wywołuje metodę wywołania zwrotnego `ValidationCallback` do obsługi schematu Walidacja ostrzeżeń i błędów.  
  
 Oto pełny przykład kodu i schematu klientów wyświetlony w konsoli.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Model SOM (XML Schema Object Model) ― omówienie](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
- [Odczytywanie i zapisywanie schematów XML](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
- [Przechodzenie schematów XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
- [Edytowanie schematów XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
- [Uwzględnianie lub importowanie schematów XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
- [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
- [Zestaw informacji po kompilacji schematu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)

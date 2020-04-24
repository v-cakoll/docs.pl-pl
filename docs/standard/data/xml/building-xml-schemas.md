---
title: Tworzenie schematów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 8a5ea56c-0140-4b51-8997-875ae6a8e0cb
ms.openlocfilehash: c921331b00fe137d4ad52d62951e8c161768dfae
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711145"
---
# <a name="building-xml-schemas"></a>Tworzenie schematów XML
Klasy w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw są mapowane na struktury zdefiniowane w organizacja World Wide Web Consortium (W3C) zalecenia schematu XML i mogą być używane do kompilowania schematów XML w pamięci.  
  
## <a name="building-an-xml-schema"></a>Kompilowanie schematu XML  
 W poniższym przykładzie kodu model API SOM jest używany do kompilowania schematu XML klienta w pamięci.  
  
### <a name="creating-element-and-attributes"></a>Tworzenie elementu i atrybutów  
 Przykłady kodu kompilują schemat klienta od dołu, tworzą elementy podrzędne, atrybuty i odpowiadające im typy najpierw, a następnie elementy najwyższego poziomu.  
  
 W poniższym przykładzie kodu `FirstName` elementy i, a `LastName` także `CustomerId` atrybut schematu klienta są tworzone przy użyciu klas <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaAttribute> modelu Som. <xref:System.Xml.Schema.XmlSchemaElement.Name%2A> Oprócz <xref:System.Xml.Schema.XmlSchemaElement> właściwości i <xref:System.Xml.Schema.XmlSchemaAttribute> klasy, które odpowiadają atrybutowi "name" elementów `<xs:element />` i `<xs:attribute />` w schemacie XML, wszystkie inne atrybuty dozwolone przez schemat (`defaultValue`, `fixedValue`, `form`, i tak dalej) mają odpowiednie właściwości w klasach <xref:System.Xml.Schema.XmlSchemaElement> i. <xref:System.Xml.Schema.XmlSchemaAttribute>  
  
 [!code-cpp[XmlSchemaCreateExample#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#2)]
 [!code-csharp[XmlSchemaCreateExample#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#2)]
 [!code-vb[XmlSchemaCreateExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#2)]  
  
### <a name="creating-schema-types"></a>Tworzenie typów schematów  
 Zawartość elementów i atrybutów jest definiowana przez ich typy. Aby utworzyć elementy i atrybuty, których typy są jednym z wbudowanych typów schematu <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> , właściwość <xref:System.Xml.Schema.XmlSchemaElement> lub <xref:System.Xml.Schema.XmlSchemaAttribute> klasy są ustawiane za pomocą odpowiedniej kwalifikowanej nazwy typu wbudowanego przy użyciu <xref:System.Xml.XmlQualifiedName> klasy. Aby utworzyć typ zdefiniowany przez użytkownika dla elementów i atrybutów, nowy typ prosty lub złożony jest tworzony przy użyciu klasy <xref:System.Xml.Schema.XmlSchemaSimpleType> or. <xref:System.Xml.Schema.XmlSchemaComplexType>  
  
> [!NOTE]
> Aby utworzyć nienazwane proste lub złożone typy, które są anonimowymi elementami podrzędnymi elementu lub atrybutu (tylko proste typy są stosowane dla atrybutów) <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> , należy ustawić <xref:System.Xml.Schema.XmlSchemaElement> Właściwość <xref:System.Xml.Schema.XmlSchemaAttribute> lub klasy na typ prosty lub złożony, zamiast <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> właściwości <xref:System.Xml.Schema.XmlSchemaElement> lub <xref:System.Xml.Schema.XmlSchemaAttribute> klas.  
  
 Schematy XML zezwalają na wyprowadzanie anonimowych i nazwanych typów prostych przez ograniczenie z innych typów prostych (wbudowane lub zdefiniowane przez użytkownika) lub skonstruowane jako lista lub związek innych typów prostych. <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> Klasa jest używana do tworzenia typu prostego przez ograniczenie wbudowanego `xs:string` typu. Można również użyć klas <xref:System.Xml.Schema.XmlSchemaSimpleTypeList> lub <xref:System.Xml.Schema.XmlSchemaSimpleTypeUnion> do tworzenia typów list lub Unii. <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A?displayProperty=nameWithType> Właściwość określa, czy jest to proste ograniczenie typu, lista lub Unia.  
  
 W poniższym przykładzie `FirstName` kodu typ elementu jest typem wbudowanym `xs:string`, typ `LastName` elementu jest nazwanym typem prostym, który jest ograniczeniem typu `xs:string`wbudowanego, z wartością `MaxLength` aspektu 20, a typ `CustomerId` atrybutu jest typem `xs:positiveInteger`wbudowanym. `Customer` Element to anonimowy typ złożony, którego cząstka jest sekwencją elementów `FirstName` i `LastName` i których atrybuty zawiera `CustomerId` atrybut.  
  
> [!NOTE]
> Można również użyć <xref:System.Xml.Schema.XmlSchemaChoice> klas lub <xref:System.Xml.Schema.XmlSchemaAll> jako cząsteczek typu złożonego do replikowania `<xs:choice />` lub `<xs:all />` semantyki.  
  
 [!code-cpp[XmlSchemaCreateExample#3](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#3)]
 [!code-csharp[XmlSchemaCreateExample#3](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#3)]
 [!code-vb[XmlSchemaCreateExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#3)]  
  
### <a name="creating-and-compiling-schemas"></a>Tworzenie i kompilowanie schematów  
 W tym momencie elementy podrzędne i atrybuty, ich odpowiednie typy i element najwyższego poziomu `Customer` zostały utworzone w pamięci za pomocą interfejsu API modelu Som. W poniższym przykładzie kodu element schematu jest tworzony przy użyciu <xref:System.Xml.Schema.XmlSchema> klasy, elementy najwyższego poziomu i typy są dodawane do niego przy użyciu <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> właściwości, a kompletny schemat jest kompilowany przy użyciu <xref:System.Xml.Schema.XmlSchemaSet> klasy i zapisywana w konsoli.  
  
 [!code-cpp[XmlSchemaCreateExample#4](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaCreateExample/CPP/XmlSchemaCreateExample.cpp#4)]
 [!code-csharp[XmlSchemaCreateExample#4](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaCreateExample/CS/XmlSchemaCreateExample.cs#4)]
 [!code-vb[XmlSchemaCreateExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaCreateExample/VB/XmlSchemaCreateExample.vb#4)]  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A?displayProperty=nameWithType> Metoda sprawdza poprawność schematu klienta względem reguł schematu XML i umożliwia dostęp do właściwości kompilacji po schemacie.  
  
> [!NOTE]
> Wszystkie właściwości kompilacji po schemacie w interfejsie API modelu SOM różnią się w zależności od posprawdzonych.  
  
 <xref:System.Xml.Schema.ValidationEventHandler> Dodanie do obiektu <xref:System.Xml.Schema.XmlSchemaSet> jest delegatem, który wywołuje metodę `ValidationCallback` wywołania zwrotnego w celu obsługi ostrzeżeń i błędów walidacji schematu.  
  
 Poniżej znajduje się kompletny przykład kodu i schemat klienta zapisany w konsoli programu.  
  
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

- [Model SOM (XML Schema Object Model) ― omówienie](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)
- [Odczytywanie i zapisywanie schematów XML](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)
- [Przechodzenie schematów XML](../../../../docs/standard/data/xml/traversing-xml-schemas.md)
- [Edytowanie schematów XML](../../../../docs/standard/data/xml/editing-xml-schemas.md)
- [Uwzględnianie lub importowanie schematów XML](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)
- [Klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Zestaw informacji po kompilacji schematu](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)

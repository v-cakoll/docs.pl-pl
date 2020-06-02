---
title: Zestaw informacji po kompilacji schematu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
ms.openlocfilehash: 3bd0c6063fee1fa1a9f046a8be2ebfde07aea9ee
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291516"
---
# <a name="post-schema-compilation-infoset"></a>Zestaw informacji po kompilacji schematu
[Zalecenie dotyczące schematu XML organizacja World Wide Web Consortium (W3C)](https://www.w3.org/XML/Schema) omawia zestaw informacji (sprawdzonych), który musi być narażony na weryfikację przed schematem i kompilację po schemacie. Model obiektów schematu XML (SOM) przegląda to narażenie przed i po <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> wywołaniu metody.  
  
 Sprawdzonych weryfikacji przed schematem jest tworzony podczas edytowania schematu. Kompilacja po schemacie sprawdzonych jest generowana po <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> wywołaniu metody, podczas kompilowania schematu i jest udostępniana jako właściwości.  
  
 SOM jest modelem obiektów, który reprezentuje walidację przedprodukcyjną i kompilację po schemacie Infosets; składa się z klas w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw. Wszystkie właściwości odczytu i zapisu klas w <xref:System.Xml.Schema> przestrzeni nazw należą do sprawdzonych weryfikacji przed schematem, podczas gdy wszystkie właściwości tylko do odczytu klas w <xref:System.Xml.Schema> przestrzeni nazw należą do kompilacji po schemacie sprawdzonych. Wyjątkiem od tej reguły są następujące właściwości, które są zarówno walidacją presprawdzonych, jak i sprawdzonych właściwości kompilacji po schemacie.  
  
|Klasa|Właściwość|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 Na przykład <xref:System.Xml.Schema.XmlSchemaElement> <xref:System.Xml.Schema.XmlSchemaComplexType> klasy i mają `BlockResolved` właściwości i `FinalResolved` . Te właściwości są używane do przechowywania wartości `Block` `Final` właściwości i po skompilowaniu i sprawdzeniu schematu. `BlockResolved`i `FinalResolved` są właściwościami tylko do odczytu, które są częścią kompilacji po schemacie sprawdzonych.  
  
 Poniższy przykład pokazuje <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> Właściwość <xref:System.Xml.Schema.XmlSchemaElement> zestawu klasy po walidacji schematu. Przed walidacją Właściwość zawiera `null` odwołanie i <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> jest ustawiana na nazwę danego typu. Po walidacji, <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> jest rozpoznawany jako prawidłowy typ, a obiekt Type jest dostępny za pomocą <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> właściwości.  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Model SOM (XML Schema Object Model)](xml-schema-object-model-som.md)

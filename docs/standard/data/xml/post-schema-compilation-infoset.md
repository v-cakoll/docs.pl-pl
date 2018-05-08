---
title: Obiekt typu Infoset schematu po kompilacji
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db1c952003e73beb756567be74ed4eb72612c989
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="post-schema-compilation-infoset"></a>Obiekt typu Infoset schematu po kompilacji
[Zalecenie schematu XML w sieci World Wide Web konsorcjum W3C](https://www.w3.org/XML/Schema) omówiono zestaw informacji (obiekt typu infoset) muszą być widoczne dla sprawdzanie poprawności schematu przed i po schematu kompilacji. Model obiektu schematu XML (SOM) widoków tego narażenia przed i po <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda <xref:System.Xml.Schema.XmlSchemaSet> jest wywoływana.  
  
 Obiekt typu infoset sprawdzanie poprawności schematu przed jest tworzona podczas edytowania schematu. Obiekt typu infoset schematu po kompilacji jest generowany po <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda <xref:System.Xml.Schema.XmlSchemaSet> jest wywoływana podczas kompilowania schematu i jest udostępniany jako właściwości.  
  
 SOM to model obiektu, który reprezentuje sprawdzanie poprawności schematu przed i po schematu kompilacji infosets; składa się z klas w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw. Wszystkie odczytu i zapisu właściwości klas w <xref:System.Xml.Schema> przestrzeni nazw należy do typu infoset sprawdzanie poprawności schematu wstępne podczas wszystkich tylko do odczytu właściwości klas w <xref:System.Xml.Schema> przestrzeni nazw należy do obiektu typu infoset schematu po kompilacji. Wyjątkiem od tej reguły są następujące właściwości, które są typu infoset sprawdzanie poprawności schematu wstępne i właściwości obiektu typu infoset schematu po kompilacji.  
  
|Class|Właściwość|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 Na przykład <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaComplexType> klasy zarówno mają `BlockResolved` i `FinalResolved` właściwości. Te właściwości są używane do przechowywania wartości `Block` i `Final` właściwości po schemat został skompilowany i sprawdzania poprawności. `BlockResolved` i `FinalResolved` są właściwości tylko do odczytu, które są częścią typu infoset schematu po kompilacji.  
  
 W poniższym przykładzie przedstawiono <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> właściwość <xref:System.Xml.Schema.XmlSchemaElement> klasy zestawu po sprawdzania poprawności schematu. Przed sprawdzania poprawności, ta właściwość zawiera `null` odwołanie i <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> jest ustawiona na nazwę typu zagrożona. Po sprawdzeniu poprawności <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> jest rozwiązane do prawidłowego typu i jest dostępna za pośrednictwem obiektu typu <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> właściwości.  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Model SOM (XML Schema Object Model)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)

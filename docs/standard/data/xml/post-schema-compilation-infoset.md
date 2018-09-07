---
title: Zestaw informacji po kompilacji schematu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e7892289248c9651b529bcc68d7228b8babb28a
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083822"
---
# <a name="post-schema-compilation-infoset"></a>Zestaw informacji po kompilacji schematu
[Zaleceniem schematu XML World Wide Web Consortium (W3C)](https://www.w3.org/XML/Schema) w tym artykule omówiono zestaw informacji (zestaw informacji) muszą być widoczne dla sprawdzanie poprawności schematu przed i po kompilacji schematu. Model obiektu schematu XML (SOM) widoki tego zagrożenia, przed i po nim <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda <xref:System.Xml.Schema.XmlSchemaSet> jest wywoływana.  
  
 Zestaw informacji sprawdzania poprawności schematu wstępnego została stworzona podczas edycji schematu. Zestaw informacji po kompilacji schematu jest generowany po <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda <xref:System.Xml.Schema.XmlSchemaSet> jest wywoływana podczas kompilowania schematów i jest udostępniany jako właściwości.  
  
 Model SOM to model obiektów, który reprezentuje sprawdzanie poprawności schematu przed i po kompilacji schematu infosets; składa się z klas w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw. Wszystkie Odczyt i zapis właściwości klas w <xref:System.Xml.Schema> przestrzeni nazw należą do zestaw informacji sprawdzania poprawności schematu przed, podczas wszystkich tylko do odczytu właściwości klas w <xref:System.Xml.Schema> przestrzeni nazw należą do zestaw informacji po kompilacji schematu. Wyjątkiem od tej reguły są następujące właściwości, które są zarówno zestaw informacji sprawdzania poprawności schematu wstępne i właściwości zestaw informacji po kompilacji schematu.  
  
|Class|Właściwość|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 Na przykład <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaComplexType> mają obu klas `BlockResolved` i `FinalResolved` właściwości. Te właściwości są używane do przechowywania wartości `Block` i `Final` właściwości po schemat został skompilowany i zweryfikowane. `BlockResolved` i `FinalResolved` są właściwości tylko do odczytu, które są częścią zestaw informacji po kompilacji schematu.  
  
 W poniższym przykładzie przedstawiono <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> właściwość <xref:System.Xml.Schema.XmlSchemaElement> klasy zestawu po poprawności schematu. Przed sprawdzania poprawności, ta właściwość zawiera `null` odwołania, a <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> jest ustawiona na nazwę typu zagrożona. Po zakończeniu walidacji <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> jest tłumaczona na prawidłowy typ i obiektu typu jest dostępna za pośrednictwem <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> właściwości.  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Model SOM (XML Schema Object Model)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)

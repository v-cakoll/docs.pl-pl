---
title: Obiekt typu Infoset schematu po kompilacji
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
ms.assetid: 7f1bc7f4-401b-459f-9078-f099cc711fde
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 77fe1790a4ff2f910a740e969e458549f1fd9642
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="post-schema-compilation-infoset"></a><span data-ttu-id="4eae9-102">Obiekt typu Infoset schematu po kompilacji</span><span class="sxs-lookup"><span data-stu-id="4eae9-102">Post-Schema Compilation Infoset</span></span>
<span data-ttu-id="4eae9-103">[Zalecenie schematu XML w sieci World Wide Web konsorcjum W3C](http://go.microsoft.com/fwlink/?linkid=45242) omówiono zestaw informacji (obiekt typu infoset) muszą być widoczne dla sprawdzanie poprawności schematu przed i po schematu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4eae9-103">The [World Wide Web Consortium (W3C) XML Schema Recommendation](http://go.microsoft.com/fwlink/?linkid=45242) discusses the information set (infoset) that must be exposed for pre-schema validation and post-schema compilation.</span></span> <span data-ttu-id="4eae9-104">Model obiektu schematu XML (SOM) widoków tego narażenia przed i po <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda <xref:System.Xml.Schema.XmlSchemaSet> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="4eae9-104">The XML Schema Object Model (SOM) views this exposure before and after the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called.</span></span>  
  
 <span data-ttu-id="4eae9-105">Obiekt typu infoset sprawdzanie poprawności schematu przed jest tworzona podczas edytowania schematu.</span><span class="sxs-lookup"><span data-stu-id="4eae9-105">The pre-schema validation infoset is built during the editing of the schema.</span></span> <span data-ttu-id="4eae9-106">Obiekt typu infoset schematu po kompilacji jest generowany po <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda <xref:System.Xml.Schema.XmlSchemaSet> jest wywoływana podczas kompilowania schematu i jest udostępniany jako właściwości.</span><span class="sxs-lookup"><span data-stu-id="4eae9-106">The post-schema compilation infoset is generated after the <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> method of the <xref:System.Xml.Schema.XmlSchemaSet> is called, during compilation of the schema, and is exposed as properties.</span></span>  
  
 <span data-ttu-id="4eae9-107">SOM to model obiektu, który reprezentuje sprawdzanie poprawności schematu przed i po schematu kompilacji infosets; składa się z klas w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4eae9-107">The SOM is the object model that represents the pre-schema validation and post-schema compilation infosets; it consists of the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="4eae9-108">Wszystkie odczytu i zapisu właściwości klas w <xref:System.Xml.Schema> przestrzeni nazw należy do typu infoset sprawdzanie poprawności schematu wstępne podczas wszystkich tylko do odczytu właściwości klas w <xref:System.Xml.Schema> przestrzeni nazw należy do obiektu typu infoset schematu po kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4eae9-108">All read and write properties of classes in the <xref:System.Xml.Schema> namespace belong to the pre-schema validation infoset, while all read-only properties of classes in the <xref:System.Xml.Schema> namespace belong to the post-schema compilation infoset.</span></span> <span data-ttu-id="4eae9-109">Wyjątkiem od tej reguły są następujące właściwości, które są typu infoset sprawdzanie poprawności schematu wstępne i właściwości obiektu typu infoset schematu po kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4eae9-109">The exception to this rule are the following properties, which are both pre-schema validation infoset and post-schema compilation infoset properties.</span></span>  
  
|<span data-ttu-id="4eae9-110">Class</span><span class="sxs-lookup"><span data-stu-id="4eae9-110">Class</span></span>|<span data-ttu-id="4eae9-111">Właściwość</span><span class="sxs-lookup"><span data-stu-id="4eae9-111">Property</span></span>|  
|-----------|--------------|  
|<xref:System.Xml.Schema.XmlSchemaObject>|<xref:System.Xml.Schema.XmlSchemaObject.Parent%2A>|  
|<xref:System.Xml.Schema.XmlSchema>|<span data-ttu-id="4eae9-112"><xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="4eae9-112"><xref:System.Xml.Schema.XmlSchema.AttributeFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.BlockDefault%2A>, <xref:System.Xml.Schema.XmlSchema.ElementFormDefault%2A>, <xref:System.Xml.Schema.XmlSchema.FinalDefault%2A>, <xref:System.Xml.Schema.XmlSchema.TargetNamespace%2A></span></span>|  
|<xref:System.Xml.Schema.XmlSchemaExternal>|<xref:System.Xml.Schema.XmlSchemaExternal.Schema%2A>|  
|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup.AnyAttribute%2A>|  
|<xref:System.Xml.Schema.XmlSchemaParticle>|<span data-ttu-id="4eae9-113"><xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A></span><span class="sxs-lookup"><span data-stu-id="4eae9-113"><xref:System.Xml.Schema.XmlSchemaParticle.MaxOccurs%2A>, <xref:System.Xml.Schema.XmlSchemaParticle.MinOccurs%2A></span></span>|  
|<xref:System.Xml.Schema.XmlSchemaComplexType>|<xref:System.Xml.Schema.XmlSchemaComplexType.AnyAttribute%2A>|  
  
 <span data-ttu-id="4eae9-114">Na przykład <xref:System.Xml.Schema.XmlSchemaElement> i <xref:System.Xml.Schema.XmlSchemaComplexType> klasy zarówno mają `BlockResolved` i `FinalResolved` właściwości.</span><span class="sxs-lookup"><span data-stu-id="4eae9-114">For example, the <xref:System.Xml.Schema.XmlSchemaElement> and <xref:System.Xml.Schema.XmlSchemaComplexType> classes both have `BlockResolved` and `FinalResolved` properties.</span></span> <span data-ttu-id="4eae9-115">Te właściwości są używane do przechowywania wartości `Block` i `Final` właściwości po schemat został skompilowany i sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="4eae9-115">These properties are used to hold the values for the `Block` and `Final` properties after the schema has been compiled and validated.</span></span> <span data-ttu-id="4eae9-116">`BlockResolved`i `FinalResolved` są właściwości tylko do odczytu, które są częścią typu infoset schematu po kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4eae9-116">`BlockResolved` and `FinalResolved` are read-only properties that are part of the post-schema compilation infoset.</span></span>  
  
 <span data-ttu-id="4eae9-117">W poniższym przykładzie przedstawiono <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> właściwość <xref:System.Xml.Schema.XmlSchemaElement> klasy zestawu po sprawdzania poprawności schematu.</span><span class="sxs-lookup"><span data-stu-id="4eae9-117">The following example shows the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> property of the <xref:System.Xml.Schema.XmlSchemaElement> class set after validating the schema.</span></span> <span data-ttu-id="4eae9-118">Przed sprawdzania poprawności, ta właściwość zawiera `null` odwołanie i <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> jest ustawiona na nazwę typu zagrożona.</span><span class="sxs-lookup"><span data-stu-id="4eae9-118">Before validation, the property contains a `null` reference, and the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> is set to the name of the type in question.</span></span> <span data-ttu-id="4eae9-119">Po sprawdzeniu poprawności <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> jest rozwiązane do prawidłowego typu i jest dostępna za pośrednictwem obiektu typu <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4eae9-119">After validation, the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> is resolved to a valid type, and the type object is available through the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> property.</span></span>  
  
 [!code-cpp[PsciSample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/PsciSample/CPP/PsciSample.cpp#1)]
 [!code-csharp[PsciSample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/PsciSample/CS/PsciSample.cs#1)]
 [!code-vb[PsciSample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/PsciSample/VB/PsciSample.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4eae9-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4eae9-120">See Also</span></span>  
 [<span data-ttu-id="4eae9-121">Model obiektu schematu XML (SOM)</span><span class="sxs-lookup"><span data-stu-id="4eae9-121">XML Schema Object Model (SOM)</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)

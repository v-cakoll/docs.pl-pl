---
title: "Za pomocą języka XML w zestawie danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 28c1668dcb9678b65db62c0040adcd116221b92e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-xml-in-a-dataset"></a><span data-ttu-id="6f723-102">Za pomocą języka XML w zestawie danych</span><span class="sxs-lookup"><span data-stu-id="6f723-102">Using XML in a DataSet</span></span>
<span data-ttu-id="6f723-103">Z ADO.NET możesz wpisać <xref:System.Data.DataSet> ze strumienia XML lub dokumentu.</span><span class="sxs-lookup"><span data-stu-id="6f723-103">With ADO.NET you can fill a <xref:System.Data.DataSet> from an XML stream or document.</span></span> <span data-ttu-id="6f723-104">Strumień XML lub dokument można użyć do dostarczenia <xref:System.Data.DataSet> danych, informacje o schemacie lub obu.</span><span class="sxs-lookup"><span data-stu-id="6f723-104">You can use the XML stream or document to supply to the <xref:System.Data.DataSet> either data, schema information, or both.</span></span> <span data-ttu-id="6f723-105">Informacje podane w strumieniu XML lub dokument można połączyć z istniejących danych i informacji o schemacie znajduje się już w <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="6f723-105">The information supplied from the XML stream or document can be combined with existing data or schema information already present in the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="6f723-106">ADO.NET umożliwia również tworzenie reprezentację XML <xref:System.Data.DataSet>, z lub bez jego schemat, aby przetransportować <xref:System.Data.DataSet> przez HTTP do użycia przez inną platformie włączone XML lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f723-106">ADO.NET also allows you to create an XML representation of a <xref:System.Data.DataSet>, with or without its schema, in order to transport the <xref:System.Data.DataSet> across HTTP for use by another application or XML-enabled platform.</span></span> <span data-ttu-id="6f723-107">W reprezentacji XML <xref:System.Data.DataSet>, dane są zapisywane w pliku XML i schemat, jeśli jest dołączony wbudowany w reprezentacji, jest zapisywany przy użyciu języka definicji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="6f723-107">In an XML representation of a <xref:System.Data.DataSet>, the data is written in XML and the schema, if it is included inline in the representation, is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="6f723-108">XML i schematu XML zapewniają wygodną format przesyłania zawartości <xref:System.Data.DataSet> do i z klientów zdalnych.</span><span class="sxs-lookup"><span data-stu-id="6f723-108">XML and XML Schema provide a convenient format for transferring the contents of a <xref:System.Data.DataSet> to and from remote clients.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f723-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6f723-109">In This Section</span></span>  
 [<span data-ttu-id="6f723-110">DataSets</span><span class="sxs-lookup"><span data-stu-id="6f723-110">DiffGrams</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)  
 <span data-ttu-id="6f723-111">Zawiera szczegółowe informacje na format XML używany do odczytu i zapisu zawartości w formacie DiffGram <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="6f723-111">Provides details on the DiffGram, an XML format used to read and write the contents of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="6f723-112">Podczas ładowania zestawu danych z pliku XML</span><span class="sxs-lookup"><span data-stu-id="6f723-112">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 <span data-ttu-id="6f723-113">W tym artykule omówiono różne opcje, które należy uwzględnić podczas ładowania zawartości <xref:System.Data.DataSet> z dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="6f723-113">Discusses different options to consider when loading the contents of a <xref:System.Data.DataSet> from an XML document.</span></span>  
  
 [<span data-ttu-id="6f723-114">Zapisywanie zawartości zestawu danych jako dane XML</span><span class="sxs-lookup"><span data-stu-id="6f723-114">Writing DataSet Contents as XML Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 <span data-ttu-id="6f723-115">W tym artykule omówiono sposób generowania zawartości <xref:System.Data.DataSet> jako dane XML i można użyć różnych opcji formatu XML.</span><span class="sxs-lookup"><span data-stu-id="6f723-115">Discusses how to generate the contents of a <xref:System.Data.DataSet> as XML data, and the different XML format options you can use.</span></span>  
  
 [<span data-ttu-id="6f723-116">Ładowanie informacji o schemacie zestawu danych z pliku XML</span><span class="sxs-lookup"><span data-stu-id="6f723-116">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 <span data-ttu-id="6f723-117">W tym artykule omówiono <xref:System.Data.DataSet> metody używane do ładowania schematu <xref:System.Data.DataSet> z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="6f723-117">Discusses the <xref:System.Data.DataSet> methods used to load the schema of a <xref:System.Data.DataSet> from XML.</span></span>  
  
 [<span data-ttu-id="6f723-118">Zapisywanie informacji o schemacie zestawu danych jako XSD</span><span class="sxs-lookup"><span data-stu-id="6f723-118">Writing DataSet Schema Information as XSD</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-schema-information-as-xsd.md)  
 <span data-ttu-id="6f723-119">W tym artykule omówiono zastosowania schematu XML i sposób generowania z <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="6f723-119">Discusses the uses for an XML Schema and how to generate one from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="6f723-120">Zestaw danych i dokumentu XmlDataDocument synchronizacji</span><span class="sxs-lookup"><span data-stu-id="6f723-120">DataSet and XmlDataDocument Synchronization</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataset-and-xmldatadocument-synchronization.md)  
 <span data-ttu-id="6f723-121">Zawiera omówienie możliwości dostępnych w programie .NET Framework synchronicznego dostępu do widoków relacyjnych i hierarchicznych jednego zestawu danych, a pokazano, jak utworzyć synchroniczne relacji między <xref:System.Data.DataSet> i <xref:System.Xml.XmlDataDocument>.</span><span class="sxs-lookup"><span data-stu-id="6f723-121">Discusses the capability available in the .NET Framework of synchronous access to both relational and hierarchical views of a single set of data, and shows how to create a synchronous relationship between a <xref:System.Data.DataSet> and an <xref:System.Xml.XmlDataDocument>.</span></span>  
  
 [<span data-ttu-id="6f723-122">DataRelations zagnieżdżenia</span><span class="sxs-lookup"><span data-stu-id="6f723-122">Nesting DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/nesting-datarelations.md)  
 <span data-ttu-id="6f723-123">W tym artykule omówiono znaczenie zagnieżdżonych <xref:System.Data.DataRelation> obiektów po reprezentujący zawartość <xref:System.Data.DataSet> danych XML oraz sposób ich tworzenia.</span><span class="sxs-lookup"><span data-stu-id="6f723-123">Discusses the importance of nested <xref:System.Data.DataRelation> objects when representing the contents of a <xref:System.Data.DataSet> as XML data, and describes how to create them.</span></span>  
  
 [<span data-ttu-id="6f723-124">Wyprowadzanie relacyjne struktury zestawu danych z schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="6f723-124">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="6f723-125">Opisuje relacyjne struktury lub schematu z <xref:System.Data.DataSet> która jest tworzona na podstawie schematu XML.</span><span class="sxs-lookup"><span data-stu-id="6f723-125">Describes the relational structure, or schema, of a <xref:System.Data.DataSet> that is created from XML Schema.</span></span>  
  
 [<span data-ttu-id="6f723-126">Wnioskowanie struktury zestawu danych relacyjnych z pliku XML</span><span class="sxs-lookup"><span data-stu-id="6f723-126">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 <span data-ttu-id="6f723-127">Opisuje wynikowy relacyjne struktury lub schematu z <xref:System.Data.DataSet> utworzonego podczas wywnioskować na podstawie elementów XML.</span><span class="sxs-lookup"><span data-stu-id="6f723-127">Describes the resulting relational structure, or schema, of a <xref:System.Data.DataSet> that is created when inferred from XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6f723-128">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="6f723-128">Related Sections</span></span>  
 [<span data-ttu-id="6f723-129">ADO.NET — omówienie</span><span class="sxs-lookup"><span data-stu-id="6f723-129">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 <span data-ttu-id="6f723-130">W tym artykule opisano ADO.NET architektury i składników i sposobu ich używania dostęp do istniejących źródeł danych oraz do zarządzania danymi w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6f723-130">Describes the ADO.NET architecture and components, and how to use them to access existing data sources as well as to manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f723-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f723-131">See Also</span></span>  
 [<span data-ttu-id="6f723-132">Zbiory danych, DataTables i DataViews</span><span class="sxs-lookup"><span data-stu-id="6f723-132">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="6f723-133">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="6f723-133">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)

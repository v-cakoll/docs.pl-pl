---
title: "Generowanie biblioteki klienta usługi danych (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5fbf45a3447a1dc5fb449628bdd7f741fb3e8324
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="72759-102">Generowanie biblioteki klienta usługi danych (usługi danych WCF)</span><span class="sxs-lookup"><span data-stu-id="72759-102">Generating the Data Service Client Library (WCF Data Services)</span></span>
<span data-ttu-id="72759-103">Usługi danych, który implementuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] może zwrócić dokument metadanych usługi, który opisuje modelu danych udostępnianych przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych.</span><span class="sxs-lookup"><span data-stu-id="72759-103">A data service that implements the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] can return a service metadata document that describes the data model exposed by the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="72759-104">Aby uzyskać więcej informacji, zobacz [OData: Dokument metadanych usługi](http://go.microsoft.com/fwlink/?LinkId=186070).</span><span class="sxs-lookup"><span data-stu-id="72759-104">For more information, see [OData: Service Metadata Document](http://go.microsoft.com/fwlink/?LinkId=186070).</span></span> <span data-ttu-id="72759-105">Można użyć **Dodaj odwołanie do usługi** okna dialogowego w programie Visual Studio można dodać odwołania do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— na podstawie usługi.</span><span class="sxs-lookup"><span data-stu-id="72759-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service.</span></span> <span data-ttu-id="72759-106">Jeśli używasz tego narzędzia można dodać odwołania do metadanych zwróconych przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych w projekcie klienta, wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="72759-106">When you use this tool to add a reference to the metadata returned by an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed in a client project, it performs the following actions:</span></span>  
  
-   <span data-ttu-id="72759-107">Żądania dokument metadanych usługi z usługą danych i interpretowania metadane zwrócony.</span><span class="sxs-lookup"><span data-stu-id="72759-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="72759-108">Zwrócone metadane są przechowywane w projektu klienta jako plik edmx.</span><span class="sxs-lookup"><span data-stu-id="72759-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="72759-109">Nie można otworzyć tego pliku edmx przy użyciu narzędzia Projektant modelu danych jednostki, ponieważ nie ma taki sam format pliku edmx, używany przez program Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="72759-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="72759-110">Ten plik metadanych można wyświetlić za pomocą edytora XML lub edytorze tekstu.</span><span class="sxs-lookup"><span data-stu-id="72759-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="72759-111">Aby uzyskać więcej informacji, zobacz [ \[MC EDMX\]: modelu Entity Data Model danych usługi tworzenia pakietów formatu](http://go.microsoft.com/fwlink/?LinkID=178833) specyfikacji</span><span class="sxs-lookup"><span data-stu-id="72759-111">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](http://go.microsoft.com/fwlink/?LinkID=178833) specification</span></span>  
  
-   <span data-ttu-id="72759-112">Generuje reprezentację usługi jako klasy kontenera jednostka, która dziedziczy <xref:System.Data.Services.Client.DataServiceContext>.</span><span class="sxs-lookup"><span data-stu-id="72759-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="72759-113">Ta klasa kontenera jednostek wygenerowanego podobny do kontenera jednostek, który generuje narzędzi modelu danych jednostki.</span><span class="sxs-lookup"><span data-stu-id="72759-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="72759-114">Aby uzyskać więcej informacji, zobacz [obiektu usługi — omówienie (Entity Framework)](http://msdn.microsoft.com/en-us/43014cf9-c9cb-4538-bfbb-197820b60038).</span><span class="sxs-lookup"><span data-stu-id="72759-114">For more information, see [Object Services Overview (Entity Framework)](http://msdn.microsoft.com/en-us/43014cf9-c9cb-4538-bfbb-197820b60038).</span></span>  
  
-   <span data-ttu-id="72759-115">Generuje klasy danych do typów modelu danych, które wykryje w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="72759-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
-   <span data-ttu-id="72759-116">Dodanie odwołania do `System.Data.Services.Client` zestawu do projektu.</span><span class="sxs-lookup"><span data-stu-id="72759-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="72759-117">Aby uzyskać więcej informacji, zobacz [porady: Dodawanie odwołania do danych usługi](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="72759-117">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="72759-118">Klasy usługi danych klienta może być również generowany przy użyciu [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) narzędzia w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="72759-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="72759-119">Aby uzyskać więcej informacji, zobacz [porady: ręcznie wygenerować klienta usługi klas danych](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="72759-119">For more information, see [How to: Manually Generate Client Data Service Classes](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="72759-120">Mapowanie typu danych klienta</span><span class="sxs-lookup"><span data-stu-id="72759-120">Client Data Type Mapping</span></span>  
 <span data-ttu-id="72759-121">Jeśli używasz **Dodaj odwołanie do usługi** okna dialogowego w programie Visual Studio lub `DataSvcUtil.exe` narzędzie do generowania klasy danych klienta, które są oparte na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych, typy danych .NET Framework są mapowane na typy pierwotne z model bazy danych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="72759-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="72759-122">Typ modelu danych</span><span class="sxs-lookup"><span data-stu-id="72759-122">Data model type</span></span>|<span data-ttu-id="72759-123">Typ danych .NET framework</span><span class="sxs-lookup"><span data-stu-id="72759-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="72759-124"><xref:System.Byte>`[]`</span><span class="sxs-lookup"><span data-stu-id="72759-124"><xref:System.Byte> `[]`</span></span>|  
|`Edm.Boolean`|<xref:System.Boolean>|  
|`Edm.Byte`|<xref:System.Byte>|  
|`Edm.DateTime`|<xref:System.DateTime>|  
|`Edm.Decimal`|<xref:System.Decimal>|  
|`Edm.Double`|<xref:System.Double>|  
|`Edm.Guid`|<xref:System.Guid>|  
|`Edm.Int16`|<xref:System.Int16>|  
|`Edm.Int32`|<xref:System.Int32>|  
|`Edm.Int64`|<xref:System.Int64>|  
|`Edm.SByte`|<xref:System.SByte>|  
|`Edm.Single`|<xref:System.Single>|  
|`Edm.String`|<xref:System.String>|  
  
 <span data-ttu-id="72759-125">Aby uzyskać więcej informacji, zobacz [OData: typy pierwotne danych](http://go.microsoft.com/fwlink/?LinkId=186072).</span><span class="sxs-lookup"><span data-stu-id="72759-125">For more information, see [OData: Primitive Data Types](http://go.microsoft.com/fwlink/?LinkId=186072).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72759-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72759-126">See Also</span></span>  
 [<span data-ttu-id="72759-127">Biblioteka klienta usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="72759-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [<span data-ttu-id="72759-128">Szybki Start</span><span class="sxs-lookup"><span data-stu-id="72759-128">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

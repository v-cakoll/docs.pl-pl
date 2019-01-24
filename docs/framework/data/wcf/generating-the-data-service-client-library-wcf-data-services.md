---
title: Generowanie biblioteki klienta usługi danych (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: b550af85bcd4bec30707721c6549c7b9094bfd1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630908"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="c42c8-102">Generowanie biblioteki klienta usługi danych (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="c42c8-102">Generating the Data Service Client Library (WCF Data Services)</span></span>
<span data-ttu-id="c42c8-103">Usługi danych, który implementuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] może zwrócić dokument metadanych usług, który opisuje model danych udostępnianych przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych.</span><span class="sxs-lookup"><span data-stu-id="c42c8-103">A data service that implements the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] can return a service metadata document that describes the data model exposed by the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="c42c8-104">Aby uzyskać więcej informacji, zobacz [OData: Dokument metadanych usługi](https://go.microsoft.com/fwlink/?LinkId=186070).</span><span class="sxs-lookup"><span data-stu-id="c42c8-104">For more information, see [OData: Service Metadata Document](https://go.microsoft.com/fwlink/?LinkId=186070).</span></span> <span data-ttu-id="c42c8-105">Możesz użyć **Dodaj odwołanie do usługi** w programie Visual Studio można dodać odwołania do okna dialogowego [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— na podstawie usługi.</span><span class="sxs-lookup"><span data-stu-id="c42c8-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service.</span></span> <span data-ttu-id="c42c8-106">Kiedy używać tego narzędzia można dodać odwołania do metadanych zwróconych przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych w projekcie klienta, wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c42c8-106">When you use this tool to add a reference to the metadata returned by an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed in a client project, it performs the following actions:</span></span>  
  
-   <span data-ttu-id="c42c8-107">Żądanie dokumentu metadanych usługi z usługi danych, a następnie interpretuje zwróconych metadanych.</span><span class="sxs-lookup"><span data-stu-id="c42c8-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c42c8-108">Zwróconych metadanych znajduje się w projekcie klienta jako pliku edmx.</span><span class="sxs-lookup"><span data-stu-id="c42c8-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="c42c8-109">Nie można otworzyć tego pliku edmx przy użyciu projektanta modelu Entity Data Model, ponieważ nie ma taki sam format pliku edmx używane przez program Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c42c8-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="c42c8-110">Ten plik metadanych można wyświetlić za pomocą edytora XML lub dowolnego edytora tekstów.</span><span class="sxs-lookup"><span data-stu-id="c42c8-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="c42c8-111">Aby uzyskać więcej informacji, zobacz [ \[MC EDMX\]: Model Entity Data Model do formatu pakietu usług danych](https://go.microsoft.com/fwlink/?LinkID=178833) specyfikacji</span><span class="sxs-lookup"><span data-stu-id="c42c8-111">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](https://go.microsoft.com/fwlink/?LinkID=178833) specification</span></span>  
  
-   <span data-ttu-id="c42c8-112">Generuje reprezentację usługi jako klasa kontenera jednostki, która dziedziczy <xref:System.Data.Services.Client.DataServiceContext>.</span><span class="sxs-lookup"><span data-stu-id="c42c8-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="c42c8-113">Ta klasa kontenera jednostki wygenerowanego przypomina kontener jednostek, które generują narzędzia modelu Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="c42c8-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="c42c8-114">Aby uzyskać więcej informacji, zobacz [obiektu usługi — omówienie (Entity Framework)](https://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).</span><span class="sxs-lookup"><span data-stu-id="c42c8-114">For more information, see [Object Services Overview (Entity Framework)](https://msdn.microsoft.com/library/43014cf9-c9cb-4538-bfbb-197820b60038).</span></span>  
  
-   <span data-ttu-id="c42c8-115">Generuje klasy danych dla typów modelu danych, które wykryje w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="c42c8-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
-   <span data-ttu-id="c42c8-116">Dodanie odwołania do `System.Data.Services.Client` zestawu do projektu.</span><span class="sxs-lookup"><span data-stu-id="c42c8-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="c42c8-117">Aby uzyskać więcej informacji, zobacz [jak: Dodaj odwołanie do usługi danych](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="c42c8-117">For more information, see [How to: Add a Data Service Reference](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="c42c8-118">Klas usługi danych klienta mogą być też generowane przy użyciu [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) narzędzia w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="c42c8-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="c42c8-119">Aby uzyskać więcej informacji, zobacz [jak: Ręczne Generowanie klas usługi danych klienta](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="c42c8-119">For more information, see [How to: Manually Generate Client Data Service Classes](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="c42c8-120">Mapowanie typu danych klienta</span><span class="sxs-lookup"><span data-stu-id="c42c8-120">Client Data Type Mapping</span></span>  
 <span data-ttu-id="c42c8-121">Kiedy używasz **Dodaj odwołanie do usługi** okna dialogowego w programie Visual Studio lub `DataSvcUtil.exe` narzędzie do generowania klasy danych klienta, które są oparte na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] kanału informacyjnego, typów danych programu .NET Framework są mapowane na typy pierwotne z modelu danych w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="c42c8-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="c42c8-122">Typ modelu danych</span><span class="sxs-lookup"><span data-stu-id="c42c8-122">Data model type</span></span>|<span data-ttu-id="c42c8-123">Typ danych .NET framework</span><span class="sxs-lookup"><span data-stu-id="c42c8-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="c42c8-124"><xref:System.Byte>`[]`</span><span class="sxs-lookup"><span data-stu-id="c42c8-124"><xref:System.Byte> `[]`</span></span>|  
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
  
 <span data-ttu-id="c42c8-125">Aby uzyskać więcej informacji, zobacz [OData: Pierwotne typy danych](https://go.microsoft.com/fwlink/?LinkId=186072).</span><span class="sxs-lookup"><span data-stu-id="c42c8-125">For more information, see [OData: Primitive Data Types](https://go.microsoft.com/fwlink/?LinkId=186072).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c42c8-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c42c8-126">See also</span></span>
- [<span data-ttu-id="c42c8-127">Biblioteka klienta usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="c42c8-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [<span data-ttu-id="c42c8-128">Szybki start</span><span class="sxs-lookup"><span data-stu-id="c42c8-128">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)

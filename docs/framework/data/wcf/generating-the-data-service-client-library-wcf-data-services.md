---
title: Generowanie biblioteki klienta usługi danych (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- Add Service Reference dialog box
ms.assetid: 314077c1-ac10-47e1-bed4-940b5462359d
ms.openlocfilehash: d53f2d209d6fb0a6f3cadb96245338060ece87db
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780285"
---
# <a name="generating-the-data-service-client-library-wcf-data-services"></a><span data-ttu-id="788c9-102">Generowanie biblioteki klienta usługi danych (Usługi danych programu WCF)</span><span class="sxs-lookup"><span data-stu-id="788c9-102">Generating the Data Service Client Library (WCF Data Services)</span></span>
<span data-ttu-id="788c9-103">Usługa danych implementująca [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] może zwrócić dokument metadanych usługi, który opisuje model danych uwidoczniony [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] przez kanał informacyjny.</span><span class="sxs-lookup"><span data-stu-id="788c9-103">A data service that implements the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] can return a service metadata document that describes the data model exposed by the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed.</span></span> <span data-ttu-id="788c9-104">Aby uzyskać więcej informacji, [zobacz OData: Dokument](https://go.microsoft.com/fwlink/?LinkId=186070)metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="788c9-104">For more information, see [OData: Service Metadata Document](https://go.microsoft.com/fwlink/?LinkId=186070).</span></span> <span data-ttu-id="788c9-105">Możesz użyć okna dialogowego **Dodaj odwołanie do usługi** w programie Visual Studio, aby dodać odwołanie do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]usługi opartej na usłudze.</span><span class="sxs-lookup"><span data-stu-id="788c9-105">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based service.</span></span> <span data-ttu-id="788c9-106">W przypadku użycia tego narzędzia do dodania odwołania do metadanych zwracanych przez [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródło danych w projekcie klienta wykonywane są następujące akcje:</span><span class="sxs-lookup"><span data-stu-id="788c9-106">When you use this tool to add a reference to the metadata returned by an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed in a client project, it performs the following actions:</span></span>  
  
- <span data-ttu-id="788c9-107">Żąda dokumentu metadanych usługi z usługi danych i interpretuje zwrócone metadane.</span><span class="sxs-lookup"><span data-stu-id="788c9-107">Requests the service metadata document from the data service and interprets the returned metadata.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="788c9-108">Zwrócone metadane są przechowywane w projekcie klienta jako plik. edmx.</span><span class="sxs-lookup"><span data-stu-id="788c9-108">The returned metadata is stored in the client project as an .edmx file.</span></span> <span data-ttu-id="788c9-109">Nie można otworzyć tego pliku edmx przy użyciu projektanta Entity Data Model, ponieważ nie ma on tego samego formatu pliku. edmx, który jest używany przez Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="788c9-109">This .edmx file cannot be opened by using the Entity Data Model designer because it does not have the same format an .edmx file used by the Entity Framework.</span></span> <span data-ttu-id="788c9-110">Ten plik metadanych można wyświetlić za pomocą edytora XML lub dowolnego edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="788c9-110">You can view this metadata file by using the XML editor or any text editor.</span></span> <span data-ttu-id="788c9-111">Aby uzyskać więcej informacji, zobacz [ \[MC-edmx\]: Entity Data Model specyfikacji formatu](https://go.microsoft.com/fwlink/?LinkID=178833) pakowania Data Services</span><span class="sxs-lookup"><span data-stu-id="788c9-111">For more information, see the [\[MC-EDMX\]: Entity Data Model for Data Services Packaging Format](https://go.microsoft.com/fwlink/?LinkID=178833) specification</span></span>  
  
- <span data-ttu-id="788c9-112">Generuje reprezentację usługi jako klasę kontenera jednostek, która dziedziczy z <xref:System.Data.Services.Client.DataServiceContext>.</span><span class="sxs-lookup"><span data-stu-id="788c9-112">Generates a representation of the service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>.</span></span> <span data-ttu-id="788c9-113">Ta klasa kontenerów jednostek jest podobna do kontenera jednostek wygenerowanego przez narzędzia Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="788c9-113">This generated entity container class resembles the entity container that the Entity Data Model tools generate.</span></span> <span data-ttu-id="788c9-114">Aby uzyskać więcej informacji, zobacz temat [usługi obiektów — omówienie (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="788c9-114">For more information, see [Object Services Overview (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)).</span></span>  
  
- <span data-ttu-id="788c9-115">Generuje klasy danych dla typów modeli danych odnajdywanych w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="788c9-115">Generates data classes for the data model types that it discovers in the service metadata.</span></span>  
  
- <span data-ttu-id="788c9-116">Dodaje odwołanie do `System.Data.Services.Client` zestawu do projektu.</span><span class="sxs-lookup"><span data-stu-id="788c9-116">Adds a reference to the `System.Data.Services.Client` assembly to the project.</span></span>  
  
 <span data-ttu-id="788c9-117">Aby uzyskać więcej informacji, zobacz [jak: Dodaj odwołanie](how-to-add-a-data-service-reference-wcf-data-services.md)do usługi danych.</span><span class="sxs-lookup"><span data-stu-id="788c9-117">For more information, see [How to: Add a Data Service Reference](how-to-add-a-data-service-reference-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="788c9-118">Klasy usługi danych klienta mogą być również generowane za pomocą narzędzia [DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="788c9-118">The client data service classes can also be generated by using the [DataSvcUtil.exe](wcf-data-service-client-utility-datasvcutil-exe.md) tool at the command prompt.</span></span> <span data-ttu-id="788c9-119">Aby uzyskać więcej informacji, zobacz [jak: Generuj ręcznie klasy](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)usługi danych klienta.</span><span class="sxs-lookup"><span data-stu-id="788c9-119">For more information, see [How to: Manually Generate Client Data Service Classes](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).</span></span>  
  
## <a name="client-data-type-mapping"></a><span data-ttu-id="788c9-120">Mapowanie typu danych klienta</span><span class="sxs-lookup"><span data-stu-id="788c9-120">Client Data Type Mapping</span></span>  
 <span data-ttu-id="788c9-121">W przypadku korzystania z okna dialogowego **Dodaj odwołanie do usługi** w programie Visual Studio `DataSvcUtil.exe` lub narzędzia do generowania klas danych klienta, które [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] są oparte na źródle danych, typy danych .NET Framework są mapowane na typy pierwotne z modelu dane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="788c9-121">When you use the **Add Service Reference** dialog in Visual Studio or the `DataSvcUtil.exe` tool to generate client data classes that are based on an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed, the .NET Framework data types are mapped to the primitive types from the data model as follows:</span></span>  
  
|<span data-ttu-id="788c9-122">Typ modelu danych</span><span class="sxs-lookup"><span data-stu-id="788c9-122">Data model type</span></span>|<span data-ttu-id="788c9-123">Typ danych .NET Framework</span><span class="sxs-lookup"><span data-stu-id="788c9-123">.NET Framework data type</span></span>|  
|---------------------|------------------------------|  
|`Edm.Binary`|<span data-ttu-id="788c9-124"><xref:System.Byte>`[]`</span><span class="sxs-lookup"><span data-stu-id="788c9-124"><xref:System.Byte> `[]`</span></span>|  
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
  
 <span data-ttu-id="788c9-125">Aby uzyskać więcej informacji, [zobacz OData: Typy](https://go.microsoft.com/fwlink/?LinkId=186072)danych pierwotnych.</span><span class="sxs-lookup"><span data-stu-id="788c9-125">For more information, see [OData: Primitive Data Types](https://go.microsoft.com/fwlink/?LinkId=186072).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="788c9-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="788c9-126">See also</span></span>

- [<span data-ttu-id="788c9-127">Biblioteka klienta usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="788c9-127">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
- [<span data-ttu-id="788c9-128">Szybki start</span><span class="sxs-lookup"><span data-stu-id="788c9-128">Quickstart</span></span>](quickstart-wcf-data-services.md)

---
title: Definiowanie usług danych WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
ms.openlocfilehash: c0c9010a71877d2c9757a2c9cf2d5c1fec8aedf7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515540"
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="50ded-102">Definiowanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="50ded-102">Defining WCF Data Services</span></span>

<span data-ttu-id="50ded-103">W tej sekcji opisano sposób tworzenia i konfigurowania usług danych WCF, aby uwidocznić dane jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych.</span><span class="sxs-lookup"><span data-stu-id="50ded-103">This section describes how to create and configure WCF Data Services to expose data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="50ded-104">Aby uzyskać więcej informacji na temat podstawowych czynności wymagane do tworzenia usługi danych, zobacz [udostępnianie własnych danych jako usługa](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="50ded-104">For more information about the basic steps required to create a data service, see [Exposing Your Data as a Service](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="50ded-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="50ded-105">In This Section</span></span>

 [<span data-ttu-id="50ded-106">Konfigurowanie usługi danych</span><span class="sxs-lookup"><span data-stu-id="50ded-106">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)

 <span data-ttu-id="50ded-107">W tym artykule opisano opcje konfiguracji usługi danych, udostępniane przez usługi danych WCF.</span><span class="sxs-lookup"><span data-stu-id="50ded-107">Describes the data service configuration options provided by WCF Data Services.</span></span>

 [<span data-ttu-id="50ded-108">Dostawcy usług danych</span><span class="sxs-lookup"><span data-stu-id="50ded-108">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)

 <span data-ttu-id="50ded-109">W tym artykule opisano modele dostawcy do udostępniania danych jako usługę danych.</span><span class="sxs-lookup"><span data-stu-id="50ded-109">Describes the provider models for exposing data as a data service.</span></span>

 [<span data-ttu-id="50ded-110">Operacje usługi</span><span class="sxs-lookup"><span data-stu-id="50ded-110">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)

 <span data-ttu-id="50ded-111">W tym artykule opisano, jak zdefiniować operacje usług, które uwidaczniają metod na serwerze.</span><span class="sxs-lookup"><span data-stu-id="50ded-111">Describes how to define service operations that expose methods on the server.</span></span>

 [<span data-ttu-id="50ded-112">Dostosowywanie źródła</span><span class="sxs-lookup"><span data-stu-id="50ded-112">Feed Customization</span></span>](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)

 <span data-ttu-id="50ded-113">Opisuje sposób tworzenia mapowania między jednostkami w modelu danych zdefiniowane przez dostawcę usług danych i elementów strumieniowego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="50ded-113">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>

 [<span data-ttu-id="50ded-114">Interceptory</span><span class="sxs-lookup"><span data-stu-id="50ded-114">Interceptors</span></span>](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)

 <span data-ttu-id="50ded-115">W tym artykule opisano sposób definiowania metody interceptor do wykonania niestandardowej logiki biznesowej w żądaniach do usługi danych.</span><span class="sxs-lookup"><span data-stu-id="50ded-115">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>

 [<span data-ttu-id="50ded-116">Tworzenie i wdrażanie usług danych programu WCF</span><span class="sxs-lookup"><span data-stu-id="50ded-116">Developing and Deploying WCF Data Services</span></span>](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)

 <span data-ttu-id="50ded-117">Opisuje sposób tworzenia i wdrażania usługi danych przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="50ded-117">Describes how to develop and deploy a data service by using Visual Studio.</span></span>

 [<span data-ttu-id="50ded-118">Zabezpieczanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="50ded-118">Securing WCF Data Services</span></span>](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)

 <span data-ttu-id="50ded-119">W tym artykule opisano uwierzytelnianie i autoryzacja dla usługi danych i innych zagadnień dotyczących zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="50ded-119">Describes authentication and authorization for the data service and other security considerations.</span></span>

 [<span data-ttu-id="50ded-120">Hosting usługi danych</span><span class="sxs-lookup"><span data-stu-id="50ded-120">Hosting the Data Service</span></span>](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)

 <span data-ttu-id="50ded-121">Opisuje sposób wybierania hosta usługi danych.</span><span class="sxs-lookup"><span data-stu-id="50ded-121">Describes how to select a host for your data service.</span></span>

 [<span data-ttu-id="50ded-122">Przechowywanie wersji usługi danych</span><span class="sxs-lookup"><span data-stu-id="50ded-122">Data Service Versioning</span></span>](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)

 <span data-ttu-id="50ded-123">W tym artykule opisano sposób pracy z użyciem różnych wersji OData.</span><span class="sxs-lookup"><span data-stu-id="50ded-123">Describes how to work with different versions of the OData.</span></span>

 [<span data-ttu-id="50ded-124">Szczegóły implementacji protokołu usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="50ded-124">WCF Data Services Protocol Implementation Details</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-protocol-implementation-details.md)

 <span data-ttu-id="50ded-125">W tym artykule opisano opcjonalne funkcje protokołu OData, które nie są obecnie implementowane w usługach danych programu WCF.</span><span class="sxs-lookup"><span data-stu-id="50ded-125">Describes optional functionalities of the OData protocol that are not currently implemented by WCF Data Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="50ded-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50ded-126">See Also</span></span>

- [<span data-ttu-id="50ded-127">Biblioteka klienta usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="50ded-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [<span data-ttu-id="50ded-128">Uzyskiwanie dostępu do zasobów usługi danych</span><span class="sxs-lookup"><span data-stu-id="50ded-128">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
- [<span data-ttu-id="50ded-129">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="50ded-129">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

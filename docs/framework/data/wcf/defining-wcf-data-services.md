---
title: Definiowanie usług danych WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
ms.openlocfilehash: b9280936a16d50283c01120c9dc046e65a0a79ae
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790870"
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="8310a-102">Definiowanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="8310a-102">Defining WCF Data Services</span></span>

<span data-ttu-id="8310a-103">W tej sekcji opisano sposób tworzenia i konfigurowania usługi danych programu WCF w celu udostępnienia danych [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] jako źródła strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="8310a-103">This section describes how to create and configure WCF Data Services to expose data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> <span data-ttu-id="8310a-104">Aby uzyskać więcej informacji na temat podstawowych kroków wymaganych do utworzenia usługi danych, zobacz [udostępnianie danych jako usługi](exposing-your-data-as-a-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8310a-104">For more information about the basic steps required to create a data service, see [Exposing Your Data as a Service](exposing-your-data-as-a-service-wcf-data-services.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8310a-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="8310a-105">In This Section</span></span>

 [<span data-ttu-id="8310a-106">Konfigurowanie usługi danych</span><span class="sxs-lookup"><span data-stu-id="8310a-106">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)

 <span data-ttu-id="8310a-107">Opisuje opcje konfiguracji usługi danych udostępniane przez Usługi danych programu WCF.</span><span class="sxs-lookup"><span data-stu-id="8310a-107">Describes the data service configuration options provided by WCF Data Services.</span></span>

 [<span data-ttu-id="8310a-108">Dostawcy usług danych</span><span class="sxs-lookup"><span data-stu-id="8310a-108">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)

 <span data-ttu-id="8310a-109">Opisuje modele dostawców umożliwiające udostępnianie danych jako usługi danych.</span><span class="sxs-lookup"><span data-stu-id="8310a-109">Describes the provider models for exposing data as a data service.</span></span>

 [<span data-ttu-id="8310a-110">Operacje usługi</span><span class="sxs-lookup"><span data-stu-id="8310a-110">Service Operations</span></span>](service-operations-wcf-data-services.md)

 <span data-ttu-id="8310a-111">Opisuje sposób definiowania operacji usługi, które uwidaczniają metody na serwerze.</span><span class="sxs-lookup"><span data-stu-id="8310a-111">Describes how to define service operations that expose methods on the server.</span></span>

 [<span data-ttu-id="8310a-112">Dostosowywanie źródła</span><span class="sxs-lookup"><span data-stu-id="8310a-112">Feed Customization</span></span>](feed-customization-wcf-data-services.md)

 <span data-ttu-id="8310a-113">Opisuje sposób tworzenia mapowania między jednostkami w modelu danych zdefiniowanym przez dostawcę usługi danych i elementy w strumieniowym źródle danych.</span><span class="sxs-lookup"><span data-stu-id="8310a-113">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>

 [<span data-ttu-id="8310a-114">Interceptory</span><span class="sxs-lookup"><span data-stu-id="8310a-114">Interceptors</span></span>](interceptors-wcf-data-services.md)

 <span data-ttu-id="8310a-115">Opisuje sposób definiowania metod przechwytywania w celu wykonywania niestandardowej logiki biznesowej w przypadku żądań do usługi danych.</span><span class="sxs-lookup"><span data-stu-id="8310a-115">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>

 [<span data-ttu-id="8310a-116">Tworzenie i wdrażanie usług danych programu WCF</span><span class="sxs-lookup"><span data-stu-id="8310a-116">Developing and Deploying WCF Data Services</span></span>](developing-and-deploying-wcf-data-services.md)

 <span data-ttu-id="8310a-117">Opisuje sposób tworzenia i wdrażania usługi danych przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8310a-117">Describes how to develop and deploy a data service by using Visual Studio.</span></span>

 [<span data-ttu-id="8310a-118">Zabezpieczanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="8310a-118">Securing WCF Data Services</span></span>](securing-wcf-data-services.md)

 <span data-ttu-id="8310a-119">Opisuje uwierzytelnianie i autoryzację usługi danych oraz inne zagadnienia dotyczące zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="8310a-119">Describes authentication and authorization for the data service and other security considerations.</span></span>

 [<span data-ttu-id="8310a-120">Hosting usługi danych</span><span class="sxs-lookup"><span data-stu-id="8310a-120">Hosting the Data Service</span></span>](hosting-the-data-service-wcf-data-services.md)

 <span data-ttu-id="8310a-121">Opisuje sposób wybierania hosta dla usługi danych.</span><span class="sxs-lookup"><span data-stu-id="8310a-121">Describes how to select a host for your data service.</span></span>

 [<span data-ttu-id="8310a-122">Przechowywanie wersji usługi danych</span><span class="sxs-lookup"><span data-stu-id="8310a-122">Data Service Versioning</span></span>](data-service-versioning-wcf-data-services.md)

 <span data-ttu-id="8310a-123">Opisuje sposób pracy z różnymi wersjami protokołu OData.</span><span class="sxs-lookup"><span data-stu-id="8310a-123">Describes how to work with different versions of the OData.</span></span>

 [<span data-ttu-id="8310a-124">Szczegóły implementacji protokołu usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="8310a-124">WCF Data Services Protocol Implementation Details</span></span>](wcf-data-services-protocol-implementation-details.md)

 <span data-ttu-id="8310a-125">Opisuje opcjonalne funkcje protokołu OData, które nie są obecnie zaimplementowane przez Usługi danych programu WCF.</span><span class="sxs-lookup"><span data-stu-id="8310a-125">Describes optional functionalities of the OData protocol that are not currently implemented by WCF Data Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="8310a-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8310a-126">See also</span></span>

- [<span data-ttu-id="8310a-127">Biblioteka klienta usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="8310a-127">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
- [<span data-ttu-id="8310a-128">Uzyskiwanie dostępu do zasobów usługi danych</span><span class="sxs-lookup"><span data-stu-id="8310a-128">Accessing Data Service Resources</span></span>](accessing-data-service-resources-wcf-data-services.md)
- [<span data-ttu-id="8310a-129">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="8310a-129">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

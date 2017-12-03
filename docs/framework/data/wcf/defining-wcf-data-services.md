---
title: "Definiowanie usługi danych WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 05006ff3-02dc-410e-831e-54ec3e7e24ef
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e66c26c12f3f62ee61e02e16318e747793ff927
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="defining-wcf-data-services"></a><span data-ttu-id="d5599-102">Definiowanie usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="d5599-102">Defining WCF Data Services</span></span>
<span data-ttu-id="d5599-103">W tej sekcji opisano sposób tworzenia i konfigurowania [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] do udostępniania danych jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych.</span><span class="sxs-lookup"><span data-stu-id="d5599-103">This section describes how to create and configure [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to expose data as an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d5599-104">podstawowe kroki wymagane do utworzenia usługi danych, zobacz [udostępnianie danych jako usługa](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d5599-104"> the basic steps required to create a data service, see [Exposing Your Data as a Service](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5599-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d5599-105">In This Section</span></span>  
 [<span data-ttu-id="d5599-106">Konfigurowanie usługi danych</span><span class="sxs-lookup"><span data-stu-id="d5599-106">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="d5599-107">Zawiera opis opcji konfiguracji usługi danych dostarczanych przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5599-107">Describes the data service configuration options provided by [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span>  
  
 [<span data-ttu-id="d5599-108">Dostawców usług danych</span><span class="sxs-lookup"><span data-stu-id="d5599-108">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 <span data-ttu-id="d5599-109">W tym artykule opisano modele dostawcy dla udostępnianie danych jako usługa danych.</span><span class="sxs-lookup"><span data-stu-id="d5599-109">Describes the provider models for exposing data as a data service.</span></span>  
  
 [<span data-ttu-id="d5599-110">Operacje usługi</span><span class="sxs-lookup"><span data-stu-id="d5599-110">Service Operations</span></span>](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)  
 <span data-ttu-id="d5599-111">Opisuje sposób zdefiniowania operacji usługi, które udostępniają metody na serwerze.</span><span class="sxs-lookup"><span data-stu-id="d5599-111">Describes how to define service operations that expose methods on the server.</span></span>  
  
 [<span data-ttu-id="d5599-112">Dostosowywanie źródła</span><span class="sxs-lookup"><span data-stu-id="d5599-112">Feed Customization</span></span>](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)  
 <span data-ttu-id="d5599-113">Opisuje sposób tworzenia mapowania między jednostkami w modelu danych, wynika z dostawcy usług danych i elementów w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="d5599-113">Describes how to create a mapping between entities in the data model defined by the data service provider and elements in the data feed.</span></span>  
  
 [<span data-ttu-id="d5599-114">Interceptory</span><span class="sxs-lookup"><span data-stu-id="d5599-114">Interceptors</span></span>](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)  
 <span data-ttu-id="d5599-115">Opisuje sposób zdefiniowania metody interceptora wykonać niestandardowe reguły biznesowe na żądania usług danych.</span><span class="sxs-lookup"><span data-stu-id="d5599-115">Describes how to define interceptor methods to perform custom business logic on requests to the data service.</span></span>  
  
 [<span data-ttu-id="d5599-116">Tworzenie i wdrażanie usług danych WCF</span><span class="sxs-lookup"><span data-stu-id="d5599-116">Developing and Deploying WCF Data Services</span></span>](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)  
 <span data-ttu-id="d5599-117">Opisuje sposób tworzenia i wdrażania usługi danych przy użyciu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d5599-117">Describes how to develop and deploy a data service by using Visual Studio.</span></span>  
  
 [<span data-ttu-id="d5599-118">Zabezpieczanie usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="d5599-118">Securing WCF Data Services</span></span>](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 <span data-ttu-id="d5599-119">Opisuje, uwierzytelniania i autoryzacji dla usługi danych i innych zagadnień dotyczących zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d5599-119">Describes authentication and authorization for the data service and other security considerations.</span></span>  
  
 [<span data-ttu-id="d5599-120">Hosting usług danych</span><span class="sxs-lookup"><span data-stu-id="d5599-120">Hosting the Data Service</span></span>](../../../../docs/framework/data/wcf/hosting-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="d5599-121">Opisuje sposób wybierania hosta usługi danych.</span><span class="sxs-lookup"><span data-stu-id="d5599-121">Describes how to select a host for your data service.</span></span>  
  
 [<span data-ttu-id="d5599-122">Przechowywanie wersji usługi danych</span><span class="sxs-lookup"><span data-stu-id="d5599-122">Data Service Versioning</span></span>](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)  
 <span data-ttu-id="d5599-123">Opisuje sposób pracy z różnymi wersjami programu [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5599-123">Describes how to work with different versions of the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)].</span></span>  
  
 [<span data-ttu-id="d5599-124">Szczegóły implementacji protokołu usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="d5599-124">WCF Data Services Protocol Implementation Details</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-protocol-implementation-details.md)  
 <span data-ttu-id="d5599-125">W tym artykule opisano opcjonalne funkcje związane z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokołu, które nie są obecnie implementowane przez usługi danych WCF.</span><span class="sxs-lookup"><span data-stu-id="d5599-125">Describes optional functionalities of the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protocol that are not currently implemented by WCF Data Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5599-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5599-126">See Also</span></span>  
 [<span data-ttu-id="d5599-127">Biblioteka klienta usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="d5599-127">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [<span data-ttu-id="d5599-128">Podczas uzyskiwania dostępu do zasobów usługi danych</span><span class="sxs-lookup"><span data-stu-id="d5599-128">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)  
 [<span data-ttu-id="d5599-129">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="d5599-129">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)

---
title: "Model programowania protokołu HTTP sieci Web w programie WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web services programming model [WCF]
- POX
- REST
ms.assetid: 2312a8d3-b66e-4623-ba42-978434300c7f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 32e7cb3a340865530b6a8d76609eb246184363b0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-web-http-programming-model"></a><span data-ttu-id="3b580-102">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="3b580-102">WCF Web HTTP Programming Model</span></span>
<span data-ttu-id="3b580-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Modelu programowania protokołu HTTP sieci Web umożliwia deweloperom ujawnia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi operacje punktów końcowych z systemem innym niż SOAP.</span><span class="sxs-lookup"><span data-stu-id="3b580-103">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model allows developers to expose [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service operations to non-SOAP endpoints.</span></span> <span data-ttu-id="3b580-104">Tematy w tej sekcji Sprawdź, czy funkcja szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="3b580-104">The topics in this section examine the feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3b580-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3b580-105">In This Section</span></span>  
 [<span data-ttu-id="3b580-106">Omówienie modelu programowania protokołu HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="3b580-106">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 <span data-ttu-id="3b580-107">Zawiera omówienie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] modelu programowania protokołu HTTP sieci Web.</span><span class="sxs-lookup"><span data-stu-id="3b580-107">Provides an overview of the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model.</span></span>  
  
 [<span data-ttu-id="3b580-108">Model obiektowy programowania protokołu HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="3b580-108">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 <span data-ttu-id="3b580-109">W tym artykule omówiono [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] modelu programowania protokołu HTTP sieci Web i jej działania.</span><span class="sxs-lookup"><span data-stu-id="3b580-109">Discusses the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Web HTTP Programming Model and how it works.</span></span>  
  
 [<span data-ttu-id="3b580-110">Porady: Tworzenie usługi HTTP sieci Web WCF podstawowe</span><span class="sxs-lookup"><span data-stu-id="3b580-110">How to: Create a Basic WCF Web HTTP Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
 <span data-ttu-id="3b580-111">Opisuje sposób zapisania podstawowe usługi, która udostępnia punkt końcowy z systemem innym niż SOAP.</span><span class="sxs-lookup"><span data-stu-id="3b580-111">Describes how to write a basic service that exposes a non-SOAP endpoint.</span></span>  
  
 [<span data-ttu-id="3b580-112">Porady: ujawnianie kontraktu klientom sieci Web i SOAP</span><span class="sxs-lookup"><span data-stu-id="3b580-112">How to: Expose a Contract to SOAP and Web Clients</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md)  
 <span data-ttu-id="3b580-113">Opisuje sposób zapisania podstawowej usługi, który ujawnia ten sam kontrakt klientów z systemem innym niż SOAP i SOAP.</span><span class="sxs-lookup"><span data-stu-id="3b580-113">Describes how to write a basic service that exposes the same contract to both SOAP and non-SOAP clients.</span></span>  
  
 [<span data-ttu-id="3b580-114">Obiekt UriTemplate i UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="3b580-114">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 <span data-ttu-id="3b580-115">Zawiera opis sposobu kontrolowania identyfikatory URI, używając <xref:System.UriTemplate> i <xref:System.UriTemplateTable>.</span><span class="sxs-lookup"><span data-stu-id="3b580-115">Describes how to control URIs using <xref:System.UriTemplate> and <xref:System.UriTemplateTable>.</span></span>  
  
 [<span data-ttu-id="3b580-116">Obsługa buforowania dla usług HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="3b580-116">Caching Support for WCF Web HTTP Services</span></span>](../../../../docs/framework/wcf/feature-details/caching-support-for-wcf-web-http-services.md)  
 <span data-ttu-id="3b580-117">Opisuje sposób określenia zachowanie buforowania dla usługi WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="3b580-117">Describes how to specify caching behavior for a WCF Web HTTP service.</span></span>  
  
 [<span data-ttu-id="3b580-118">Formatowanie kodu HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="3b580-118">WCF Web HTTP Formatting</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 <span data-ttu-id="3b580-119">Opisuje sposób określenia format odpowiedzi z usługi WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="3b580-119">Describes how to specify the format of the response from a WCF Web HTTP service.</span></span>  
  
 [<span data-ttu-id="3b580-120">Obsługa błędów protokołu HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="3b580-120">WCF Web HTTP Error Handling</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-error-handling.md)  
 <span data-ttu-id="3b580-121">Opisuje sposób zwracania błędów klientów sieci Web WCF, w tym dane o błędach zdefiniowane przez użytkownika dodatkowe i kodów stanu HTTP.</span><span class="sxs-lookup"><span data-stu-id="3b580-121">Describes how to return errors to WCF Web clients including HTTP status codes and additional user-defined error data.</span></span>  
  
 [<span data-ttu-id="3b580-122">Wywoływanie usługi typu REST z usługą WCF</span><span class="sxs-lookup"><span data-stu-id="3b580-122">Calling a REST-style service from a WCF service</span></span>](../../../../docs/framework/wcf/feature-details/calling-a-rest-style-service-from-a-wcf-service.md)  
 <span data-ttu-id="3b580-123">Zawiera opis sposobu wywoływania usługi typu REST z wewnątrz usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="3b580-123">Describes how to call a REST-style service from inside a WCF service.</span></span>

---
title: "Rozszerzanie elementu ServiceHost i warstwy modelu usług"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1a1a439735375d96bee2d09f13d50e43783df964
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="extending-servicehost-and-the-service-model-layer"></a><span data-ttu-id="388a0-102">Rozszerzanie elementu ServiceHost i warstwy modelu usług</span><span class="sxs-lookup"><span data-stu-id="388a0-102">Extending ServiceHost and the Service Model Layer</span></span>
<span data-ttu-id="388a0-103">Warstwy modelu usług jest odpowiedzialny za ściąganie wiadomości przychodzących poza podstawowej kanały, tłumaczenia je do wywołania metody w kodzie aplikacji i wysłaniem wyniki z powrotem do wywołującego.</span><span class="sxs-lookup"><span data-stu-id="388a0-103">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span> <span data-ttu-id="388a0-104">Rozszerzenia modelu usługi zmodyfikować, lub zaimplementuj wykonywania lub zachowanie komunikacji i funkcje dotyczące klienta lub dyspozytora funkcje, niestandardowe zachowania, wiadomości i przechwytywaniu parametru i innych funkcji rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="388a0-104">Service model extensions modify or implement execution or communication behavior and features involving client or dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="388a0-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="388a0-105">In This Section</span></span>  
 [<span data-ttu-id="388a0-106">Rozszerzanie klientów</span><span class="sxs-lookup"><span data-stu-id="388a0-106">Extending Clients</span></span>](../../../../docs/framework/wcf/extending/extending-clients.md)  
 <span data-ttu-id="388a0-107">Opisuje interfejsy, które mogą przechwytywać i zmodyfikować środowiska uruchomieniowego klienta, a także klasy, do których można wstawić niestandardowych rozszerzeń w aplikacjach klienckich.</span><span class="sxs-lookup"><span data-stu-id="388a0-107">Describes the interfaces that can intercept and modify the client runtime, as well as the classes into which you can insert your custom extensions in client applications.</span></span> <span data-ttu-id="388a0-108">Na przykład można wykonywać rejestrowanie komunikatów niestandardowego klienta, wykonywania serializacji niestandardowy komunikat i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="388a0-108">For example, you can perform custom client message logging, perform custom message serialization, and so on.</span></span>  
  
 [<span data-ttu-id="388a0-109">Rozszerzanie dyspozytorów</span><span class="sxs-lookup"><span data-stu-id="388a0-109">Extending Dispatchers</span></span>](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 <span data-ttu-id="388a0-110">Opisuje interfejsy, które mogą przechwytywać i zmodyfikować środowiska uruchomieniowego usługi, a także klasy, do których można wstawić niestandardowych rozszerzeń w aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="388a0-110">Describes the interfaces that can intercept and modify the service runtime, as well as the classes into which you can insert your custom extensions in service applications.</span></span> <span data-ttu-id="388a0-111">Na przykład można wykonać rejestrowania usług niestandardowych, sprawdzanie poprawności komunikatu po stronie usługi, wysyłania niestandardowych i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="388a0-111">For example, you can perform custom service logging, service-side message validation, custom dispatching, and so on.</span></span>  
  
 [<span data-ttu-id="388a0-112">Obiekty rozszerzalne</span><span class="sxs-lookup"><span data-stu-id="388a0-112">Extensible Objects</span></span>](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 <span data-ttu-id="388a0-113">W tym artykule opisano pięć obiekty rozszerzalne i <xref:System.ServiceModel.IExtensibleObject%601> wzorca.</span><span class="sxs-lookup"><span data-stu-id="388a0-113">Describes the five extensible objects and the <xref:System.ServiceModel.IExtensibleObject%601> pattern.</span></span> <span data-ttu-id="388a0-114">Wzorzec rozszerzonego obiektu jest używany, aby wydłużyć istniejące klasy środowiska uruchomieniowego z nowych funkcji lub aby dodać nowy stan do obiektu.</span><span class="sxs-lookup"><span data-stu-id="388a0-114">The extensible object pattern is used to either extend existing runtime classes with new functionality or to add new state to an object.</span></span> <span data-ttu-id="388a0-115">Dołączony do jednego z obiekty rozszerzalne, dzięki rozszerzeniom zachowania w bardzo różnych etapach przetwarzania dostęp do stanu udostępnionego i dołączony do obiektu extensible wspólnej mogą uzyskiwać dostęp do funkcji.</span><span class="sxs-lookup"><span data-stu-id="388a0-115">Extensions, attached to one of the extensible objects, enable behaviors at very different stages in processing to access shared state and functionality attached to a common extensible object that they can access.</span></span>  
  
 [<span data-ttu-id="388a0-116">Konfigurowanie i rozszerzanie środowiska uruchomieniowego za pomocą zachowań</span><span class="sxs-lookup"><span data-stu-id="388a0-116">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 <span data-ttu-id="388a0-117">Aby zmienić ustawienia lub Wstaw rozszerzenia w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] środowiska uruchomieniowego, użyj zachowania.</span><span class="sxs-lookup"><span data-stu-id="388a0-117">To change settings on or insert extensions in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime, you use Behaviors.</span></span> <span data-ttu-id="388a0-118">Usługi WCF zawiera zachowania zaimplementowana system kontroli przepustowości, wystąpień i wiele innych aspektów operacji dotyczących usług i.</span><span class="sxs-lookup"><span data-stu-id="388a0-118">WCF includes system-implemented behaviors for controlling throttling, instancing, and many other aspects of services and operations.</span></span> <span data-ttu-id="388a0-119">W tej sekcji opisano sposób tworzenia niestandardowych zachowania i porady były dostępne do użycia zarówno programowo i za pomocą plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="388a0-119">This section describes how to create your own custom behaviors and how to make them available for use both programmatically and using configuration files.</span></span>  
  
 [<span data-ttu-id="388a0-120">Rozszerzanie hostingu za pomocą elementu ServiceHostFactory</span><span class="sxs-lookup"><span data-stu-id="388a0-120">Extending Hosting Using ServiceHostFactory</span></span>](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 <span data-ttu-id="388a0-121">Opisuje sposób rozszerzyć <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>i użyj <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> klas, aby dostosować środowisku hosta.</span><span class="sxs-lookup"><span data-stu-id="388a0-121">Describes how to extend <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, and use the <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> classes to customize the host environment.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="388a0-122">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="388a0-122">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="388a0-123">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="388a0-123">Related Sections</span></span>

---
title: <behavior> dla <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: 489678a5adeae3965acae90a847c4b087478354d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140811"
---
# <a name="behavior-of-endpointbehaviors"></a><span data-ttu-id="be09c-102">\<behavior> dla \<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="be09c-102">\<behavior> of \<endpointBehaviors></span></span>
<span data-ttu-id="be09c-103">`behavior`Element zawiera kolekcję ustawień zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="be09c-103">The `behavior` element contains a collection of settings for the behavior of an endpoint.</span></span> <span data-ttu-id="be09c-104">Każde działanie jest indeksowane według jego `name`.</span><span class="sxs-lookup"><span data-stu-id="be09c-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="be09c-105">Punkty końcowe mogą łączyć się z każdym zachowaniem przy użyciu tej nazwy.</span><span class="sxs-lookup"><span data-stu-id="be09c-105">Endpoints can link to each behavior through this name.</span></span> <span data-ttu-id="be09c-106">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="be09c-106">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="be09c-107">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="be09c-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="be09c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="be09c-108">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="String" />
    </endpointBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be09c-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="be09c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="be09c-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="be09c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be09c-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="be09c-111">Attributes</span></span>  
  
|<span data-ttu-id="be09c-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="be09c-112">Attribute</span></span>|<span data-ttu-id="be09c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="be09c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="be09c-114">name</span><span class="sxs-lookup"><span data-stu-id="be09c-114">name</span></span>|<span data-ttu-id="be09c-115">Unikatowy ciąg, który zawiera nazwę konfiguracji zachowanie.</span><span class="sxs-lookup"><span data-stu-id="be09c-115">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="be09c-116">Ta wartość jest ciągiem zdefiniowanej przez użytkownika, który musi być unikatowy, ponieważ działa jako ciąg identyfikacyjny dla elementu.</span><span class="sxs-lookup"><span data-stu-id="be09c-116">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="be09c-117">Począwszy od .NET Framework 4, powiązania i zachowania nie muszą mieć nazwy.</span><span class="sxs-lookup"><span data-stu-id="be09c-117">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="be09c-118">Aby uzyskać więcej informacji na temat konfiguracji domyślnej i powiązań pustego i zachowań, zobacz [Uproszczona konfiguracja](../../../wcf/simplified-configuration.md) i [Uproszczona konfiguracja dla usług WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="be09c-118">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be09c-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="be09c-119">Child Elements</span></span>  
  
|<span data-ttu-id="be09c-120">Element</span><span class="sxs-lookup"><span data-stu-id="be09c-120">Element</span></span>|<span data-ttu-id="be09c-121">Opis</span><span class="sxs-lookup"><span data-stu-id="be09c-121">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="be09c-122">Określa poświadczenia używane do uwierzytelniania klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="be09c-122">Specifies the credentials used to authenticate the client to a service.</span></span>|  
|[\<callbackDebug>](callbackdebug.md)|<span data-ttu-id="be09c-123">Określa debugowanie usługi dla obiektu wywołania zwrotnego Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="be09c-123">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>|  
|[\<callbackTimeouts>](callbacktimeouts.md)|<span data-ttu-id="be09c-124">Określa limit czasu dla wywołania zwrotnego klienta.</span><span class="sxs-lookup"><span data-stu-id="be09c-124">Specifies the timeout for the client callback.</span></span>|  
|[\<clientVia>](clientvia.md)|<span data-ttu-id="be09c-125">Określa trasę, którą powinien wykonać wiadomość.</span><span class="sxs-lookup"><span data-stu-id="be09c-125">Specifies the route a message should take.</span></span>|  
|[\<dataContractSerializer>](datacontractserializer.md)|<span data-ttu-id="be09c-126">Zawiera dane konfiguracyjne dla elementu DataContractSerializer.</span><span class="sxs-lookup"><span data-stu-id="be09c-126">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<dispatcherSynchronization>](dispatchersynchronization.md)|<span data-ttu-id="be09c-127">Określa zachowanie punktu końcowego, które umożliwia usłudze wysyłanie odpowiedzi asynchronicznie.</span><span class="sxs-lookup"><span data-stu-id="be09c-127">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>|  
|[\<enableWebScript>](enablewebscript.md)|<span data-ttu-id="be09c-128">Włącza zachowanie punktu końcowego, który umożliwia korzystanie z usługi z ASP.NET AJAX stron sieci Web.</span><span class="sxs-lookup"><span data-stu-id="be09c-128">Enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span> <span data-ttu-id="be09c-129">Zachowanie powinno być używane tylko w połączeniu ze \<webHttpBinding> standardowym powiązaniem lub \<webMessageEncoding> elementem powiązania.</span><span class="sxs-lookup"><span data-stu-id="be09c-129">The behavior should only be used in conjunction with either the \<webHttpBinding> standard binding, or the \<webMessageEncoding> binding element.</span></span>|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="be09c-130">Określa różne ustawienia odnajdywania dla punktu końcowego, takie jak jego wykrywalność, zakresy i wszelkie niestandardowe rozszerzenia do swoich metadanych.</span><span class="sxs-lookup"><span data-stu-id="be09c-130">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
|[\<soapProcessing>](soapprocessing.md)|<span data-ttu-id="be09c-131">Definiuje zachowanie punktu końcowego klienta używane do organizowania komunikatów między różnymi typami powiązań i wersjami komunikatów.</span><span class="sxs-lookup"><span data-stu-id="be09c-131">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>|  
|[\<synchronousReceive>](synchronousreceive-element.md)|<span data-ttu-id="be09c-132">Określa zachowanie w czasie wykonywania w przypadku otrzymywania wiadomości w usłudze lub aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="be09c-132">Specifies run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="be09c-133">Nie ma żadnych atrybutów ani elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="be09c-133">It does not have any attributes or child elements.</span></span>|  
|[\<transactedBatching>](transactedbatching.md)|<span data-ttu-id="be09c-134">Określa, czy przetwarzanie wsadowe transakcji jest obsługiwane dla operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="be09c-134">Specifies whether transaction batching is supported for receive operations.</span></span>|  
|[\<webHttp>](webhttp.md)|<span data-ttu-id="be09c-135">Określa WebHttpBehavior w punkcie końcowym za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="be09c-135">Specifies the WebHttpBehavior on an endpoint through configuration.</span></span> <span data-ttu-id="be09c-136">Takie zachowanie, gdy jest używane w połączeniu ze \<webHttpBinding> standardowym powiązaniem, umożliwia model programowania sieci Web dla usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="be09c-136">This behavior, when used in conjunction with the \<webHttpBinding> standard binding, enables the Web programming model for a WCF service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="be09c-137">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="be09c-137">Parent Elements</span></span>  
  
|<span data-ttu-id="be09c-138">Element</span><span class="sxs-lookup"><span data-stu-id="be09c-138">Element</span></span>|<span data-ttu-id="be09c-139">Opis</span><span class="sxs-lookup"><span data-stu-id="be09c-139">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="be09c-140">Kolekcja elementów zachowania punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="be09c-140">A collection of endpoint behavior elements.</span></span>|

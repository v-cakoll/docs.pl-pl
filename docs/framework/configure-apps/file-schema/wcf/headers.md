---
title: "&lt;nagłówki&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d5e0a56055df588e9e42c4e1855c352c3f0d1b2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltheadersgt"></a><span data-ttu-id="9925d-102">&lt;nagłówki&gt;</span><span class="sxs-lookup"><span data-stu-id="9925d-102">&lt;headers&gt;</span></span>
<span data-ttu-id="9925d-103">Punkt końcowy może zostać zlikwidowane przez co najmniej jeden nagłówek SOAP oprócz jego podstawowego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="9925d-103">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="9925d-104">Jeden zestaw scenariuszy, w których jest to przydatne to zestaw SOAP scenariuszy pośredniczącego w przypadku gdy punkt końcowy wymaga klientom tego punktu końcowego obejmują celem pośredników nagłówki SOAP.</span><span class="sxs-lookup"><span data-stu-id="9925d-104">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="9925d-105">Ten element konfiguracji może służyć do definiowania takie nagłówki niestandardowy adres.</span><span class="sxs-lookup"><span data-stu-id="9925d-105">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="9925d-106">Wpisy w kolekcji nagłówka punktu końcowego są zdefiniowane przez użytkownika elementy XML.</span><span class="sxs-lookup"><span data-stu-id="9925d-106">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="9925d-107">Każdy element ma być poprawnie sformułowanym XML.</span><span class="sxs-lookup"><span data-stu-id="9925d-107">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="9925d-108">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="9925d-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="9925d-109">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="9925d-109">\<client></span></span>  
<span data-ttu-id="9925d-110">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="9925d-110">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9925d-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="9925d-111">Syntax</span></span>  
  
```xml  
<headers>  
    <Region xmlns="Uri">"String"</Region>  
        <Member xmlns="Uri">"String"</Member>  
</headers>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9925d-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9925d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9925d-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9925d-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9925d-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9925d-114">Attributes</span></span>  
 <span data-ttu-id="9925d-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="9925d-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9925d-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9925d-116">Child Elements</span></span>  
  
|<span data-ttu-id="9925d-117">Element</span><span class="sxs-lookup"><span data-stu-id="9925d-117">Element</span></span>|<span data-ttu-id="9925d-118">Opis</span><span class="sxs-lookup"><span data-stu-id="9925d-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9925d-119">Region</span><span class="sxs-lookup"><span data-stu-id="9925d-119">Region</span></span>||  
|<span data-ttu-id="9925d-120">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="9925d-120">Member</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="9925d-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9925d-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9925d-122">Element</span><span class="sxs-lookup"><span data-stu-id="9925d-122">Element</span></span>|<span data-ttu-id="9925d-123">Opis</span><span class="sxs-lookup"><span data-stu-id="9925d-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9925d-124">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="9925d-124">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="9925d-125">Umożliwia skonfigurowanie różnych typów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="9925d-125">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9925d-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9925d-126">Remarks</span></span>  
 <span data-ttu-id="9925d-127">Opcjonalne nagłówki zawierają bardziej szczegółowe informacje adresowania do identyfikacji użytkownika lub interakcji z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="9925d-127">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="9925d-128">Na przykład nagłówków można wskazać sposobu przetwarzania wiadomości przychodzących, gdzie wysłać komunikat odpowiedzi punktu końcowego lub które wystąpienie usługi do przetwarzania komunikat przychodzący z konkretnego użytkownika, jeśli dostępnych jest wiele wystąpień.</span><span class="sxs-lookup"><span data-stu-id="9925d-128">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9925d-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9925d-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [<span data-ttu-id="9925d-130">Punkty końcowe: Adresy powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="9925d-130">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)

---
title: '&lt;Nagłówki&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 84b9a9437d4b0dfae72a6e625b21f2b830eb28d8
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147866"
---
# <a name="ltheadersgt"></a><span data-ttu-id="51873-102">&lt;Nagłówki&gt;</span><span class="sxs-lookup"><span data-stu-id="51873-102">&lt;headers&gt;</span></span>
<span data-ttu-id="51873-103">Punkt końcowy może zostać zlikwidowane przez jeden lub więcej nagłówków protokołu SOAP, oprócz jego podstawowego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="51873-103">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="51873-104">Jeden zestaw scenariuszy, w których jest to przydatne to zestaw scenariuszy pośrednie protokołu SOAP, gdzie punktu końcowego wymaga od klientów zawiera nagłówków protokołu SOAP, przeznaczona dla pośredników tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="51873-104">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="51873-105">Ten element konfiguracji, może służyć do definiowania takich Nagłówki niestandardowe adresów.</span><span class="sxs-lookup"><span data-stu-id="51873-105">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="51873-106">Wpisy w kolekcję nagłówków punktu końcowego są zdefiniowane przez użytkownika elementy XML.</span><span class="sxs-lookup"><span data-stu-id="51873-106">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="51873-107">Każdy element musi być poprawnie sformułowany XML.</span><span class="sxs-lookup"><span data-stu-id="51873-107">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="51873-108">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="51873-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="51873-109">\<Klient ></span><span class="sxs-lookup"><span data-stu-id="51873-109">\<client></span></span>  
<span data-ttu-id="51873-110">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="51873-110">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51873-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="51873-111">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="51873-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="51873-112">Attributes and Elements</span></span>  
 <span data-ttu-id="51873-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="51873-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="51873-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="51873-114">Attributes</span></span>  
 <span data-ttu-id="51873-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="51873-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="51873-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="51873-116">Child Elements</span></span>  
  
|<span data-ttu-id="51873-117">Element</span><span class="sxs-lookup"><span data-stu-id="51873-117">Element</span></span>|<span data-ttu-id="51873-118">Opis</span><span class="sxs-lookup"><span data-stu-id="51873-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="51873-119">Region</span><span class="sxs-lookup"><span data-stu-id="51873-119">Region</span></span>||  
|<span data-ttu-id="51873-120">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="51873-120">Member</span></span>||  
  
### <a name="parent-elements"></a><span data-ttu-id="51873-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="51873-121">Parent Elements</span></span>  
  
|<span data-ttu-id="51873-122">Element</span><span class="sxs-lookup"><span data-stu-id="51873-122">Element</span></span>|<span data-ttu-id="51873-123">Opis</span><span class="sxs-lookup"><span data-stu-id="51873-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="51873-124">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="51873-124">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="51873-125">Służy do konfigurowania różnych typów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="51873-125">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51873-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51873-126">Remarks</span></span>  
 <span data-ttu-id="51873-127">Opcjonalne nagłówki zawierają więcej szczegółowych informacji adresowania, aby zidentyfikować lub nawiązać kontakt z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="51873-127">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="51873-128">Na przykład nagłówków, można wskazać sposób przetwarzania wiadomości przychodzących, gdzie wysłać komunikat odpowiedzi punktu końcowego lub które wystąpienie usługi do przetwarzania wiadomości przychodzących konkretnego użytkownika, jeśli wiele wystąpień są dostępne.</span><span class="sxs-lookup"><span data-stu-id="51873-128">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51873-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51873-129">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [<span data-ttu-id="51873-130">Punkty końcowe: Adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="51873-130">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)

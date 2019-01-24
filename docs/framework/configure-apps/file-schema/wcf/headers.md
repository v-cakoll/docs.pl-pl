---
title: '&lt;headers&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: f47462ba63b9bd8868420ee9d3a320ba18c83c65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54557828"
---
# <a name="ltheadersgt"></a><span data-ttu-id="98f7f-102">&lt;headers&gt;</span><span class="sxs-lookup"><span data-stu-id="98f7f-102">&lt;headers&gt;</span></span>
<span data-ttu-id="98f7f-103">Punkt końcowy może zostać zlikwidowane przez jeden lub więcej nagłówków protokołu SOAP, oprócz jego podstawowego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="98f7f-103">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="98f7f-104">Jeden zestaw scenariuszy, w których jest to przydatne to zestaw scenariuszy pośrednie protokołu SOAP, gdzie punktu końcowego wymaga od klientów zawiera nagłówków protokołu SOAP, przeznaczona dla pośredników tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="98f7f-104">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="98f7f-105">Ten element konfiguracji, może służyć do definiowania takich Nagłówki niestandardowe adresów.</span><span class="sxs-lookup"><span data-stu-id="98f7f-105">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="98f7f-106">Wpisy w kolekcję nagłówków punktu końcowego są zdefiniowane przez użytkownika elementy XML.</span><span class="sxs-lookup"><span data-stu-id="98f7f-106">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="98f7f-107">Każdy element musi być poprawnie sformułowany XML.</span><span class="sxs-lookup"><span data-stu-id="98f7f-107">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="98f7f-108">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="98f7f-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="98f7f-109">\<client></span><span class="sxs-lookup"><span data-stu-id="98f7f-109">\<client></span></span>  
<span data-ttu-id="98f7f-110">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="98f7f-110">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98f7f-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="98f7f-111">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98f7f-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="98f7f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="98f7f-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="98f7f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98f7f-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="98f7f-114">Attributes</span></span>  
 <span data-ttu-id="98f7f-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="98f7f-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="98f7f-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="98f7f-116">Child Elements</span></span>  
 <span data-ttu-id="98f7f-117">Zdefiniowane przez użytkownika elementy XML.</span><span class="sxs-lookup"><span data-stu-id="98f7f-117">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98f7f-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="98f7f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="98f7f-119">Element</span><span class="sxs-lookup"><span data-stu-id="98f7f-119">Element</span></span>|<span data-ttu-id="98f7f-120">Opis</span><span class="sxs-lookup"><span data-stu-id="98f7f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98f7f-121">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="98f7f-121">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="98f7f-122">Służy do konfigurowania różnych typów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="98f7f-122">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98f7f-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="98f7f-123">Remarks</span></span>  
 <span data-ttu-id="98f7f-124">Opcjonalne nagłówki zawierają więcej szczegółowych informacji adresowania, aby zidentyfikować lub nawiązać kontakt z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="98f7f-124">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="98f7f-125">Na przykład nagłówków, można wskazać sposób przetwarzania wiadomości przychodzących, gdzie wysłać komunikat odpowiedzi punktu końcowego lub które wystąpienie usługi do przetwarzania wiadomości przychodzących konkretnego użytkownika, jeśli wiele wystąpień są dostępne.</span><span class="sxs-lookup"><span data-stu-id="98f7f-125">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98f7f-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98f7f-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="98f7f-127">Punkty końcowe: Adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="98f7f-127">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)

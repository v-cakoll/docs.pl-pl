---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 660497012dd057e4ecf95524833e2573fe03a8b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670680"
---
# <a name="headers"></a><span data-ttu-id="70dd2-101">\<headers></span><span class="sxs-lookup"><span data-stu-id="70dd2-101">\<headers></span></span>
<span data-ttu-id="70dd2-102">Punkt końcowy może zostać zlikwidowane przez jeden lub więcej nagłówków protokołu SOAP, oprócz jego podstawowego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="70dd2-102">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="70dd2-103">Jeden zestaw scenariuszy, w których jest to przydatne to zestaw scenariuszy pośrednie protokołu SOAP, gdzie punktu końcowego wymaga od klientów zawiera nagłówków protokołu SOAP, przeznaczona dla pośredników tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="70dd2-103">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="70dd2-104">Ten element konfiguracji, może służyć do definiowania takich Nagłówki niestandardowe adresów.</span><span class="sxs-lookup"><span data-stu-id="70dd2-104">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="70dd2-105">Wpisy w kolekcję nagłówków punktu końcowego są zdefiniowane przez użytkownika elementy XML.</span><span class="sxs-lookup"><span data-stu-id="70dd2-105">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="70dd2-106">Każdy element musi być poprawnie sformułowany XML.</span><span class="sxs-lookup"><span data-stu-id="70dd2-106">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="70dd2-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="70dd2-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="70dd2-108">\<client></span><span class="sxs-lookup"><span data-stu-id="70dd2-108">\<client></span></span>  
<span data-ttu-id="70dd2-109">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="70dd2-109">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70dd2-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="70dd2-110">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70dd2-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="70dd2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="70dd2-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="70dd2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70dd2-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="70dd2-113">Attributes</span></span>  
 <span data-ttu-id="70dd2-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="70dd2-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="70dd2-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="70dd2-115">Child Elements</span></span>  
 <span data-ttu-id="70dd2-116">Zdefiniowane przez użytkownika elementy XML.</span><span class="sxs-lookup"><span data-stu-id="70dd2-116">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70dd2-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="70dd2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="70dd2-118">Element</span><span class="sxs-lookup"><span data-stu-id="70dd2-118">Element</span></span>|<span data-ttu-id="70dd2-119">Opis</span><span class="sxs-lookup"><span data-stu-id="70dd2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70dd2-120">\<punkt końcowy ></span><span class="sxs-lookup"><span data-stu-id="70dd2-120">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|<span data-ttu-id="70dd2-121">Służy do konfigurowania różnych typów punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="70dd2-121">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70dd2-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="70dd2-122">Remarks</span></span>  
 <span data-ttu-id="70dd2-123">Opcjonalne nagłówki zawierają więcej szczegółowych informacji adresowania, aby zidentyfikować lub nawiązać kontakt z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="70dd2-123">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="70dd2-124">Na przykład nagłówków, można wskazać sposób przetwarzania wiadomości przychodzących, gdzie wysłać komunikat odpowiedzi punktu końcowego lub które wystąpienie usługi do przetwarzania wiadomości przychodzących konkretnego użytkownika, jeśli wiele wystąpień są dostępne.</span><span class="sxs-lookup"><span data-stu-id="70dd2-124">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70dd2-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70dd2-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="70dd2-126">Punkty końcowe: Adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="70dd2-126">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)

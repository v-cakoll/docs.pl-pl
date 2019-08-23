---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: a982fa87ab84725e36ee913f00200cd34f0b8f6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925577"
---
# <a name="headers"></a><span data-ttu-id="b54de-101">\<headers></span><span class="sxs-lookup"><span data-stu-id="b54de-101">\<headers></span></span>
<span data-ttu-id="b54de-102">Punkt końcowy może być rozkierowany przy użyciu co najmniej jednego nagłówka SOAP oprócz podstawowego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="b54de-102">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="b54de-103">Jednym z zestawów scenariuszy, w których jest to przydatne, jest zestaw scenariuszy pośrednich protokołu SOAP, w których punkt końcowy wymaga od klientów tego punktu końcowego dołączenia nagłówków protokołu SOAP przeznaczonych dla pośredników.</span><span class="sxs-lookup"><span data-stu-id="b54de-103">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="b54de-104">Ten element konfiguracji może służyć do definiowania takich niestandardowych nagłówków adresów.</span><span class="sxs-lookup"><span data-stu-id="b54de-104">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="b54de-105">Wpisy w kolekcji nagłówka punktu końcowego są elementami XML zdefiniowanymi przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b54de-105">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="b54de-106">Każdy element musi być poprawnie sformułowanym plikiem XML.</span><span class="sxs-lookup"><span data-stu-id="b54de-106">Each element has to be well-formed XML.</span></span>  
  
 <span data-ttu-id="b54de-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b54de-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="b54de-108">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="b54de-108">\<client></span></span>  
<span data-ttu-id="b54de-109">\<> punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="b54de-109">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b54de-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="b54de-110">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b54de-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b54de-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b54de-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b54de-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b54de-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b54de-113">Attributes</span></span>  
 <span data-ttu-id="b54de-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="b54de-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b54de-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b54de-115">Child Elements</span></span>  
 <span data-ttu-id="b54de-116">Zdefiniowane przez użytkownika elementy XML.</span><span class="sxs-lookup"><span data-stu-id="b54de-116">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b54de-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b54de-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b54de-118">Element</span><span class="sxs-lookup"><span data-stu-id="b54de-118">Element</span></span>|<span data-ttu-id="b54de-119">Opis</span><span class="sxs-lookup"><span data-stu-id="b54de-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b54de-120">\<> punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="b54de-120">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="b54de-121">Konfiguruje różne typy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="b54de-121">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b54de-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b54de-122">Remarks</span></span>  
 <span data-ttu-id="b54de-123">Opcjonalne nagłówki zawierają bardziej szczegółowe informacje dotyczące adresowania, które identyfikują lub współpracują z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="b54de-123">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="b54de-124">Na przykład nagłówki mogą wskazywać, jak przetwarzać komunikat przychodzący, gdzie punkt końcowy powinien wysłać komunikat odpowiedzi lub którego wystąpienia usługi należy użyć do przetworzenia komunikatu przychodzącego od określonego użytkownika, gdy jest dostępnych wiele wystąpień.</span><span class="sxs-lookup"><span data-stu-id="b54de-124">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b54de-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b54de-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="b54de-126">Punktów końcowych Adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="b54de-126">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)

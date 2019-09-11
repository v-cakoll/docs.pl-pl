---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 76b3cbf6b867a983c203141bcd901b2b7b4038d5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855171"
---
# <a name="headers"></a><span data-ttu-id="96acd-101">\<headers></span><span class="sxs-lookup"><span data-stu-id="96acd-101">\<headers></span></span>
<span data-ttu-id="96acd-102">Punkt końcowy może być rozkierowany przy użyciu co najmniej jednego nagłówka SOAP oprócz podstawowego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="96acd-102">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="96acd-103">Jednym z zestawów scenariuszy, w których jest to przydatne, jest zestaw scenariuszy pośrednich protokołu SOAP, w których punkt końcowy wymaga od klientów tego punktu końcowego dołączenia nagłówków protokołu SOAP przeznaczonych dla pośredników.</span><span class="sxs-lookup"><span data-stu-id="96acd-103">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="96acd-104">Ten element konfiguracji może służyć do definiowania takich niestandardowych nagłówków adresów.</span><span class="sxs-lookup"><span data-stu-id="96acd-104">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="96acd-105">Wpisy w kolekcji nagłówka punktu końcowego są elementami XML zdefiniowanymi przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="96acd-105">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="96acd-106">Każdy element musi być poprawnie sformułowanym plikiem XML.</span><span class="sxs-lookup"><span data-stu-id="96acd-106">Each element has to be well-formed XML.</span></span>  
  
<span data-ttu-id="96acd-107">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="96acd-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="96acd-108">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="96acd-108">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="96acd-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="96acd-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="96acd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> punktu końcowego**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="96acd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="96acd-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<nagłówki >**</span><span class="sxs-lookup"><span data-stu-id="96acd-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<headers>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96acd-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="96acd-112">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96acd-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="96acd-113">Attributes and Elements</span></span>  
 <span data-ttu-id="96acd-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="96acd-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96acd-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="96acd-115">Attributes</span></span>  
 <span data-ttu-id="96acd-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="96acd-116">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="96acd-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="96acd-117">Child Elements</span></span>  
 <span data-ttu-id="96acd-118">Zdefiniowane przez użytkownika elementy XML.</span><span class="sxs-lookup"><span data-stu-id="96acd-118">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="96acd-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="96acd-119">Parent Elements</span></span>  
  
|<span data-ttu-id="96acd-120">Element</span><span class="sxs-lookup"><span data-stu-id="96acd-120">Element</span></span>|<span data-ttu-id="96acd-121">Opis</span><span class="sxs-lookup"><span data-stu-id="96acd-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96acd-122">\<> punktu końcowego</span><span class="sxs-lookup"><span data-stu-id="96acd-122">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="96acd-123">Konfiguruje różne typy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="96acd-123">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96acd-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="96acd-124">Remarks</span></span>  
 <span data-ttu-id="96acd-125">Opcjonalne nagłówki zawierają bardziej szczegółowe informacje dotyczące adresowania, które identyfikują lub współpracują z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="96acd-125">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="96acd-126">Na przykład nagłówki mogą wskazywać, jak przetwarzać komunikat przychodzący, gdzie punkt końcowy powinien wysłać komunikat odpowiedzi lub którego wystąpienia usługi należy użyć do przetworzenia komunikatu przychodzącego od określonego użytkownika, gdy jest dostępnych wiele wystąpień.</span><span class="sxs-lookup"><span data-stu-id="96acd-126">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96acd-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96acd-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="96acd-128">Punktów końcowych Adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="96acd-128">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)

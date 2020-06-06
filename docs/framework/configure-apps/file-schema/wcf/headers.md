---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 76b3cbf6b867a983c203141bcd901b2b7b4038d5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855171"
---
# \<headers>
<span data-ttu-id="e088b-101">Punkt końcowy może być rozkierowany przy użyciu co najmniej jednego nagłówka SOAP oprócz podstawowego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="e088b-101">An endpoint can be addressed by one or more SOAP headers in addition to its basic URI.</span></span> <span data-ttu-id="e088b-102">Jednym z zestawów scenariuszy, w których jest to przydatne, jest zestaw scenariuszy pośrednich protokołu SOAP, w których punkt końcowy wymaga od klientów tego punktu końcowego dołączenia nagłówków protokołu SOAP przeznaczonych dla pośredników.</span><span class="sxs-lookup"><span data-stu-id="e088b-102">One set of scenarios where this is useful is a set of SOAP intermediary scenarios where an endpoint requires clients of that endpoint to include SOAP headers targeted at intermediaries.</span></span> <span data-ttu-id="e088b-103">Ten element konfiguracji może służyć do definiowania takich niestandardowych nagłówków adresów.</span><span class="sxs-lookup"><span data-stu-id="e088b-103">This configuration element can be used to define such custom address headers.</span></span> <span data-ttu-id="e088b-104">Wpisy w kolekcji nagłówka punktu końcowego są elementami XML zdefiniowanymi przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e088b-104">Entries in the endpoint header collection are user-defined XML elements.</span></span> <span data-ttu-id="e088b-105">Każdy element musi być poprawnie sformułowanym plikiem XML.</span><span class="sxs-lookup"><span data-stu-id="e088b-105">Each element has to be well-formed XML.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<headers>**  
  
## <a name="syntax"></a><span data-ttu-id="e088b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e088b-106">Syntax</span></span>  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e088b-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e088b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e088b-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e088b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e088b-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e088b-109">Attributes</span></span>  
 <span data-ttu-id="e088b-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="e088b-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e088b-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e088b-111">Child Elements</span></span>  
 <span data-ttu-id="e088b-112">Zdefiniowane przez użytkownika elementy XML.</span><span class="sxs-lookup"><span data-stu-id="e088b-112">User-defined XML elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e088b-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e088b-113">Parent Elements</span></span>  
  
|<span data-ttu-id="e088b-114">Element</span><span class="sxs-lookup"><span data-stu-id="e088b-114">Element</span></span>|<span data-ttu-id="e088b-115">Opis</span><span class="sxs-lookup"><span data-stu-id="e088b-115">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-of-client.md)|<span data-ttu-id="e088b-116">Konfiguruje różne typy punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="e088b-116">Configures different types of endpoints.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e088b-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e088b-117">Remarks</span></span>  
 <span data-ttu-id="e088b-118">Opcjonalne nagłówki zawierają bardziej szczegółowe informacje dotyczące adresowania, które identyfikują lub współpracują z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="e088b-118">The optional headers provide more detailed addressing information to identify or interact with the endpoint.</span></span> <span data-ttu-id="e088b-119">Na przykład nagłówki mogą wskazywać, jak przetwarzać komunikat przychodzący, gdzie punkt końcowy powinien wysłać komunikat odpowiedzi lub którego wystąpienia usługi należy użyć do przetworzenia komunikatu przychodzącego od określonego użytkownika, gdy jest dostępnych wiele wystąpień.</span><span class="sxs-lookup"><span data-stu-id="e088b-119">For example, headers can indicate how to process an incoming message, where the endpoint should send a reply message, or which instance of a service to use to process an incoming message from a particular user when multiple instances are available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e088b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e088b-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [<span data-ttu-id="e088b-121">Punkty końcowe: Adresy, powiązania i kontrakty</span><span class="sxs-lookup"><span data-stu-id="e088b-121">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)

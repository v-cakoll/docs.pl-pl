---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: c68cabd03eca71b41a0d0acce26897fa2653f4d3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855377"
---
# <a name="dns"></a><span data-ttu-id="70abf-101">\<dns></span><span class="sxs-lookup"><span data-stu-id="70abf-101">\<dns></span></span>
<span data-ttu-id="70abf-102">Określa oczekiwaną tożsamość serwera.</span><span class="sxs-lookup"><span data-stu-id="70abf-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="70abf-103">Ta tożsamość jest prawidłowa dla trybu uwierzytelniania certyfikatu x509, jeśli certyfikat serwera zawiera system DNS o tej samej wartości.</span><span class="sxs-lookup"><span data-stu-id="70abf-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="70abf-104">Obowiązuje również w przypadku trybu uwierzytelniania systemu Windows, jeśli nazwa SPN ma taką samą wartość.</span><span class="sxs-lookup"><span data-stu-id="70abf-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="70abf-105">Aby uzyskać więcej informacji na temat ustawiania wartości elementu, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="70abf-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
<span data-ttu-id="70abf-106">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="70abf-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="70abf-107">&nbsp;&nbsp;[ **\<> System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="70abf-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="70abf-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)</span><span class="sxs-lookup"><span data-stu-id="70abf-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="70abf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> punktu końcowego**](endpoint-of-client.md)</span><span class="sxs-lookup"><span data-stu-id="70abf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)</span></span>\
<span data-ttu-id="70abf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> tożsamości**](identity.md)</span><span class="sxs-lookup"><span data-stu-id="70abf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)</span></span>\
<span data-ttu-id="70abf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> DNS**</span><span class="sxs-lookup"><span data-stu-id="70abf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70abf-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="70abf-112">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70abf-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="70abf-113">Attributes and Elements</span></span>  
 <span data-ttu-id="70abf-114">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="70abf-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70abf-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="70abf-115">Attributes</span></span>  
  
|<span data-ttu-id="70abf-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="70abf-116">Attribute</span></span>|<span data-ttu-id="70abf-117">Opis</span><span class="sxs-lookup"><span data-stu-id="70abf-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="70abf-118">value</span><span class="sxs-lookup"><span data-stu-id="70abf-118">value</span></span>|<span data-ttu-id="70abf-119">Serwer DNS certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="70abf-119">The DNS of the certificate.</span></span> <span data-ttu-id="70abf-120">DNS to standardowy branżowy protokół używany do lokalizowania komputerów w sieci opartej na protokole IP.</span><span class="sxs-lookup"><span data-stu-id="70abf-120">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="70abf-121">Użytkownicy mogą pamiętać nazwy wyświetlane, takie jak <https://go.microsoft.com/fwlink/?prd=10929> lub [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), łatwiejsze niż adresy oparte na liczbie, takie jak 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="70abf-121">Users can remember display names, such as <https://go.microsoft.com/fwlink/?prd=10929> or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70abf-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="70abf-122">Child Elements</span></span>  
 <span data-ttu-id="70abf-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="70abf-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70abf-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="70abf-124">Parent Elements</span></span>  
  
|<span data-ttu-id="70abf-125">Element</span><span class="sxs-lookup"><span data-stu-id="70abf-125">Element</span></span>|<span data-ttu-id="70abf-126">Opis</span><span class="sxs-lookup"><span data-stu-id="70abf-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70abf-127">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="70abf-127">\<identity></span></span>](identity.md)|<span data-ttu-id="70abf-128">Określa tożsamość usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="70abf-128">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="70abf-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="70abf-129">Example</span></span>  
 <span data-ttu-id="70abf-130">Poniższy kod konfiguracji określa DNS certyfikatu X. 509, który jest używany do uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="70abf-130">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="70abf-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="70abf-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="70abf-132">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="70abf-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="70abf-133">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="70abf-133">\<identity></span></span>](identity.md)

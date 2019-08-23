---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 35d33fd4d174c8e4ccdaaf1ac33884663340e16a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919125"
---
# <a name="dns"></a><span data-ttu-id="76fb6-101">\<dns></span><span class="sxs-lookup"><span data-stu-id="76fb6-101">\<dns></span></span>
<span data-ttu-id="76fb6-102">Określa oczekiwaną tożsamość serwera.</span><span class="sxs-lookup"><span data-stu-id="76fb6-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="76fb6-103">Ta tożsamość jest prawidłowa dla trybu uwierzytelniania certyfikatu x509, jeśli certyfikat serwera zawiera system DNS o tej samej wartości.</span><span class="sxs-lookup"><span data-stu-id="76fb6-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="76fb6-104">Obowiązuje również w przypadku trybu uwierzytelniania systemu Windows, jeśli nazwa SPN ma taką samą wartość.</span><span class="sxs-lookup"><span data-stu-id="76fb6-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="76fb6-105">Aby uzyskać więcej informacji na temat ustawiania wartości elementu, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="76fb6-105">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="76fb6-106">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="76fb6-106">\<identity></span></span>  
<span data-ttu-id="76fb6-107">\<dns></span><span class="sxs-lookup"><span data-stu-id="76fb6-107">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76fb6-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="76fb6-108">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76fb6-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="76fb6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="76fb6-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="76fb6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76fb6-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="76fb6-111">Attributes</span></span>  
  
|<span data-ttu-id="76fb6-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="76fb6-112">Attribute</span></span>|<span data-ttu-id="76fb6-113">Opis</span><span class="sxs-lookup"><span data-stu-id="76fb6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76fb6-114">value</span><span class="sxs-lookup"><span data-stu-id="76fb6-114">value</span></span>|<span data-ttu-id="76fb6-115">Serwer DNS certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="76fb6-115">The DNS of the certificate.</span></span> <span data-ttu-id="76fb6-116">DNS to standardowy branżowy protokół używany do lokalizowania komputerów w sieci opartej na protokole IP.</span><span class="sxs-lookup"><span data-stu-id="76fb6-116">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="76fb6-117">Użytkownicy mogą pamiętać nazwy wyświetlane, takie jak <https://go.microsoft.com/fwlink/?prd=10929> lub [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), łatwiejsze niż adresy oparte na liczbie, takie jak 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="76fb6-117">Users can remember display names, such as <https://go.microsoft.com/fwlink/?prd=10929> or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76fb6-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="76fb6-118">Child Elements</span></span>  
 <span data-ttu-id="76fb6-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="76fb6-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76fb6-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="76fb6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="76fb6-121">Element</span><span class="sxs-lookup"><span data-stu-id="76fb6-121">Element</span></span>|<span data-ttu-id="76fb6-122">Opis</span><span class="sxs-lookup"><span data-stu-id="76fb6-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76fb6-123">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="76fb6-123">\<identity></span></span>](identity.md)|<span data-ttu-id="76fb6-124">Określa tożsamość usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="76fb6-124">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="76fb6-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="76fb6-125">Example</span></span>  
 <span data-ttu-id="76fb6-126">Poniższy kod konfiguracji określa DNS certyfikatu X. 509, który jest używany do uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="76fb6-126">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="76fb6-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76fb6-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="76fb6-128">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="76fb6-128">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="76fb6-129">\<> tożsamości</span><span class="sxs-lookup"><span data-stu-id="76fb6-129">\<identity></span></span>](identity.md)

---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: e49a564c9793b371425b2b787586bb9d3cbed58b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "77452230"
---
# \<dns>
<span data-ttu-id="46a11-101">Określa oczekiwaną tożsamość serwera.</span><span class="sxs-lookup"><span data-stu-id="46a11-101">Specifies the expected identity of the server.</span></span> <span data-ttu-id="46a11-102">Ta tożsamość jest prawidłowa dla trybu uwierzytelniania certyfikatu x509, jeśli certyfikat serwera zawiera system DNS o tej samej wartości.</span><span class="sxs-lookup"><span data-stu-id="46a11-102">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="46a11-103">Obowiązuje również w przypadku trybu uwierzytelniania systemu Windows, jeśli nazwa SPN ma taką samą wartość.</span><span class="sxs-lookup"><span data-stu-id="46a11-103">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
<span data-ttu-id="46a11-104">Aby uzyskać więcej informacji na temat ustawiania wartości elementu, zobacz [tożsamość usługi i uwierzytelnianie](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="46a11-104">For more information about setting the element value, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**  
  
## <a name="syntax"></a><span data-ttu-id="46a11-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="46a11-105">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46a11-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="46a11-106">Attributes and Elements</span></span>  
 <span data-ttu-id="46a11-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="46a11-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46a11-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="46a11-108">Attributes</span></span>  
  
|<span data-ttu-id="46a11-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="46a11-109">Attribute</span></span>|<span data-ttu-id="46a11-110">Opis</span><span class="sxs-lookup"><span data-stu-id="46a11-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46a11-111">value</span><span class="sxs-lookup"><span data-stu-id="46a11-111">value</span></span>|<span data-ttu-id="46a11-112">Serwer DNS certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="46a11-112">The DNS of the certificate.</span></span> <span data-ttu-id="46a11-113">DNS to standardowy branżowy protokół używany do lokalizowania komputerów w sieci opartej na protokole IP.</span><span class="sxs-lookup"><span data-stu-id="46a11-113">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="46a11-114">Użytkownicy mogą pamiętać nazwy wyświetlane, takie jak `https://go.microsoft.com/fwlink/?prd=10929` lub `https://go.microsoft.com/fwlink/?LinkID=96165` , łatwiejsze niż adresy oparte na liczbie, takie jak 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="46a11-114">Users can remember display names, such as `https://go.microsoft.com/fwlink/?prd=10929` or `https://go.microsoft.com/fwlink/?LinkID=96165`, easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46a11-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="46a11-115">Child Elements</span></span>  
 <span data-ttu-id="46a11-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="46a11-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46a11-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="46a11-117">Parent Elements</span></span>  
  
|<span data-ttu-id="46a11-118">Element</span><span class="sxs-lookup"><span data-stu-id="46a11-118">Element</span></span>|<span data-ttu-id="46a11-119">Opis</span><span class="sxs-lookup"><span data-stu-id="46a11-119">Description</span></span>|  
|-------------|-----------------|  
|[\<identity>](identity.md)|<span data-ttu-id="46a11-120">Określa tożsamość usługi do uwierzytelnienia przez klienta.</span><span class="sxs-lookup"><span data-stu-id="46a11-120">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="46a11-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="46a11-121">Example</span></span>  
 <span data-ttu-id="46a11-122">Poniższy kod konfiguracji określa DNS certyfikatu X. 509, który jest używany do uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="46a11-122">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="46a11-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46a11-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="46a11-124">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="46a11-124">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)

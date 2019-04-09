---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: ce12d0a82c8a443994559ed772496897f359b4e4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166676"
---
# <a name="dns"></a><span data-ttu-id="b4c58-101">\<dns></span><span class="sxs-lookup"><span data-stu-id="b4c58-101">\<dns></span></span>
<span data-ttu-id="b4c58-102">Określa oczekiwaną tożsamość serwera.</span><span class="sxs-lookup"><span data-stu-id="b4c58-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="b4c58-103">Ta tożsamość jest nieprawidłowa dla X509 tryb uwierzytelniania certyfikatu, jeśli certyfikat serwera zawiera DNS z taką samą wartość.</span><span class="sxs-lookup"><span data-stu-id="b4c58-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="b4c58-104">Ma również zastosowanie do tryb uwierzytelniania Windows, jeśli nazwa SPN ma taką samą wartość.</span><span class="sxs-lookup"><span data-stu-id="b4c58-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="b4c58-105">Aby uzyskać więcej informacji na temat ustawienia wartości elementu, zobacz [uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b4c58-105">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="b4c58-106">\<identity></span><span class="sxs-lookup"><span data-stu-id="b4c58-106">\<identity></span></span>  
<span data-ttu-id="b4c58-107">\<dns></span><span class="sxs-lookup"><span data-stu-id="b4c58-107">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4c58-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4c58-108">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4c58-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b4c58-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b4c58-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b4c58-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4c58-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b4c58-111">Attributes</span></span>  
  
|<span data-ttu-id="b4c58-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b4c58-112">Attribute</span></span>|<span data-ttu-id="b4c58-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b4c58-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b4c58-114">value</span><span class="sxs-lookup"><span data-stu-id="b4c58-114">value</span></span>|<span data-ttu-id="b4c58-115">DNS certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="b4c58-115">The DNS of the certificate.</span></span> <span data-ttu-id="b4c58-116">Serwer DNS jest standardowym protokołem używanym do lokalizacji komputerów w sieci opartych na protokole IP.</span><span class="sxs-lookup"><span data-stu-id="b4c58-116">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="b4c58-117">Użytkownikom można zapamiętać nazw wyświetlanych, takich jak [ https://go.microsoft.com/fwlink/?prd=10929 ](https://go.microsoft.com/fwlink/?prd=10929) lub [ https://go.microsoft.com/fwlink/?LinkID=96165 ](https://go.microsoft.com/fwlink/?LinkID=96165), na podstawie liczby adresów, takich jak 207.46.131.137 było łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="b4c58-117">Users can remember display names, such as [https://go.microsoft.com/fwlink/?prd=10929](https://go.microsoft.com/fwlink/?prd=10929) or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b4c58-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b4c58-118">Child Elements</span></span>  
 <span data-ttu-id="b4c58-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="b4c58-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b4c58-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b4c58-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b4c58-121">Element</span><span class="sxs-lookup"><span data-stu-id="b4c58-121">Element</span></span>|<span data-ttu-id="b4c58-122">Opis</span><span class="sxs-lookup"><span data-stu-id="b4c58-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4c58-123">\<identity></span><span class="sxs-lookup"><span data-stu-id="b4c58-123">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="b4c58-124">Określa tożsamość usługi, aby zostać uwierzytelnionym przez klienta.</span><span class="sxs-lookup"><span data-stu-id="b4c58-124">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b4c58-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4c58-125">Example</span></span>  
 <span data-ttu-id="b4c58-126">Poniższy kod konfiguracji określa certyfikat X.509, który jest używany do uwierzytelniania serwera DNS.</span><span class="sxs-lookup"><span data-stu-id="b4c58-126">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="b4c58-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4c58-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="b4c58-128">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="b4c58-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="b4c58-129">\<identity></span><span class="sxs-lookup"><span data-stu-id="b4c58-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)

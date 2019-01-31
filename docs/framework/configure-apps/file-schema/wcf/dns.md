---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: eb5459625cf58feeef5ba29d76e74691a4f87cc8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278424"
---
# <a name="dns"></a><span data-ttu-id="6964a-101">\<dns></span><span class="sxs-lookup"><span data-stu-id="6964a-101">\<dns></span></span>
<span data-ttu-id="6964a-102">Określa oczekiwaną tożsamość serwera.</span><span class="sxs-lookup"><span data-stu-id="6964a-102">Specifies the expected identity of the server.</span></span> <span data-ttu-id="6964a-103">Ta tożsamość jest nieprawidłowa dla X509 tryb uwierzytelniania certyfikatu, jeśli certyfikat serwera zawiera DNS z taką samą wartość.</span><span class="sxs-lookup"><span data-stu-id="6964a-103">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="6964a-104">Ma również zastosowanie do tryb uwierzytelniania Windows, jeśli nazwa SPN ma taką samą wartość.</span><span class="sxs-lookup"><span data-stu-id="6964a-104">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="6964a-105">Aby uzyskać więcej informacji na temat ustawienia wartości elementu, zobacz [uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6964a-105">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="6964a-106">\<identity></span><span class="sxs-lookup"><span data-stu-id="6964a-106">\<identity></span></span>  
<span data-ttu-id="6964a-107">\<dns></span><span class="sxs-lookup"><span data-stu-id="6964a-107">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6964a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="6964a-108">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6964a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6964a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6964a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6964a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6964a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6964a-111">Attributes</span></span>  
  
|<span data-ttu-id="6964a-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6964a-112">Attribute</span></span>|<span data-ttu-id="6964a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="6964a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6964a-114">value</span><span class="sxs-lookup"><span data-stu-id="6964a-114">value</span></span>|<span data-ttu-id="6964a-115">DNS certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="6964a-115">The DNS of the certificate.</span></span> <span data-ttu-id="6964a-116">Serwer DNS jest standardowym protokołem używanym do lokalizacji komputerów w sieci opartych na protokole IP.</span><span class="sxs-lookup"><span data-stu-id="6964a-116">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="6964a-117">Użytkownikom można zapamiętać nazw wyświetlanych, takich jak [ https://go.microsoft.com/fwlink/?prd=10929 ](https://go.microsoft.com/fwlink/?prd=10929) lub [ https://go.microsoft.com/fwlink/?LinkID=96165 ](https://go.microsoft.com/fwlink/?LinkID=96165), na podstawie liczby adresów, takich jak 207.46.131.137 było łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="6964a-117">Users can remember display names, such as [https://go.microsoft.com/fwlink/?prd=10929](https://go.microsoft.com/fwlink/?prd=10929) or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6964a-118">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6964a-118">Child Elements</span></span>  
 <span data-ttu-id="6964a-119">Brak.</span><span class="sxs-lookup"><span data-stu-id="6964a-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6964a-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6964a-120">Parent Elements</span></span>  
  
|<span data-ttu-id="6964a-121">Element</span><span class="sxs-lookup"><span data-stu-id="6964a-121">Element</span></span>|<span data-ttu-id="6964a-122">Opis</span><span class="sxs-lookup"><span data-stu-id="6964a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6964a-123">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="6964a-123">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="6964a-124">Określa tożsamość usługi, aby zostać uwierzytelnionym przez klienta.</span><span class="sxs-lookup"><span data-stu-id="6964a-124">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6964a-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="6964a-125">Example</span></span>  
 <span data-ttu-id="6964a-126">Poniższy kod konfiguracji określa certyfikat X.509, który jest używany do uwierzytelniania serwera DNS.</span><span class="sxs-lookup"><span data-stu-id="6964a-126">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="6964a-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6964a-127">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="6964a-128">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="6964a-128">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="6964a-129">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="6964a-129">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)

---
title: '&lt;dns&gt;'
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: 68cbb25b79bbda301c29d72800a125c7a6ba0b6f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616462"
---
# <a name="ltdnsgt"></a><span data-ttu-id="e9b3e-102">&lt;dns&gt;</span><span class="sxs-lookup"><span data-stu-id="e9b3e-102">&lt;dns&gt;</span></span>
<span data-ttu-id="e9b3e-103">Określa oczekiwaną tożsamość serwera.</span><span class="sxs-lookup"><span data-stu-id="e9b3e-103">Specifies the expected identity of the server.</span></span> <span data-ttu-id="e9b3e-104">Ta tożsamość jest nieprawidłowa dla X509 tryb uwierzytelniania certyfikatu, jeśli certyfikat serwera zawiera DNS z taką samą wartość.</span><span class="sxs-lookup"><span data-stu-id="e9b3e-104">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="e9b3e-105">Ma również zastosowanie do tryb uwierzytelniania Windows, jeśli nazwa SPN ma taką samą wartość.</span><span class="sxs-lookup"><span data-stu-id="e9b3e-105">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="e9b3e-106">Aby uzyskać więcej informacji na temat ustawienia wartości elementu, zobacz [uwierzytelnianie i tożsamość usług](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e9b3e-106">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="e9b3e-107">\<identity></span><span class="sxs-lookup"><span data-stu-id="e9b3e-107">\<identity></span></span>  
<span data-ttu-id="e9b3e-108">\<dns></span><span class="sxs-lookup"><span data-stu-id="e9b3e-108">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9b3e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9b3e-109">Syntax</span></span>  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9b3e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e9b3e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e9b3e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e9b3e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9b3e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e9b3e-112">Attributes</span></span>  
  
|<span data-ttu-id="e9b3e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e9b3e-113">Attribute</span></span>|<span data-ttu-id="e9b3e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e9b3e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e9b3e-115">value</span><span class="sxs-lookup"><span data-stu-id="e9b3e-115">value</span></span>|<span data-ttu-id="e9b3e-116">DNS certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e9b3e-116">The DNS of the certificate.</span></span> <span data-ttu-id="e9b3e-117">Serwer DNS jest standardowym protokołem używanym do lokalizacji komputerów w sieci opartych na protokole IP.</span><span class="sxs-lookup"><span data-stu-id="e9b3e-117">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="e9b3e-118">Użytkownikom można zapamiętać nazw wyświetlanych, takich jak [ https://go.microsoft.com/fwlink/?prd=10929 ](https://go.microsoft.com/fwlink/?prd=10929) lub [ https://go.microsoft.com/fwlink/?LinkID=96165 ](https://go.microsoft.com/fwlink/?LinkID=96165), na podstawie liczby adresów, takich jak 207.46.131.137 było łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="e9b3e-118">Users can remember display names, such as [https://go.microsoft.com/fwlink/?prd=10929](https://go.microsoft.com/fwlink/?prd=10929) or [https://go.microsoft.com/fwlink/?LinkID=96165](https://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9b3e-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e9b3e-119">Child Elements</span></span>  
 <span data-ttu-id="e9b3e-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="e9b3e-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9b3e-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e9b3e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e9b3e-122">Element</span><span class="sxs-lookup"><span data-stu-id="e9b3e-122">Element</span></span>|<span data-ttu-id="e9b3e-123">Opis</span><span class="sxs-lookup"><span data-stu-id="e9b3e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9b3e-124">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="e9b3e-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="e9b3e-125">Określa tożsamość usługi, aby zostać uwierzytelnionym przez klienta.</span><span class="sxs-lookup"><span data-stu-id="e9b3e-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e9b3e-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="e9b3e-126">Example</span></span>  
 <span data-ttu-id="e9b3e-127">Poniższy kod konfiguracji określa certyfikat X.509, który jest używany do uwierzytelniania serwera DNS.</span><span class="sxs-lookup"><span data-stu-id="e9b3e-127">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a><span data-ttu-id="e9b3e-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e9b3e-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [<span data-ttu-id="e9b3e-129">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="e9b3e-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e9b3e-130">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="e9b3e-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)

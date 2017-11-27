---
title: '&lt;DNS&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f2e3dbd0781485336a441c8eacb536ad008ff7a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltdnsgt"></a><span data-ttu-id="09c82-102">&lt;DNS&gt;</span><span class="sxs-lookup"><span data-stu-id="09c82-102">&lt;dns&gt;</span></span>
<span data-ttu-id="09c82-103">Określa oczekiwaną tożsamość serwera.</span><span class="sxs-lookup"><span data-stu-id="09c82-103">Specifies the expected identity of the server.</span></span> <span data-ttu-id="09c82-104">Ta tożsamość jest nieprawidłowa dla X509 tryb uwierzytelniania certyfikatu, jeśli certyfikat serwera zawiera DNS o tej samej wartości.</span><span class="sxs-lookup"><span data-stu-id="09c82-104">This identity is valid for X509 Certificate authentication mode if the server’s certificate contains a DNS with the same value.</span></span> <span data-ttu-id="09c82-105">Ma również zastosowanie do trybu uwierzytelniania systemu Windows, jeśli nazwa SPN ma taką samą wartość.</span><span class="sxs-lookup"><span data-stu-id="09c82-105">It is also valid for Windows authentication mode if the SPN has the same value.</span></span>  
  
 <span data-ttu-id="09c82-106">Aby uzyskać więcej informacji na temat ustawiania wartości elementu, zobacz [uwierzytelnianie i tożsamość usługi](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="09c82-106">For more information about setting the element value, see [Service Identity and Authentication](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="09c82-107">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="09c82-107">\<identity></span></span>  
<span data-ttu-id="09c82-108">\<DNS ></span><span class="sxs-lookup"><span data-stu-id="09c82-108">\<dns></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09c82-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="09c82-109">Syntax</span></span>  
  
```xml  
<dns value = "String" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09c82-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="09c82-110">Attributes and Elements</span></span>  
 <span data-ttu-id="09c82-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="09c82-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09c82-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="09c82-112">Attributes</span></span>  
  
|<span data-ttu-id="09c82-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="09c82-113">Attribute</span></span>|<span data-ttu-id="09c82-114">Opis</span><span class="sxs-lookup"><span data-stu-id="09c82-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="09c82-115">value</span><span class="sxs-lookup"><span data-stu-id="09c82-115">value</span></span>|<span data-ttu-id="09c82-116">DNS certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="09c82-116">The DNS of the certificate.</span></span> <span data-ttu-id="09c82-117">Usługa DNS jest standardowym protokołem używanym do lokalizacji komputerów w sieciach opartych na protokole IP.</span><span class="sxs-lookup"><span data-stu-id="09c82-117">DNS is an industry-standard protocol used to locate computers on an IP-based network.</span></span> <span data-ttu-id="09c82-118">Użytkownicy do zapamiętania nazw wyświetlanych, takich jak [http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929) lub [http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165), łatwiejsze niż liczbowe adresów, takich jak 207.46.131.137.</span><span class="sxs-lookup"><span data-stu-id="09c82-118">Users can remember display names, such as [http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929) or [http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165), easier than number-based addresses, such as 207.46.131.137.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09c82-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="09c82-119">Child Elements</span></span>  
 <span data-ttu-id="09c82-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="09c82-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="09c82-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="09c82-121">Parent Elements</span></span>  
  
|<span data-ttu-id="09c82-122">Element</span><span class="sxs-lookup"><span data-stu-id="09c82-122">Element</span></span>|<span data-ttu-id="09c82-123">Opis</span><span class="sxs-lookup"><span data-stu-id="09c82-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="09c82-124">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="09c82-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="09c82-125">Określa tożsamość usługi uwierzytelniania przez klienta.</span><span class="sxs-lookup"><span data-stu-id="09c82-125">Specifies the identity of the service to be authenticated by the client.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="09c82-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="09c82-126">Example</span></span>  
 <span data-ttu-id="09c82-127">Poniższy kod konfiguracji określa certyfikat X.509 używany do uwierzytelniania serwera DNS.</span><span class="sxs-lookup"><span data-stu-id="09c82-127">The following configuration code specifies the DNS of an X.509 certificate that is used to authenticate a server.</span></span>  
  
```xml  
<identity>  
  <dns value = "www.cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a><span data-ttu-id="09c82-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09c82-128">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.DnsEndpointIdentity>  
 [<span data-ttu-id="09c82-129">Uwierzytelnianie i tożsamość usług</span><span class="sxs-lookup"><span data-stu-id="09c82-129">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="09c82-130">\<tożsamość ></span><span class="sxs-lookup"><span data-stu-id="09c82-130">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)

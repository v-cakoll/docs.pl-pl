---
title: <security> dla <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 4969c041678bbf3490975bc0ec53507b6cf762bb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738604"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="982a3-102">\<security> dla \<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="982a3-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="982a3-103">Definiuje możliwości zabezpieczeń programu [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="982a3-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="982a3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="982a3-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="982a3-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="982a3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="982a3-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="982a3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="982a3-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="982a3-107">Attributes</span></span>  
  
|<span data-ttu-id="982a3-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="982a3-108">Attribute</span></span>|<span data-ttu-id="982a3-109">Opis</span><span class="sxs-lookup"><span data-stu-id="982a3-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="982a3-110">tryb</span><span class="sxs-lookup"><span data-stu-id="982a3-110">mode</span></span>|<span data-ttu-id="982a3-111">Obowiązkowe.</span><span class="sxs-lookup"><span data-stu-id="982a3-111">-   Optional.</span></span> <span data-ttu-id="982a3-112">Określa typ stosowanego zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="982a3-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="982a3-113">Wartość domyślna to `Message`.</span><span class="sxs-lookup"><span data-stu-id="982a3-113">The default value is `Message`.</span></span> <span data-ttu-id="982a3-114">Ten atrybut jest typu <xref:System.ServiceModel.WSDualHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="982a3-114">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="982a3-115">Atrybut Mode</span><span class="sxs-lookup"><span data-stu-id="982a3-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="982a3-116">Wartość</span><span class="sxs-lookup"><span data-stu-id="982a3-116">Value</span></span>|<span data-ttu-id="982a3-117">Opis</span><span class="sxs-lookup"><span data-stu-id="982a3-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="982a3-118">Brak</span><span class="sxs-lookup"><span data-stu-id="982a3-118">None</span></span>|<span data-ttu-id="982a3-119">Zabezpieczenia są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="982a3-119">Security is disabled.</span></span>|  
|<span data-ttu-id="982a3-120">Komunikat</span><span class="sxs-lookup"><span data-stu-id="982a3-120">Message</span></span>|<span data-ttu-id="982a3-121">Zabezpieczenia są udostępniane przy użyciu zabezpieczeń komunikatów protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="982a3-121">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="982a3-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="982a3-122">Child Elements</span></span>  
  
|<span data-ttu-id="982a3-123">Element</span><span class="sxs-lookup"><span data-stu-id="982a3-123">Element</span></span>|<span data-ttu-id="982a3-124">Opis</span><span class="sxs-lookup"><span data-stu-id="982a3-124">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="982a3-125">Definiuje ustawienia zabezpieczeń na poziomie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="982a3-125">Defines the settings for the message-level security.</span></span> <span data-ttu-id="982a3-126">Ten element jest typu <xref:System.ServiceModel.MessageSecurityOverHttp> .</span><span class="sxs-lookup"><span data-stu-id="982a3-126">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="982a3-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="982a3-127">Parent Elements</span></span>  
  
|<span data-ttu-id="982a3-128">Element</span><span class="sxs-lookup"><span data-stu-id="982a3-128">Element</span></span>|<span data-ttu-id="982a3-129">Opis</span><span class="sxs-lookup"><span data-stu-id="982a3-129">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="982a3-130">Definiuje wszystkie możliwości powiązań [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="982a3-130">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="982a3-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="982a3-131">Remarks</span></span>  
 <span data-ttu-id="982a3-132">Podwójne powiązanie uwidacznia adres IP klienta w usłudze.</span><span class="sxs-lookup"><span data-stu-id="982a3-132">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="982a3-133">Klient powinien korzystać z zabezpieczeń, aby upewnić się, że tylko nawiązuje połączenie z usługami, które ufają.</span><span class="sxs-lookup"><span data-stu-id="982a3-133">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="982a3-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="982a3-134">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="982a3-135">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="982a3-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="982a3-136">Powiązania</span><span class="sxs-lookup"><span data-stu-id="982a3-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="982a3-137">Konfigurowanie powiązań dostarczanych przez system</span><span class="sxs-lookup"><span data-stu-id="982a3-137">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="982a3-138">Konfigurowanie usług i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="982a3-138">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

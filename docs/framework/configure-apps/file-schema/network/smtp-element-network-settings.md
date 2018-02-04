---
title: '&lt;SMTP&gt; elementu (ustawienia sieciowe)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: f5b2a3b7eec17fbdd12181c29f610d2b2ad32bd4
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="ltsmtpgt-element-network-settings"></a><span data-ttu-id="c3319-102">&lt;SMTP&gt; elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="c3319-102">&lt;smtp&gt; Element (Network Settings)</span></span>
<span data-ttu-id="c3319-103">Określa format dostarczania, metody dostarczania i z adresu do wysyłania wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="c3319-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="c3319-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c3319-104">\<configuration></span></span>  
<span data-ttu-id="c3319-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="c3319-105">\<system.net></span></span>  
<span data-ttu-id="c3319-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="c3319-106">\<mailSettings></span></span>  
<span data-ttu-id="c3319-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="c3319-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3319-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3319-108">Syntax</span></span>  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3319-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c3319-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c3319-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c3319-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3319-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c3319-111">Attributes</span></span>  
  
|<span data-ttu-id="c3319-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c3319-112">Attribute</span></span>|<span data-ttu-id="c3319-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c3319-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="c3319-114">Określa format dostarczania wychodzących wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="c3319-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="c3319-115">Dopuszczalne wartości to SevenBit i międzynarodowe.</span><span class="sxs-lookup"><span data-stu-id="c3319-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="c3319-116">Określa metodę dostarczania dla wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="c3319-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="c3319-117">Dopuszczalne wartości to sieci, pickupDirectoryFromIis i specifiedpickupdirectory —.</span><span class="sxs-lookup"><span data-stu-id="c3319-117">Acceptable values are network, pickupDirectoryFromIis, and specifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="c3319-118">Określa adres początkowy dla wychodzących wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="c3319-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3319-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c3319-119">Child Elements</span></span>  
  
|<span data-ttu-id="c3319-120">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c3319-120">Attribute</span></span>|<span data-ttu-id="c3319-121">Opis</span><span class="sxs-lookup"><span data-stu-id="c3319-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="c3319-122">Konfiguruje katalogu lokalnego dla serwera transportu protokołu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="c3319-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="c3319-123">Służy do konfigurowania opcji sieciowych do zewnętrznego serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="c3319-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c3319-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c3319-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c3319-125">**Element**</span><span class="sxs-lookup"><span data-stu-id="c3319-125">**Element**</span></span>|<span data-ttu-id="c3319-126">**Opis**</span><span class="sxs-lookup"><span data-stu-id="c3319-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c3319-127">\<mailSettings > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="c3319-127">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="c3319-128">Konfiguruje opcje wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="c3319-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c3319-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="c3319-129">Example</span></span>  
 <span data-ttu-id="c3319-130">W poniższym przykładzie odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu poświadczeń domyślnych w sieci.</span><span class="sxs-lookup"><span data-stu-id="c3319-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c3319-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c3319-131">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [<span data-ttu-id="c3319-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="c3319-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

---
title: '&lt;SMTP&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 61110413f43e95060aa2cfecb4acdb3ebaae14df
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2018
ms.locfileid: "47425826"
---
# <a name="ltsmtpgt-element-network-settings"></a><span data-ttu-id="fd8a1-102">&lt;SMTP&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="fd8a1-102">&lt;smtp&gt; Element (Network Settings)</span></span>
<span data-ttu-id="fd8a1-103">Konfiguruje format dostarczania, metodę dostarczania i z adresu do wysyłania wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="fd8a1-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="fd8a1-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="fd8a1-104">\<configuration></span></span>  
<span data-ttu-id="fd8a1-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="fd8a1-105">\<system.net></span></span>  
<span data-ttu-id="fd8a1-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="fd8a1-106">\<mailSettings></span></span>  
<span data-ttu-id="fd8a1-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="fd8a1-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd8a1-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd8a1-108">Syntax</span></span>  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd8a1-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fd8a1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="fd8a1-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fd8a1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd8a1-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fd8a1-111">Attributes</span></span>  
  
|<span data-ttu-id="fd8a1-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fd8a1-112">Attribute</span></span>|<span data-ttu-id="fd8a1-113">Opis</span><span class="sxs-lookup"><span data-stu-id="fd8a1-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="fd8a1-114">Określa format dostarczania wychodzących wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="fd8a1-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="fd8a1-115">Dopuszczalne wartości to SevenBit i międzynarodowe.</span><span class="sxs-lookup"><span data-stu-id="fd8a1-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="fd8a1-116">Określa metodę dostarczania wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="fd8a1-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="fd8a1-117">Dopuszczalne wartości to sieć, PickupDirectoryFromIis i SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="fd8a1-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="fd8a1-118">Określa adres początkowy dla wychodzących wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="fd8a1-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd8a1-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fd8a1-119">Child Elements</span></span>  
  
|<span data-ttu-id="fd8a1-120">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fd8a1-120">Attribute</span></span>|<span data-ttu-id="fd8a1-121">Opis</span><span class="sxs-lookup"><span data-stu-id="fd8a1-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="fd8a1-122">Konfiguruje katalog lokalny dla serwera transportu protokołu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="fd8a1-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="fd8a1-123">Konfiguruje opcje sieciowe dla zewnętrznego serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="fd8a1-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fd8a1-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fd8a1-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fd8a1-125">**Element**</span><span class="sxs-lookup"><span data-stu-id="fd8a1-125">**Element**</span></span>|<span data-ttu-id="fd8a1-126">**Opis**</span><span class="sxs-lookup"><span data-stu-id="fd8a1-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="fd8a1-127">\<mailSettings — >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="fd8a1-127">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="fd8a1-128">Konfiguruje opcje wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="fd8a1-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fd8a1-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="fd8a1-129">Example</span></span>  
 <span data-ttu-id="fd8a1-130">Poniższy przykład określa odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu poświadczeń domyślnych sieci.</span><span class="sxs-lookup"><span data-stu-id="fd8a1-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
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
  
## <a name="see-also"></a><span data-ttu-id="fd8a1-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd8a1-131">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [<span data-ttu-id="fd8a1-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="fd8a1-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

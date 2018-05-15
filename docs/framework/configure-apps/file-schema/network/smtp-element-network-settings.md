---
title: '&lt;SMTP&gt; elementu (ustawienia sieciowe)'
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
manager: markl
ms.openlocfilehash: 56912e09d24fc83e93a91cc42b1d96dcc68210f2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltsmtpgt-element-network-settings"></a><span data-ttu-id="3a086-102">&lt;SMTP&gt; elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="3a086-102">&lt;smtp&gt; Element (Network Settings)</span></span>
<span data-ttu-id="3a086-103">Określa format dostarczania, metody dostarczania i z adresu do wysyłania wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="3a086-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="3a086-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="3a086-104">\<configuration></span></span>  
<span data-ttu-id="3a086-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="3a086-105">\<system.net></span></span>  
<span data-ttu-id="3a086-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="3a086-106">\<mailSettings></span></span>  
<span data-ttu-id="3a086-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="3a086-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a086-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a086-108">Syntax</span></span>  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a086-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3a086-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3a086-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3a086-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a086-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3a086-111">Attributes</span></span>  
  
|<span data-ttu-id="3a086-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3a086-112">Attribute</span></span>|<span data-ttu-id="3a086-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3a086-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="3a086-114">Określa format dostarczania wychodzących wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="3a086-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="3a086-115">Dopuszczalne wartości to SevenBit i międzynarodowe.</span><span class="sxs-lookup"><span data-stu-id="3a086-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="3a086-116">Określa metodę dostarczania dla wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="3a086-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="3a086-117">Dopuszczalne wartości to sieci, pickupDirectoryFromIis i specifiedpickupdirectory —.</span><span class="sxs-lookup"><span data-stu-id="3a086-117">Acceptable values are network, pickupDirectoryFromIis, and specifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="3a086-118">Określa adres początkowy dla wychodzących wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="3a086-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a086-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3a086-119">Child Elements</span></span>  
  
|<span data-ttu-id="3a086-120">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3a086-120">Attribute</span></span>|<span data-ttu-id="3a086-121">Opis</span><span class="sxs-lookup"><span data-stu-id="3a086-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="3a086-122">Konfiguruje katalogu lokalnego dla serwera transportu protokołu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="3a086-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="3a086-123">Służy do konfigurowania opcji sieciowych do zewnętrznego serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="3a086-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a086-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3a086-124">Parent Elements</span></span>  
  
|<span data-ttu-id="3a086-125">**Element**</span><span class="sxs-lookup"><span data-stu-id="3a086-125">**Element**</span></span>|<span data-ttu-id="3a086-126">**Opis**</span><span class="sxs-lookup"><span data-stu-id="3a086-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3a086-127">\<mailSettings > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="3a086-127">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="3a086-128">Konfiguruje opcje wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="3a086-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3a086-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a086-129">Example</span></span>  
 <span data-ttu-id="3a086-130">W poniższym przykładzie odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu poświadczeń domyślnych w sieci.</span><span class="sxs-lookup"><span data-stu-id="3a086-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a086-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a086-131">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [<span data-ttu-id="3a086-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="3a086-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

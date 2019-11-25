---
title: <smtp>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 625c3cb82a8659c742b540724e5cf31be65a705e
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089103"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="47c58-102">\<> SMTP (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="47c58-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="47c58-103">Konfiguruje format dostarczania, metodę dostarczania i adres nadawcy wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="47c58-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
<span data-ttu-id="47c58-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="47c58-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="47c58-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="47c58-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="47c58-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<mailSettings >** ](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="47c58-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="47c58-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**smtp >**</span><span class="sxs-lookup"><span data-stu-id="47c58-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="47c58-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="47c58-108">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47c58-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="47c58-109">Attributes and Elements</span></span>  
 <span data-ttu-id="47c58-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="47c58-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47c58-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="47c58-111">Attributes</span></span>  
  
|<span data-ttu-id="47c58-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="47c58-112">Attribute</span></span>|<span data-ttu-id="47c58-113">Opis</span><span class="sxs-lookup"><span data-stu-id="47c58-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="47c58-114">Określa format dostarczania wychodzących wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="47c58-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="47c58-115">Akceptowalne wartości to SevenBit i International.</span><span class="sxs-lookup"><span data-stu-id="47c58-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="47c58-116">Określa metodę dostarczania wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="47c58-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="47c58-117">Dopuszczalne wartości to Network, PickupDirectoryFromIis i SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="47c58-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="47c58-118">Określa adres od dla wychodzących wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="47c58-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47c58-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="47c58-119">Child Elements</span></span>  
  
|<span data-ttu-id="47c58-120">Atrybut</span><span class="sxs-lookup"><span data-stu-id="47c58-120">Attribute</span></span>|<span data-ttu-id="47c58-121">Opis</span><span class="sxs-lookup"><span data-stu-id="47c58-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="47c58-122">Konfiguruje katalog lokalny dla serwera SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="47c58-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="47c58-123">Konfiguruje opcje sieci dla zewnętrznego serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="47c58-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="47c58-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="47c58-124">Parent Elements</span></span>  
  
|<span data-ttu-id="47c58-125">**Element**</span><span class="sxs-lookup"><span data-stu-id="47c58-125">**Element**</span></span>|<span data-ttu-id="47c58-126">**Opis**</span><span class="sxs-lookup"><span data-stu-id="47c58-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="47c58-127">\<element > mailSettings (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="47c58-127">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="47c58-128">Konfiguruje opcje wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="47c58-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="47c58-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="47c58-129">Example</span></span>  
 <span data-ttu-id="47c58-130">W poniższym przykładzie określono odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu domyślnych poświadczeń sieciowych.</span><span class="sxs-lookup"><span data-stu-id="47c58-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="47c58-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47c58-131">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="47c58-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="47c58-132">Network Settings Schema</span></span>](index.md)

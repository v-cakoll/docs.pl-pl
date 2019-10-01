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
ms.openlocfilehash: 2105a6dd25a7f6e5e4c1ce286be7f60beae1dca0
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697608"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="61324-102">\<smtp >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="61324-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="61324-103">Konfiguruje format dostarczania, metodę dostarczania i adres nadawcy wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="61324-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[<span data-ttu-id="61324-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="61324-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="61324-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="61324-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="61324-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<mailSettings >** ](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="61324-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>  
<span data-ttu-id="61324-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<smtp >**</span><span class="sxs-lookup"><span data-stu-id="61324-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61324-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="61324-108">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="61324-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="61324-109">Attributes and Elements</span></span>  
 <span data-ttu-id="61324-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="61324-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="61324-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="61324-111">Attributes</span></span>  
  
|<span data-ttu-id="61324-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="61324-112">Attribute</span></span>|<span data-ttu-id="61324-113">Opis</span><span class="sxs-lookup"><span data-stu-id="61324-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="61324-114">Określa format dostarczania wychodzących wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="61324-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="61324-115">Akceptowalne wartości to SevenBit i International.</span><span class="sxs-lookup"><span data-stu-id="61324-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="61324-116">Określa metodę dostarczania wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="61324-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="61324-117">Dopuszczalne wartości to Network, PickupDirectoryFromIis i SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="61324-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="61324-118">Określa adres od dla wychodzących wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="61324-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="61324-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="61324-119">Child Elements</span></span>  
  
|<span data-ttu-id="61324-120">Atrybut</span><span class="sxs-lookup"><span data-stu-id="61324-120">Attribute</span></span>|<span data-ttu-id="61324-121">Opis</span><span class="sxs-lookup"><span data-stu-id="61324-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="61324-122">Konfiguruje katalog lokalny dla serwera SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="61324-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="61324-123">Konfiguruje opcje sieci dla zewnętrznego serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="61324-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="61324-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="61324-124">Parent Elements</span></span>  
  
|<span data-ttu-id="61324-125">**Element**</span><span class="sxs-lookup"><span data-stu-id="61324-125">**Element**</span></span>|<span data-ttu-id="61324-126">**Opis**</span><span class="sxs-lookup"><span data-stu-id="61324-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="61324-127">\<mailSettings >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="61324-127">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="61324-128">Konfiguruje opcje wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="61324-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="61324-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="61324-129">Example</span></span>  
 <span data-ttu-id="61324-130">W poniższym przykładzie określono odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu domyślnych poświadczeń sieciowych.</span><span class="sxs-lookup"><span data-stu-id="61324-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="61324-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61324-131">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="61324-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="61324-132">Network Settings Schema</span></span>](index.md)

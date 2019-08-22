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
ms.openlocfilehash: ac9405fdc6123a5a1352de06f94fefb6d7d4014b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659122"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="cbb13-102">\<> SMTP — element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="cbb13-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="cbb13-103">Konfiguruje format dostarczania, metodę dostarczania i adres nadawcy wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="cbb13-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="cbb13-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="cbb13-104">\<configuration></span></span>  
<span data-ttu-id="cbb13-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="cbb13-105">\<system.net></span></span>  
<span data-ttu-id="cbb13-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="cbb13-106">\<mailSettings></span></span>  
<span data-ttu-id="cbb13-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="cbb13-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbb13-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="cbb13-108">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cbb13-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cbb13-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cbb13-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cbb13-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cbb13-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cbb13-111">Attributes</span></span>  
  
|<span data-ttu-id="cbb13-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cbb13-112">Attribute</span></span>|<span data-ttu-id="cbb13-113">Opis</span><span class="sxs-lookup"><span data-stu-id="cbb13-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="cbb13-114">Określa format dostarczania wychodzących wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="cbb13-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="cbb13-115">Akceptowalne wartości to SevenBit i International.</span><span class="sxs-lookup"><span data-stu-id="cbb13-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="cbb13-116">Określa metodę dostarczania wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="cbb13-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="cbb13-117">Dopuszczalne wartości to Network, PickupDirectoryFromIis i SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="cbb13-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="cbb13-118">Określa adres od dla wychodzących wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="cbb13-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cbb13-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cbb13-119">Child Elements</span></span>  
  
|<span data-ttu-id="cbb13-120">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cbb13-120">Attribute</span></span>|<span data-ttu-id="cbb13-121">Opis</span><span class="sxs-lookup"><span data-stu-id="cbb13-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="cbb13-122">Konfiguruje katalog lokalny dla serwera SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="cbb13-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="cbb13-123">Konfiguruje opcje sieci dla zewnętrznego serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="cbb13-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cbb13-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cbb13-124">Parent Elements</span></span>  
  
|<span data-ttu-id="cbb13-125">**Element**</span><span class="sxs-lookup"><span data-stu-id="cbb13-125">**Element**</span></span>|<span data-ttu-id="cbb13-126">**Opis**</span><span class="sxs-lookup"><span data-stu-id="cbb13-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cbb13-127">\<mailSettings >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="cbb13-127">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="cbb13-128">Konfiguruje opcje wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="cbb13-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cbb13-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="cbb13-129">Example</span></span>  
 <span data-ttu-id="cbb13-130">W poniższym przykładzie określono odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu domyślnych poświadczeń sieciowych.</span><span class="sxs-lookup"><span data-stu-id="cbb13-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cbb13-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cbb13-131">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="cbb13-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="cbb13-132">Network Settings Schema</span></span>](index.md)

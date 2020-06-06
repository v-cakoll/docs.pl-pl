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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089103"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="2d80b-102">\<smtp>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="2d80b-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="2d80b-103">Konfiguruje format dostarczania, metodę dostarczania i adres nadawcy wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="2d80b-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**
  
## <a name="syntax"></a><span data-ttu-id="2d80b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d80b-104">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d80b-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2d80b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2d80b-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2d80b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d80b-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2d80b-107">Attributes</span></span>  
  
|<span data-ttu-id="2d80b-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2d80b-108">Attribute</span></span>|<span data-ttu-id="2d80b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2d80b-109">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="2d80b-110">Określa format dostarczania wychodzących wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="2d80b-110">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="2d80b-111">Akceptowalne wartości to SevenBit i International.</span><span class="sxs-lookup"><span data-stu-id="2d80b-111">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="2d80b-112">Określa metodę dostarczania wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="2d80b-112">Specifies the delivery method for emails.</span></span> <span data-ttu-id="2d80b-113">Dopuszczalne wartości to Network, PickupDirectoryFromIis i SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="2d80b-113">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="2d80b-114">Określa adres od dla wychodzących wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="2d80b-114">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d80b-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2d80b-115">Child Elements</span></span>  
  
|<span data-ttu-id="2d80b-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2d80b-116">Attribute</span></span>|<span data-ttu-id="2d80b-117">Opis</span><span class="sxs-lookup"><span data-stu-id="2d80b-117">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="2d80b-118">Konfiguruje katalog lokalny dla serwera SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="2d80b-118">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="2d80b-119">Konfiguruje opcje sieci dla zewnętrznego serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="2d80b-119">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2d80b-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2d80b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2d80b-121">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="2d80b-121">**Element**</span></span>|<span data-ttu-id="2d80b-122">**Opis**</span><span class="sxs-lookup"><span data-stu-id="2d80b-122">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2d80b-123">\<mailSettings>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="2d80b-123">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="2d80b-124">Konfiguruje opcje wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="2d80b-124">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2d80b-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d80b-125">Example</span></span>  
 <span data-ttu-id="2d80b-126">W poniższym przykładzie określono odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu domyślnych poświadczeń sieciowych.</span><span class="sxs-lookup"><span data-stu-id="2d80b-126">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2d80b-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2d80b-127">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="2d80b-128">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="2d80b-128">Network Settings Schema</span></span>](index.md)

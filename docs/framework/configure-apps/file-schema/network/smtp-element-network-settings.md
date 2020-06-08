---
title: <smtp>, element (ustawienia sieci)
description: <smtp>Element ustawienia sieci konfiguruje format dostarczania, metodę dostarczania i adres nadawcy na potrzeby wysyłania wiadomości e-mail w .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: b30b82922a69ea660f4c4abfd808e89fa9945183
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504514"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="69caf-103">\<smtp>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="69caf-103">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="69caf-104">Konfiguruje format dostarczania, metodę dostarczania i adres nadawcy wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="69caf-104">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**
  
## <a name="syntax"></a><span data-ttu-id="69caf-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="69caf-105">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69caf-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="69caf-106">Attributes and Elements</span></span>  
 <span data-ttu-id="69caf-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="69caf-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69caf-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="69caf-108">Attributes</span></span>  
  
|<span data-ttu-id="69caf-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="69caf-109">Attribute</span></span>|<span data-ttu-id="69caf-110">Opis</span><span class="sxs-lookup"><span data-stu-id="69caf-110">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="69caf-111">Określa format dostarczania wychodzących wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="69caf-111">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="69caf-112">Akceptowalne wartości to SevenBit i International.</span><span class="sxs-lookup"><span data-stu-id="69caf-112">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="69caf-113">Określa metodę dostarczania wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="69caf-113">Specifies the delivery method for emails.</span></span> <span data-ttu-id="69caf-114">Dopuszczalne wartości to Network, PickupDirectoryFromIis i SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="69caf-114">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="69caf-115">Określa adres od dla wychodzących wiadomości e-mail.</span><span class="sxs-lookup"><span data-stu-id="69caf-115">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69caf-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="69caf-116">Child Elements</span></span>  
  
|<span data-ttu-id="69caf-117">Atrybut</span><span class="sxs-lookup"><span data-stu-id="69caf-117">Attribute</span></span>|<span data-ttu-id="69caf-118">Opis</span><span class="sxs-lookup"><span data-stu-id="69caf-118">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="69caf-119">Konfiguruje katalog lokalny dla serwera SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="69caf-119">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="69caf-120">Konfiguruje opcje sieci dla zewnętrznego serwera SMTP.</span><span class="sxs-lookup"><span data-stu-id="69caf-120">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69caf-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="69caf-121">Parent Elements</span></span>  
  
|<span data-ttu-id="69caf-122">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="69caf-122">**Element**</span></span>|<span data-ttu-id="69caf-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="69caf-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="69caf-124">\<mailSettings>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="69caf-124">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="69caf-125">Konfiguruje opcje wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="69caf-125">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="69caf-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="69caf-126">Example</span></span>  
 <span data-ttu-id="69caf-127">W poniższym przykładzie określono odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu domyślnych poświadczeń sieciowych.</span><span class="sxs-lookup"><span data-stu-id="69caf-127">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="69caf-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69caf-128">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="69caf-129">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="69caf-129">Network Settings Schema</span></span>](index.md)

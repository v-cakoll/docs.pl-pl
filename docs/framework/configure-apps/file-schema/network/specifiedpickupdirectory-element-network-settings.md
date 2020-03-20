---
title: <specifiedPickupDirectory>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: 4b0cbaf9a7bfe2a9b1610811f4201253d219a6b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154611"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="2aaab-102">\<specifiedPickupDirectory> Element (Ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="2aaab-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="2aaab-103">Konfiguruje katalog lokalny dla serwera SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="2aaab-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
<span data-ttu-id="2aaab-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2aaab-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2aaab-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2aaab-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="2aaab-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2aaab-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="2aaab-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>smtp**](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2aaab-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>\
<span data-ttu-id="2aaab-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**</span><span class="sxs-lookup"><span data-stu-id="2aaab-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aaab-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="2aaab-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2aaab-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2aaab-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2aaab-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2aaab-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2aaab-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2aaab-112">Attributes</span></span>  
  
|<span data-ttu-id="2aaab-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2aaab-113">Attribute</span></span>|<span data-ttu-id="2aaab-114">Opis</span><span class="sxs-lookup"><span data-stu-id="2aaab-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="2aaab-115">Katalog, w którym aplikacje zapisują wiadomości e-mail do późniejszego przetwarzania przez serwer SMTP.</span><span class="sxs-lookup"><span data-stu-id="2aaab-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2aaab-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2aaab-116">Child Elements</span></span>  
 <span data-ttu-id="2aaab-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="2aaab-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2aaab-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2aaab-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2aaab-119">Element</span><span class="sxs-lookup"><span data-stu-id="2aaab-119">Element</span></span>|<span data-ttu-id="2aaab-120">Opis</span><span class="sxs-lookup"><span data-stu-id="2aaab-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2aaab-121">\<element> smtp (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="2aaab-121">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="2aaab-122">Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="2aaab-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2aaab-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2aaab-123">Remarks</span></span>  
 <span data-ttu-id="2aaab-124">Atrybut `specifiedPickupDirectory` ustawia katalog, w którym aplikacje zapisują wiadomości e-mail do przetworzenia przez serwer SMTP.</span><span class="sxs-lookup"><span data-stu-id="2aaab-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2aaab-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="2aaab-125">Example</span></span>  
 <span data-ttu-id="2aaab-126">Poniższy przykład określa c:\maildrop jako katalog odbioru poczty.</span><span class="sxs-lookup"><span data-stu-id="2aaab-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="SpecifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2aaab-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2aaab-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="2aaab-128">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="2aaab-128">Network Settings Schema</span></span>](index.md)

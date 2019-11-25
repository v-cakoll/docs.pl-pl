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
ms.openlocfilehash: 1acc724bb14c3610f14d06452c30b3d5dac42e13
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089073"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="53133-102">\<element > specifiedPickupDirectory (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="53133-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="53133-103">Konfiguruje katalog lokalny dla serwera SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="53133-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
<span data-ttu-id="53133-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="53133-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="53133-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="53133-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="53133-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<mailSettings >** ](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="53133-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="53133-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**SMTP**](smtp-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="53133-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>\
<span data-ttu-id="53133-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<specifiedPickupDirectory >**</span><span class="sxs-lookup"><span data-stu-id="53133-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53133-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="53133-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53133-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="53133-110">Attributes and Elements</span></span>  
 <span data-ttu-id="53133-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="53133-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53133-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="53133-112">Attributes</span></span>  
  
|<span data-ttu-id="53133-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="53133-113">Attribute</span></span>|<span data-ttu-id="53133-114">Opis</span><span class="sxs-lookup"><span data-stu-id="53133-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="53133-115">Katalog, w którym aplikacje zapisują wiadomości e-mail w celu późniejszego przetworzenia przez serwer SMTP.</span><span class="sxs-lookup"><span data-stu-id="53133-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53133-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="53133-116">Child Elements</span></span>  
 <span data-ttu-id="53133-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="53133-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53133-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="53133-118">Parent Elements</span></span>  
  
|<span data-ttu-id="53133-119">Element</span><span class="sxs-lookup"><span data-stu-id="53133-119">Element</span></span>|<span data-ttu-id="53133-120">Opis</span><span class="sxs-lookup"><span data-stu-id="53133-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53133-121">\<> SMTP (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="53133-121">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="53133-122">Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="53133-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53133-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="53133-123">Remarks</span></span>  
 <span data-ttu-id="53133-124">Atrybut `specifiedPickupDirectory` określa katalog, w którym aplikacje zapisują wiadomości e-mail, które mają być przetwarzane przez serwer SMTP.</span><span class="sxs-lookup"><span data-stu-id="53133-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53133-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="53133-125">Example</span></span>  
 <span data-ttu-id="53133-126">Poniższy przykład określa c:\maildrop jako katalog podnoszenia poczty.</span><span class="sxs-lookup"><span data-stu-id="53133-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="53133-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53133-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="53133-128">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="53133-128">Network Settings Schema</span></span>](index.md)

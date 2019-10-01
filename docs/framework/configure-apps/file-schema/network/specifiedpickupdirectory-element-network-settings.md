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
ms.openlocfilehash: 47aa357dac8b6bf71ce8c391004af16f8c98e347
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697593"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="3ec9e-102">\<specifiedPickupDirectory >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="3ec9e-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="3ec9e-103">Konfiguruje katalog lokalny dla serwera SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="3ec9e-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[<span data-ttu-id="3ec9e-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="3ec9e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="3ec9e-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3ec9e-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="3ec9e-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<mailSettings >** ](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3ec9e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>  
<span data-ttu-id="3ec9e-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<smtp >** ](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3ec9e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>  
<span data-ttu-id="3ec9e-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 **\<specifiedPickupDirectory >**</span><span class="sxs-lookup"><span data-stu-id="3ec9e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ec9e-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ec9e-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ec9e-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3ec9e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3ec9e-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3ec9e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ec9e-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3ec9e-112">Attributes</span></span>  
  
|<span data-ttu-id="3ec9e-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3ec9e-113">Attribute</span></span>|<span data-ttu-id="3ec9e-114">Opis</span><span class="sxs-lookup"><span data-stu-id="3ec9e-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="3ec9e-115">Katalog, w którym aplikacje zapisują wiadomości e-mail w celu późniejszego przetworzenia przez serwer SMTP.</span><span class="sxs-lookup"><span data-stu-id="3ec9e-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ec9e-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3ec9e-116">Child Elements</span></span>  
 <span data-ttu-id="3ec9e-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="3ec9e-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ec9e-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3ec9e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3ec9e-119">Element</span><span class="sxs-lookup"><span data-stu-id="3ec9e-119">Element</span></span>|<span data-ttu-id="3ec9e-120">Opis</span><span class="sxs-lookup"><span data-stu-id="3ec9e-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3ec9e-121">\<smtp >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="3ec9e-121">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="3ec9e-122">Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="3ec9e-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ec9e-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ec9e-123">Remarks</span></span>  
 <span data-ttu-id="3ec9e-124">Atrybut `specifiedPickupDirectory` ustawia katalog, w którym aplikacje zapisują wiadomości e-mail, które mają być przetwarzane przez serwer SMTP.</span><span class="sxs-lookup"><span data-stu-id="3ec9e-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ec9e-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ec9e-125">Example</span></span>  
 <span data-ttu-id="3ec9e-126">Poniższy przykład określa c:\maildrop jako katalog podnoszenia poczty.</span><span class="sxs-lookup"><span data-stu-id="3ec9e-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3ec9e-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ec9e-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="3ec9e-128">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="3ec9e-128">Network Settings Schema</span></span>](index.md)

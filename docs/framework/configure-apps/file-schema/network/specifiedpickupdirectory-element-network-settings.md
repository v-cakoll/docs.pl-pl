---
title: <specifiedPickupDirectory>, element (ustawienia sieci)
description: <specifiedPickupDirectory>Element ustawienia sieci konfiguruje katalog lokalny dla opcji serwera SMTP w .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: f0c4c1845e9542d0f3b836ff03f16bdf2979ebd8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504501"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="8b9d2-103">\<specifiedPickupDirectory>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="8b9d2-103">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="8b9d2-104">Konfiguruje katalog lokalny dla serwera SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="8b9d2-104">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**  
  
## <a name="syntax"></a><span data-ttu-id="8b9d2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b9d2-105">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b9d2-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8b9d2-106">Attributes and Elements</span></span>  
 <span data-ttu-id="8b9d2-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8b9d2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b9d2-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8b9d2-108">Attributes</span></span>  
  
|<span data-ttu-id="8b9d2-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8b9d2-109">Attribute</span></span>|<span data-ttu-id="8b9d2-110">Opis</span><span class="sxs-lookup"><span data-stu-id="8b9d2-110">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="8b9d2-111">Katalog, w którym aplikacje zapisują wiadomości e-mail w celu późniejszego przetworzenia przez serwer SMTP.</span><span class="sxs-lookup"><span data-stu-id="8b9d2-111">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b9d2-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8b9d2-112">Child Elements</span></span>  
 <span data-ttu-id="8b9d2-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="8b9d2-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b9d2-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8b9d2-114">Parent Elements</span></span>  
  
|<span data-ttu-id="8b9d2-115">Element</span><span class="sxs-lookup"><span data-stu-id="8b9d2-115">Element</span></span>|<span data-ttu-id="8b9d2-116">Opis</span><span class="sxs-lookup"><span data-stu-id="8b9d2-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b9d2-117">\<smtp>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="8b9d2-117">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="8b9d2-118">Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="8b9d2-118">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b9d2-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8b9d2-119">Remarks</span></span>  
 <span data-ttu-id="8b9d2-120">Ten `specifiedPickupDirectory` atrybut określa katalog, w którym aplikacje zapisują wiadomości e-mail, które mają być przetwarzane przez serwer SMTP.</span><span class="sxs-lookup"><span data-stu-id="8b9d2-120">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b9d2-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="8b9d2-121">Example</span></span>  
 <span data-ttu-id="8b9d2-122">Poniższy przykład określa c:\maildrop jako katalog podnoszenia poczty.</span><span class="sxs-lookup"><span data-stu-id="8b9d2-122">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8b9d2-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b9d2-123">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="8b9d2-124">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="8b9d2-124">Network Settings Schema</span></span>](index.md)

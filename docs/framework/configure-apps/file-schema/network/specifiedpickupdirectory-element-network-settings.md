---
title: '&lt;specifiedPickupDirectory&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 50ab7387fc5e2cac65cac1a6dba0e563225beec9
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874705"
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="b0cf1-102">&lt;specifiedPickupDirectory&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="b0cf1-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="b0cf1-103">Konfiguruje katalog lokalny dla serwera transportu protokołu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="b0cf1-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="b0cf1-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="b0cf1-104">\<configuration></span></span>  
<span data-ttu-id="b0cf1-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="b0cf1-105">\<system.net></span></span>  
<span data-ttu-id="b0cf1-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="b0cf1-106">\<mailSettings></span></span>  
<span data-ttu-id="b0cf1-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="b0cf1-107">\<smtp></span></span>  
<span data-ttu-id="b0cf1-108">\<specifiedPickupDirectory></span><span class="sxs-lookup"><span data-stu-id="b0cf1-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0cf1-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="b0cf1-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b0cf1-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b0cf1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b0cf1-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b0cf1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b0cf1-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b0cf1-112">Attributes</span></span>  
  
|<span data-ttu-id="b0cf1-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b0cf1-113">Attribute</span></span>|<span data-ttu-id="b0cf1-114">Opis</span><span class="sxs-lookup"><span data-stu-id="b0cf1-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="b0cf1-115">Katalog, w których aplikacje zapisać wiadomość e-mail do późniejszego przetwarzania przez serwer SMTP.</span><span class="sxs-lookup"><span data-stu-id="b0cf1-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b0cf1-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b0cf1-116">Child Elements</span></span>  
 <span data-ttu-id="b0cf1-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="b0cf1-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b0cf1-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b0cf1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b0cf1-119">Element</span><span class="sxs-lookup"><span data-stu-id="b0cf1-119">Element</span></span>|<span data-ttu-id="b0cf1-120">Opis</span><span class="sxs-lookup"><span data-stu-id="b0cf1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b0cf1-121">\<SMTP >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="b0cf1-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="b0cf1-122">Konfiguruje opcje wysyłania poczty transportu protokołu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="b0cf1-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0cf1-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0cf1-123">Remarks</span></span>  
 <span data-ttu-id="b0cf1-124">`specifiedPickupDirectory` Atrybut Ustawia katalog oszczędzić wiadomości e-mail do przetworzenia przez serwer SMTP w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b0cf1-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0cf1-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="b0cf1-125">Example</span></span>  
 <span data-ttu-id="b0cf1-126">W poniższym przykładzie określono c:\maildrop jako katalog podnoszenia poczty.</span><span class="sxs-lookup"><span data-stu-id="b0cf1-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b0cf1-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0cf1-127">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [<span data-ttu-id="b0cf1-128">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="b0cf1-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

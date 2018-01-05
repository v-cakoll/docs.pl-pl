---
title: "&lt;specifiedpickupdirectory —&gt; — Element (ustawienia sieciowe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0df8cb46943862e3de66faa5551f550cb232f212
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="18775-102">&lt;specifiedpickupdirectory —&gt; — Element (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="18775-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="18775-103">Konfiguruje katalogu lokalnego dla serwera transportu protokołu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="18775-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="18775-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="18775-104">\<configuration></span></span>  
<span data-ttu-id="18775-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="18775-105">\<system.net></span></span>  
<span data-ttu-id="18775-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="18775-106">\<mailSettings></span></span>  
<span data-ttu-id="18775-107">\<SMTP ></span><span class="sxs-lookup"><span data-stu-id="18775-107">\<smtp></span></span>  
<span data-ttu-id="18775-108">\<specifiedpickupdirectory — ></span><span class="sxs-lookup"><span data-stu-id="18775-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18775-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="18775-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18775-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="18775-110">Attributes and Elements</span></span>  
 <span data-ttu-id="18775-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="18775-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18775-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="18775-112">Attributes</span></span>  
  
|<span data-ttu-id="18775-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="18775-113">Attribute</span></span>|<span data-ttu-id="18775-114">Opis</span><span class="sxs-lookup"><span data-stu-id="18775-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="18775-115">Katalog, w którym aplikacje zapisać wiadomości e-mail dalej przetwarzane przez serwer SMTP.</span><span class="sxs-lookup"><span data-stu-id="18775-115">The directory where applications save e-mail for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18775-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="18775-116">Child Elements</span></span>  
 <span data-ttu-id="18775-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="18775-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18775-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="18775-118">Parent Elements</span></span>  
  
|<span data-ttu-id="18775-119">Element</span><span class="sxs-lookup"><span data-stu-id="18775-119">Element</span></span>|<span data-ttu-id="18775-120">Opis</span><span class="sxs-lookup"><span data-stu-id="18775-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18775-121">\<SMTP > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="18775-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="18775-122">Konfiguruje opcje wysyłania poczty transportu protokołu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="18775-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18775-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="18775-123">Remarks</span></span>  
 <span data-ttu-id="18775-124">`specifiedPickupDirectory` Atrybut Ustawia katalog, w którym aplikacje zapisać wiadomości do przetworzenia przez serwer SMTP.</span><span class="sxs-lookup"><span data-stu-id="18775-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18775-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="18775-125">Example</span></span>  
 <span data-ttu-id="18775-126">W poniższym przykładzie c:\maildrop jako katalog podnoszenia poczty.</span><span class="sxs-lookup"><span data-stu-id="18775-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="specifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="18775-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="18775-127">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>  
 [<span data-ttu-id="18775-128">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="18775-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

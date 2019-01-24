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
ms.openlocfilehash: 7735aea55f03b0703ebb7b0e3c5f958b57f1238d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611309"
---
# <a name="ltspecifiedpickupdirectorygt-element-network-settings"></a><span data-ttu-id="05f5c-102">&lt;specifiedPickupDirectory&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="05f5c-102">&lt;specifiedPickupDirectory&gt; Element (Network Settings)</span></span>
<span data-ttu-id="05f5c-103">Konfiguruje katalog lokalny dla serwera transportu protokołu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="05f5c-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="05f5c-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="05f5c-104">\<configuration></span></span>  
<span data-ttu-id="05f5c-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="05f5c-105">\<system.net></span></span>  
<span data-ttu-id="05f5c-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="05f5c-106">\<mailSettings></span></span>  
<span data-ttu-id="05f5c-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="05f5c-107">\<smtp></span></span>  
<span data-ttu-id="05f5c-108">\<specifiedPickupDirectory></span><span class="sxs-lookup"><span data-stu-id="05f5c-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05f5c-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="05f5c-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05f5c-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="05f5c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="05f5c-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="05f5c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05f5c-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="05f5c-112">Attributes</span></span>  
  
|<span data-ttu-id="05f5c-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="05f5c-113">Attribute</span></span>|<span data-ttu-id="05f5c-114">Opis</span><span class="sxs-lookup"><span data-stu-id="05f5c-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="05f5c-115">Katalog, w których aplikacje zapisać wiadomość e-mail do późniejszego przetwarzania przez serwer SMTP.</span><span class="sxs-lookup"><span data-stu-id="05f5c-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05f5c-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="05f5c-116">Child Elements</span></span>  
 <span data-ttu-id="05f5c-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="05f5c-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05f5c-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="05f5c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="05f5c-119">Element</span><span class="sxs-lookup"><span data-stu-id="05f5c-119">Element</span></span>|<span data-ttu-id="05f5c-120">Opis</span><span class="sxs-lookup"><span data-stu-id="05f5c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05f5c-121">\<SMTP >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="05f5c-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="05f5c-122">Konfiguruje opcje wysyłania poczty transportu protokołu SMTP (Simple Mail).</span><span class="sxs-lookup"><span data-stu-id="05f5c-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05f5c-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05f5c-123">Remarks</span></span>  
 <span data-ttu-id="05f5c-124">`specifiedPickupDirectory` Atrybut Ustawia katalog oszczędzić wiadomości e-mail do przetworzenia przez serwer SMTP w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="05f5c-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05f5c-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="05f5c-125">Example</span></span>  
 <span data-ttu-id="05f5c-126">W poniższym przykładzie określono c:\maildrop jako katalog podnoszenia poczty.</span><span class="sxs-lookup"><span data-stu-id="05f5c-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05f5c-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05f5c-127">See also</span></span>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="05f5c-128">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="05f5c-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

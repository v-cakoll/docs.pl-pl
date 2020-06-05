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
ms.sourcegitcommit: 0a798a7e9680e2d0a5a81a3eaa203870ea782883
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/03/2020
ms.locfileid: "79154611"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="07025-102">\<specifiedPickupDirectory>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="07025-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="07025-103">Konfiguruje katalog lokalny dla serwera SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="07025-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**  
  
## <a name="syntax"></a><span data-ttu-id="07025-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="07025-104">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07025-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="07025-105">Attributes and Elements</span></span>  
 <span data-ttu-id="07025-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="07025-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07025-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="07025-107">Attributes</span></span>  
  
|<span data-ttu-id="07025-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="07025-108">Attribute</span></span>|<span data-ttu-id="07025-109">Opis</span><span class="sxs-lookup"><span data-stu-id="07025-109">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="07025-110">Katalog, w którym aplikacje zapisują wiadomości e-mail w celu późniejszego przetworzenia przez serwer SMTP.</span><span class="sxs-lookup"><span data-stu-id="07025-110">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07025-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="07025-111">Child Elements</span></span>  
 <span data-ttu-id="07025-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="07025-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="07025-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="07025-113">Parent Elements</span></span>  
  
|<span data-ttu-id="07025-114">Element</span><span class="sxs-lookup"><span data-stu-id="07025-114">Element</span></span>|<span data-ttu-id="07025-115">Opis</span><span class="sxs-lookup"><span data-stu-id="07025-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07025-116">\<smtp>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="07025-116">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="07025-117">Konfiguruje opcje wysyłania poczty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="07025-117">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07025-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="07025-118">Remarks</span></span>  
 <span data-ttu-id="07025-119">Ten `specifiedPickupDirectory` atrybut określa katalog, w którym aplikacje zapisują wiadomości e-mail, które mają być przetwarzane przez serwer SMTP.</span><span class="sxs-lookup"><span data-stu-id="07025-119">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07025-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="07025-120">Example</span></span>  
 <span data-ttu-id="07025-121">Poniższy przykład określa c:\maildrop jako katalog podnoszenia poczty.</span><span class="sxs-lookup"><span data-stu-id="07025-121">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="07025-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07025-122">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="07025-123">Schemat ustawień sieciowych</span><span class="sxs-lookup"><span data-stu-id="07025-123">Network Settings Schema</span></span>](index.md)

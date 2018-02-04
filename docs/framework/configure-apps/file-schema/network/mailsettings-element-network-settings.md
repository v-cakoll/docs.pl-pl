---
title: '&lt;mailSettings&gt; elementu (ustawienia sieciowe)'
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: ce7ec8bea57436ebd184cf0d593870999405f72f
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="e229d-102">&lt;mailSettings&gt; elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="e229d-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="e229d-103">Konfiguruje opcje wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="e229d-103">Configures mail sending options.</span></span>  

<span data-ttu-id="e229d-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e229d-104">\<configuration></span></span>  
<span data-ttu-id="e229d-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="e229d-105">\<system.net></span></span>  
<span data-ttu-id="e229d-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="e229d-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e229d-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e229d-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e229d-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e229d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e229d-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e229d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e229d-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e229d-110">Attributes</span></span>  
 <span data-ttu-id="e229d-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="e229d-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e229d-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e229d-112">Child Elements</span></span>  
  
|<span data-ttu-id="e229d-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e229d-113">Attribute</span></span>|<span data-ttu-id="e229d-114">Opis</span><span class="sxs-lookup"><span data-stu-id="e229d-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="e229d-115">\<SMTP > elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="e229d-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="e229d-116">Służy do konfigurowania opcji prostego protokołu transportu poczty.</span><span class="sxs-lookup"><span data-stu-id="e229d-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e229d-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e229d-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e229d-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="e229d-118">**Element**</span></span>|<span data-ttu-id="e229d-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e229d-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e229d-120">\<system.Net > (ustawienia sieciowe) — Element</span><span class="sxs-lookup"><span data-stu-id="e229d-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="e229d-121">Zawiera ustawienia, które określają sposób programu .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="e229d-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e229d-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="e229d-122">Example</span></span>  
 <span data-ttu-id="e229d-123">W poniższym przykładzie odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu poświadczeń domyślnych w sieci.</span><span class="sxs-lookup"><span data-stu-id="e229d-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network">  
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
  
## <a name="see-also"></a><span data-ttu-id="e229d-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e229d-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="e229d-125">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="e229d-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

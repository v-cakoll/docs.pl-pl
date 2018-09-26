---
title: '&lt;mailSettings&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f3a706edaeba551139368568a7467e0cdab3524c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171611"
---
# <a name="ltmailsettingsgt-element-network-settings"></a><span data-ttu-id="4a805-102">&lt;mailSettings&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="4a805-102">&lt;mailSettings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="4a805-103">Konfiguruje opcje wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="4a805-103">Configures mail sending options.</span></span>  

<span data-ttu-id="4a805-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="4a805-104">\<configuration></span></span>  
<span data-ttu-id="4a805-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="4a805-105">\<system.net></span></span>  
<span data-ttu-id="4a805-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="4a805-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a805-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a805-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp> … </smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a805-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4a805-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4a805-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4a805-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a805-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4a805-110">Attributes</span></span>  
 <span data-ttu-id="4a805-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="4a805-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4a805-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4a805-112">Child Elements</span></span>  
  
|<span data-ttu-id="4a805-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4a805-113">Attribute</span></span>|<span data-ttu-id="4a805-114">Opis</span><span class="sxs-lookup"><span data-stu-id="4a805-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="4a805-115">\<SMTP >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="4a805-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="4a805-116">Służy do konfigurowania opcji prostego protokołu transportowego poczty.</span><span class="sxs-lookup"><span data-stu-id="4a805-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a805-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4a805-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4a805-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="4a805-118">**Element**</span></span>|<span data-ttu-id="4a805-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4a805-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4a805-120">\<przestrzeni nazw system.Net >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="4a805-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="4a805-121">Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="4a805-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4a805-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a805-122">Example</span></span>  
 <span data-ttu-id="4a805-123">Poniższy przykład określa odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu poświadczeń domyślnych sieci.</span><span class="sxs-lookup"><span data-stu-id="4a805-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
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
  
## <a name="see-also"></a><span data-ttu-id="4a805-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a805-124">See Also</span></span>  
 <xref:System.Net.Mail.SmtpClient>  
 [<span data-ttu-id="4a805-125">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="4a805-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

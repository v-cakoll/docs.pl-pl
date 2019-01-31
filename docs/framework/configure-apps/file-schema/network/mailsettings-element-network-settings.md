---
title: <mailSettings> — Element (Ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: 0e71284e914dac2d28448f3d8bd4bdc7a9f6b325
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277618"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="15672-102">\<mailSettings — >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="15672-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="15672-103">Konfiguruje opcje wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="15672-103">Configures mail sending options.</span></span>  

<span data-ttu-id="15672-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="15672-104">\<configuration></span></span>  
<span data-ttu-id="15672-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="15672-105">\<system.net></span></span>  
<span data-ttu-id="15672-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="15672-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15672-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="15672-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15672-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="15672-108">Attributes and Elements</span></span>  
 <span data-ttu-id="15672-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="15672-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15672-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="15672-110">Attributes</span></span>  
 <span data-ttu-id="15672-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="15672-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="15672-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="15672-112">Child Elements</span></span>  
  
|<span data-ttu-id="15672-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="15672-113">Attribute</span></span>|<span data-ttu-id="15672-114">Opis</span><span class="sxs-lookup"><span data-stu-id="15672-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="15672-115">\<SMTP >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="15672-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="15672-116">Służy do konfigurowania opcji prostego protokołu transportowego poczty.</span><span class="sxs-lookup"><span data-stu-id="15672-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="15672-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="15672-117">Parent Elements</span></span>  
  
|<span data-ttu-id="15672-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="15672-118">**Element**</span></span>|<span data-ttu-id="15672-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="15672-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="15672-120">\<przestrzeni nazw system.Net >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="15672-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="15672-121">Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="15672-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="15672-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="15672-122">Example</span></span>  
 <span data-ttu-id="15672-123">Poniższy przykład określa odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu poświadczeń domyślnych sieci.</span><span class="sxs-lookup"><span data-stu-id="15672-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="15672-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15672-124">See also</span></span>
- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="15672-125">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="15672-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

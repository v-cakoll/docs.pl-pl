---
title: <mailSettings> Element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: 54fb68ab0bf8aa2665d70391350c626131ccb4bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180633"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="99c53-102">\<mailSettings — >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="99c53-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="99c53-103">Konfiguruje opcje wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="99c53-103">Configures mail sending options.</span></span>  

<span data-ttu-id="99c53-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="99c53-104">\<configuration></span></span>  
<span data-ttu-id="99c53-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="99c53-105">\<system.net></span></span>  
<span data-ttu-id="99c53-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="99c53-106">\<mailSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99c53-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="99c53-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99c53-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="99c53-108">Attributes and Elements</span></span>  
 <span data-ttu-id="99c53-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="99c53-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99c53-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="99c53-110">Attributes</span></span>  
 <span data-ttu-id="99c53-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="99c53-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="99c53-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="99c53-112">Child Elements</span></span>  
  
|<span data-ttu-id="99c53-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="99c53-113">Attribute</span></span>|<span data-ttu-id="99c53-114">Opis</span><span class="sxs-lookup"><span data-stu-id="99c53-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="99c53-115">\<SMTP >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="99c53-115">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="99c53-116">Służy do konfigurowania opcji prostego protokołu transportowego poczty.</span><span class="sxs-lookup"><span data-stu-id="99c53-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99c53-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="99c53-117">Parent Elements</span></span>  
  
|**<span data-ttu-id="99c53-118">Element</span><span class="sxs-lookup"><span data-stu-id="99c53-118">Element</span></span>**|**<span data-ttu-id="99c53-119">Opis</span><span class="sxs-lookup"><span data-stu-id="99c53-119">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="99c53-120">\<przestrzeni nazw system.Net >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="99c53-120">\<system.Net> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="99c53-121">Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="99c53-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="99c53-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="99c53-122">Example</span></span>  
 <span data-ttu-id="99c53-123">Poniższy przykład określa odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu poświadczeń domyślnych sieci.</span><span class="sxs-lookup"><span data-stu-id="99c53-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="99c53-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99c53-124">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="99c53-125">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="99c53-125">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

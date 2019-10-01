---
title: <mailSettings>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: fb4c8844ed3eb13af483c214d659090c0c563c33
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698079"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="ebd17-102">\<mailSettings >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="ebd17-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="ebd17-103">Konfiguruje opcje wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="ebd17-103">Configures mail sending options.</span></span>  

[<span data-ttu-id="ebd17-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="ebd17-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="ebd17-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ebd17-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="ebd17-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<mailSettings >**</span><span class="sxs-lookup"><span data-stu-id="ebd17-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebd17-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ebd17-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ebd17-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ebd17-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ebd17-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ebd17-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ebd17-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ebd17-110">Attributes</span></span>  
 <span data-ttu-id="ebd17-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="ebd17-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ebd17-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ebd17-112">Child Elements</span></span>  
  
|<span data-ttu-id="ebd17-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ebd17-113">Attribute</span></span>|<span data-ttu-id="ebd17-114">Opis</span><span class="sxs-lookup"><span data-stu-id="ebd17-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="ebd17-115">\<smtp >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="ebd17-115">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="ebd17-116">Konfiguruje opcje protokołu Simple Mail Transport.</span><span class="sxs-lookup"><span data-stu-id="ebd17-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ebd17-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ebd17-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ebd17-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="ebd17-118">**Element**</span></span>|<span data-ttu-id="ebd17-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="ebd17-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ebd17-120">\<System .net >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="ebd17-120">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="ebd17-121">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="ebd17-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ebd17-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="ebd17-122">Example</span></span>  
 <span data-ttu-id="ebd17-123">W poniższym przykładzie określono odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu domyślnych poświadczeń sieciowych.</span><span class="sxs-lookup"><span data-stu-id="ebd17-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ebd17-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebd17-124">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="ebd17-125">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="ebd17-125">Network Settings Schema</span></span>](index.md)

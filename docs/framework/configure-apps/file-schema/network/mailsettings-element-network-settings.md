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
ms.openlocfilehash: 4e8bf23ce39edadf80f019315c690b597b3d7361
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089232"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="cf1d6-102">\<element > mailSettings (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="cf1d6-102">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="cf1d6-103">Konfiguruje opcje wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="cf1d6-103">Configures mail sending options.</span></span>  

<span data-ttu-id="cf1d6-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="cf1d6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cf1d6-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="cf1d6-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="cf1d6-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<mailSettings >**</span><span class="sxs-lookup"><span data-stu-id="cf1d6-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**</span></span>

## <a name="syntax"></a><span data-ttu-id="cf1d6-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf1d6-107">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf1d6-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cf1d6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="cf1d6-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cf1d6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf1d6-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cf1d6-110">Attributes</span></span>  
 <span data-ttu-id="cf1d6-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="cf1d6-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cf1d6-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cf1d6-112">Child Elements</span></span>  
  
|<span data-ttu-id="cf1d6-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cf1d6-113">Attribute</span></span>|<span data-ttu-id="cf1d6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="cf1d6-114">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="cf1d6-115">\<> SMTP (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="cf1d6-115">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="cf1d6-116">Konfiguruje opcje protokołu Simple Mail Transport.</span><span class="sxs-lookup"><span data-stu-id="cf1d6-116">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cf1d6-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cf1d6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="cf1d6-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="cf1d6-118">**Element**</span></span>|<span data-ttu-id="cf1d6-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="cf1d6-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cf1d6-120">\<system .net >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="cf1d6-120">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="cf1d6-121">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="cf1d6-121">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="cf1d6-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf1d6-122">Example</span></span>  
 <span data-ttu-id="cf1d6-123">W poniższym przykładzie określono odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu domyślnych poświadczeń sieciowych.</span><span class="sxs-lookup"><span data-stu-id="cf1d6-123">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cf1d6-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf1d6-124">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="cf1d6-125">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="cf1d6-125">Network Settings Schema</span></span>](index.md)

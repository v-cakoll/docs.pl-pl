---
title: <mailSettings>, element (ustawienia sieci)
description: <mailSettings>Element ustawienia sieci konfiguruje opcje wysyłania poczty w .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: ce7b8564e4ee5ea73d42259612c077420d36645b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504566"
---
# <a name="mailsettings-element-network-settings"></a><span data-ttu-id="89d8b-103">\<mailSettings>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="89d8b-103">\<mailSettings> Element (Network Settings)</span></span>
<span data-ttu-id="89d8b-104">Konfiguruje opcje wysyłania poczty.</span><span class="sxs-lookup"><span data-stu-id="89d8b-104">Configures mail sending options.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<mailSettings>**

## <a name="syntax"></a><span data-ttu-id="89d8b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="89d8b-105">Syntax</span></span>  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89d8b-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="89d8b-106">Attributes and Elements</span></span>  
 <span data-ttu-id="89d8b-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="89d8b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89d8b-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="89d8b-108">Attributes</span></span>  
 <span data-ttu-id="89d8b-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="89d8b-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="89d8b-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="89d8b-110">Child Elements</span></span>  
  
|<span data-ttu-id="89d8b-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="89d8b-111">Attribute</span></span>|<span data-ttu-id="89d8b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="89d8b-112">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="89d8b-113">\<smtp>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="89d8b-113">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="89d8b-114">Konfiguruje opcje protokołu Simple Mail Transport.</span><span class="sxs-lookup"><span data-stu-id="89d8b-114">Configures Simple Mail Transport Protocol options.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="89d8b-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="89d8b-115">Parent Elements</span></span>  
  
|<span data-ttu-id="89d8b-116">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="89d8b-116">**Element**</span></span>|<span data-ttu-id="89d8b-117">**Opis**</span><span class="sxs-lookup"><span data-stu-id="89d8b-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="89d8b-118">\<system.Net>— Element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="89d8b-118">\<system.Net> Element (Network Settings)</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="89d8b-119">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="89d8b-119">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="89d8b-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="89d8b-120">Example</span></span>  
 <span data-ttu-id="89d8b-121">W poniższym przykładzie określono odpowiednie parametry SMTP do wysyłania wiadomości e-mail przy użyciu domyślnych poświadczeń sieciowych.</span><span class="sxs-lookup"><span data-stu-id="89d8b-121">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="89d8b-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89d8b-122">See also</span></span>

- <xref:System.Net.Mail.SmtpClient>
- [<span data-ttu-id="89d8b-123">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="89d8b-123">Network Settings Schema</span></span>](index.md)

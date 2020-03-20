---
title: <remove>, element dla connectionManagement (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
ms.openlocfilehash: 39ce85c3c15a2d4bdfce801a35e9ca088bd5091b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154741"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="48098-102">\<usuń> element dla połączeniaManagement (Ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="48098-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="48098-103">Usuwa adres IP lub nazwę DNS z listy zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="48098-103">Removes an IP address or DNS name from the connection management list.</span></span>  

<span data-ttu-id="48098-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="48098-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="48098-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="48098-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="48098-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="48098-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>\
<span data-ttu-id="48098-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<usuń>**</span><span class="sxs-lookup"><span data-stu-id="48098-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="48098-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="48098-108">Syntax</span></span>  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48098-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="48098-109">Attributes and Elements</span></span>  
 <span data-ttu-id="48098-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="48098-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48098-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="48098-111">Attributes</span></span>  
  
|<span data-ttu-id="48098-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="48098-112">**Attribute**</span></span>|<span data-ttu-id="48098-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="48098-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="48098-114">Adres IP lub nazwa DNS.</span><span class="sxs-lookup"><span data-stu-id="48098-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48098-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="48098-115">Child Elements</span></span>  
 <span data-ttu-id="48098-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="48098-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="48098-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="48098-117">Parent Elements</span></span>  
  
|<span data-ttu-id="48098-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="48098-118">**Element**</span></span>|<span data-ttu-id="48098-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="48098-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="48098-120">connectionManagement (PołączenieManagement)</span><span class="sxs-lookup"><span data-stu-id="48098-120">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="48098-121">Określa maksymalną liczbę połączeń z hostem sieciowym.</span><span class="sxs-lookup"><span data-stu-id="48098-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48098-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="48098-122">Remarks</span></span>  
 <span data-ttu-id="48098-123">Element `remove` usuwa wpis listy zarządzania połączeniami dla określonego serwera.</span><span class="sxs-lookup"><span data-stu-id="48098-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="48098-124">Wartość atrybutu `address` powinna być prawidłowym adresem IP lub nazwą hosta.</span><span class="sxs-lookup"><span data-stu-id="48098-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="48098-125">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="48098-125">Configuration Files</span></span>  
 <span data-ttu-id="48098-126">Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="48098-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="48098-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="48098-127">Example</span></span>  
 <span data-ttu-id="48098-128">Poniższy przykład usuwa wszystkie wpisy listy `www.adventure-works.com` zarządzania połączeniami dla serwera, a następnie `www.contoso.com` konfiguruje aplikację do używania czterech połączeń z serwerem i dwóch połączeń ze wszystkimi innymi serwerami.</span><span class="sxs-lookup"><span data-stu-id="48098-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address="http://www.adventure-works.com" />  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="48098-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48098-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="48098-130">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="48098-130">Network Settings Schema</span></span>](index.md)

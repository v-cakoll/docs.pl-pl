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
ms.openlocfilehash: cbafd29be6855cbb95d17388791ba152230295cc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697843"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="22c30-102">\<remove > elementu connectionManagement (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="22c30-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="22c30-103">Usuwa adres IP lub nazwę DNS z listy zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="22c30-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
[<span data-ttu-id="22c30-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="22c30-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="22c30-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="22c30-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="22c30-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="22c30-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>  
<span data-ttu-id="22c30-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="22c30-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22c30-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="22c30-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22c30-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="22c30-109">Attributes and Elements</span></span>  
 <span data-ttu-id="22c30-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="22c30-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22c30-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="22c30-111">Attributes</span></span>  
  
|<span data-ttu-id="22c30-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="22c30-112">**Attribute**</span></span>|<span data-ttu-id="22c30-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="22c30-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="22c30-114">Adres IP lub nazwa DNS.</span><span class="sxs-lookup"><span data-stu-id="22c30-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22c30-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="22c30-115">Child Elements</span></span>  
 <span data-ttu-id="22c30-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="22c30-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="22c30-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="22c30-117">Parent Elements</span></span>  
  
|<span data-ttu-id="22c30-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="22c30-118">**Element**</span></span>|<span data-ttu-id="22c30-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="22c30-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="22c30-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="22c30-120">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="22c30-121">Określa maksymalną liczbę połączeń z hostem sieciowym.</span><span class="sxs-lookup"><span data-stu-id="22c30-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22c30-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="22c30-122">Remarks</span></span>  
 <span data-ttu-id="22c30-123">Element `remove` usuwa wpis listy zarządzania połączeniami dla określonego serwera.</span><span class="sxs-lookup"><span data-stu-id="22c30-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="22c30-124">Wartość atrybutu `address` powinna być prawidłowym adresem IP lub nazwą hosta.</span><span class="sxs-lookup"><span data-stu-id="22c30-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="22c30-125">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="22c30-125">Configuration Files</span></span>  
 <span data-ttu-id="22c30-126">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="22c30-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="22c30-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="22c30-127">Example</span></span>  
 <span data-ttu-id="22c30-128">Poniższy przykład usuwa wszystkie wpisy listy zarządzania połączeniami dla serwera `www.adventure-works.com`, a następnie konfiguruje aplikację do używania czterech połączeń z serwerem `www.contoso.com` i dwoma połączeniami z innymi serwerami.</span><span class="sxs-lookup"><span data-stu-id="22c30-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="22c30-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="22c30-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="22c30-130">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="22c30-130">Network Settings Schema</span></span>](index.md)

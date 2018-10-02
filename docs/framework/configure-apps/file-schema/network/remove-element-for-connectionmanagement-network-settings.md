---
title: '&lt;Usuń&gt; Element dla connectionManagement (ustawienia sieci)'
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d249cc412a1638e62b57b4976adc23fdf8f36e80
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48024587"
---
# <a name="ltremovegt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="f3a40-102">&lt;Usuń&gt; Element dla connectionManagement (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="f3a40-102">&lt;remove&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="f3a40-103">Usuwa adres IP lub nazwę DNS na liście zarządzania połączenia.</span><span class="sxs-lookup"><span data-stu-id="f3a40-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
 <span data-ttu-id="f3a40-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="f3a40-104">\<configuration></span></span>  
<span data-ttu-id="f3a40-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f3a40-105">\<system.net></span></span>  
<span data-ttu-id="f3a40-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="f3a40-106">\<connectionManagement></span></span>  
<span data-ttu-id="f3a40-107">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="f3a40-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3a40-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3a40-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3a40-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f3a40-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f3a40-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f3a40-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3a40-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f3a40-111">Attributes</span></span>  
  
|<span data-ttu-id="f3a40-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="f3a40-112">**Attribute**</span></span>|<span data-ttu-id="f3a40-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f3a40-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="f3a40-114">Adres IP lub nazwę DNS.</span><span class="sxs-lookup"><span data-stu-id="f3a40-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3a40-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f3a40-115">Child Elements</span></span>  
 <span data-ttu-id="f3a40-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="f3a40-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3a40-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f3a40-117">Parent Elements</span></span>  
  
|<span data-ttu-id="f3a40-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="f3a40-118">**Element**</span></span>|<span data-ttu-id="f3a40-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f3a40-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f3a40-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="f3a40-120">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="f3a40-121">Określa maksymalną liczbę połączeń z hostem sieci.</span><span class="sxs-lookup"><span data-stu-id="f3a40-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3a40-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3a40-122">Remarks</span></span>  
 <span data-ttu-id="f3a40-123">`remove` Elementu usuwa wpis listy zarządzania połączenia dla określonego serwera.</span><span class="sxs-lookup"><span data-stu-id="f3a40-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="f3a40-124">Wartość `address` atrybut powinien być prawidłową nazwą hosta lub adres IP.</span><span class="sxs-lookup"><span data-stu-id="f3a40-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f3a40-125">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f3a40-125">Configuration Files</span></span>  
 <span data-ttu-id="f3a40-126">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="f3a40-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3a40-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3a40-127">Example</span></span>  
 <span data-ttu-id="f3a40-128">Poniższy przykład usuwa żadnych połączeń zarządzania wpisów na liście www.adventure-works.com serwera, a następnie konfiguruje aplikację do korzystania z czterech połączeń www.contoso.com serwera i dwóch połączeń na inne serwery.</span><span class="sxs-lookup"><span data-stu-id="f3a40-128">The following example removes any connection management list entries for the server www.adventure-works.com and then configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3a40-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f3a40-129">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="f3a40-130">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="f3a40-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

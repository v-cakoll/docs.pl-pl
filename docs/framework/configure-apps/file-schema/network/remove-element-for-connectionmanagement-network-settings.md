---
title: '&lt;Usuń&gt; elementu connectionmanagement — (ustawienia sieciowe)'
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
manager: markl
ms.openlocfilehash: 8d503e06139fc6ce14f4d2c50c46e4bcfeb1b860
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltremovegt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="53dcd-102">&lt;Usuń&gt; elementu connectionmanagement — (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="53dcd-102">&lt;remove&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="53dcd-103">Usuwa adres IP lub nazwa DNS z listy zarządzania połączenia.</span><span class="sxs-lookup"><span data-stu-id="53dcd-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
 <span data-ttu-id="53dcd-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="53dcd-104">\<configuration></span></span>  
<span data-ttu-id="53dcd-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="53dcd-105">\<system.net></span></span>  
<span data-ttu-id="53dcd-106">\<connectionmanagement — ></span><span class="sxs-lookup"><span data-stu-id="53dcd-106">\<connectionManagement></span></span>  
<span data-ttu-id="53dcd-107">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="53dcd-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53dcd-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="53dcd-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53dcd-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="53dcd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="53dcd-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="53dcd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53dcd-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="53dcd-111">Attributes</span></span>  
  
|<span data-ttu-id="53dcd-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="53dcd-112">**Attribute**</span></span>|<span data-ttu-id="53dcd-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="53dcd-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="53dcd-114">Adres IP lub nazwę DNS.</span><span class="sxs-lookup"><span data-stu-id="53dcd-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53dcd-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="53dcd-115">Child Elements</span></span>  
 <span data-ttu-id="53dcd-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="53dcd-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53dcd-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="53dcd-117">Parent Elements</span></span>  
  
|<span data-ttu-id="53dcd-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="53dcd-118">**Element**</span></span>|<span data-ttu-id="53dcd-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="53dcd-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="53dcd-120">connectionmanagement —</span><span class="sxs-lookup"><span data-stu-id="53dcd-120">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="53dcd-121">Określa maksymalną liczbę połączeń z hostem sieci.</span><span class="sxs-lookup"><span data-stu-id="53dcd-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53dcd-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="53dcd-122">Remarks</span></span>  
 <span data-ttu-id="53dcd-123">`remove` Element usuwa wpis listy zarządzania połączenia dla określonego serwera.</span><span class="sxs-lookup"><span data-stu-id="53dcd-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="53dcd-124">Wartość `address` atrybutu powinna być prawidłową nazwą adres lub hosta IP.</span><span class="sxs-lookup"><span data-stu-id="53dcd-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="53dcd-125">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="53dcd-125">Configuration Files</span></span>  
 <span data-ttu-id="53dcd-126">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="53dcd-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="53dcd-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="53dcd-127">Example</span></span>  
 <span data-ttu-id="53dcd-128">Poniższy przykład usuwa wszystkie pozycje listy zarządzania połączenia dla www.adventure-works.com serwera, a następnie konfiguruje aplikację do korzystania z połączeń cztery www.contoso.com serwera i dwa połączenia do innych serwerów.</span><span class="sxs-lookup"><span data-stu-id="53dcd-128">The following example removes any connection management list entries for the server www.adventure-works.com and then configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="53dcd-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53dcd-129">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="53dcd-130">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="53dcd-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

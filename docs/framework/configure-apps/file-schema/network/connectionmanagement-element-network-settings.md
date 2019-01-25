---
title: '&lt;connectionManagement&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 28864de79e809968f7efa6f3b052cfd599961854
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685029"
---
# <a name="ltconnectionmanagementgt-element-network-settings"></a><span data-ttu-id="11c63-102">&lt;connectionManagement&gt; — Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="11c63-102">&lt;connectionManagement&gt; Element (Network Settings)</span></span>
<span data-ttu-id="11c63-103">Określa maksymalną liczbę połączeń z hostem sieci.</span><span class="sxs-lookup"><span data-stu-id="11c63-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="11c63-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="11c63-104">\<configuration></span></span>  
<span data-ttu-id="11c63-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="11c63-105">\<system.net></span></span>  
<span data-ttu-id="11c63-106">\<connectionManagement></span><span class="sxs-lookup"><span data-stu-id="11c63-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11c63-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="11c63-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11c63-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="11c63-108">Attributes and Elements</span></span>  
 <span data-ttu-id="11c63-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="11c63-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11c63-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="11c63-110">Attributes</span></span>  
 <span data-ttu-id="11c63-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="11c63-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="11c63-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="11c63-112">Child Elements</span></span>  
  
|<span data-ttu-id="11c63-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="11c63-113">**Element**</span></span>|<span data-ttu-id="11c63-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="11c63-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="11c63-115">add</span><span class="sxs-lookup"><span data-stu-id="11c63-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="11c63-116">Dodaje adres IP lub nazwę DNS na liście zarządzania połączenia.</span><span class="sxs-lookup"><span data-stu-id="11c63-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="11c63-117">Usuń zaznaczenie</span><span class="sxs-lookup"><span data-stu-id="11c63-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="11c63-118">Czyści listę zarządzania połączenia.</span><span class="sxs-lookup"><span data-stu-id="11c63-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="11c63-119">remove</span><span class="sxs-lookup"><span data-stu-id="11c63-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="11c63-120">Usuwa adres IP lub nazwę DNS na liście zarządzania połączenia.</span><span class="sxs-lookup"><span data-stu-id="11c63-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11c63-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="11c63-121">Parent Elements</span></span>  
  
|<span data-ttu-id="11c63-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="11c63-122">**Element**</span></span>|<span data-ttu-id="11c63-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="11c63-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="11c63-124">system.net</span><span class="sxs-lookup"><span data-stu-id="11c63-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="11c63-125">Zawiera ustawienia, które określają, jak .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="11c63-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11c63-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11c63-126">Remarks</span></span>  
 <span data-ttu-id="11c63-127">`connectionManagement` Element definiuje maksymalną liczbę połączeń do serwera lub grupy serwerów.</span><span class="sxs-lookup"><span data-stu-id="11c63-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="11c63-128">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="11c63-128">Configuration Files</span></span>  
 <span data-ttu-id="11c63-129">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="11c63-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="11c63-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="11c63-130">Example</span></span>  
 <span data-ttu-id="11c63-131">Poniższy przykład umożliwia skonfigurowanie aplikacji na używanie cztery połączenia z serwerem `www.contoso.com` i dwóch połączeń na inne serwery.</span><span class="sxs-lookup"><span data-stu-id="11c63-131">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="11c63-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11c63-132">See also</span></span>
- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="11c63-133">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="11c63-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

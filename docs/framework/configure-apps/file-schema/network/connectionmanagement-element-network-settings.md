---
title: "&lt;connectionmanagement —&gt; — Element (ustawienia sieciowe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e3380ce1e8e798740214feee0e76d9949caa6bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltconnectionmanagementgt-element-network-settings"></a><span data-ttu-id="57e7a-102">&lt;connectionmanagement —&gt; — Element (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="57e7a-102">&lt;connectionManagement&gt; Element (Network Settings)</span></span>
<span data-ttu-id="57e7a-103">Określa maksymalną liczbę połączeń z hostem sieci.</span><span class="sxs-lookup"><span data-stu-id="57e7a-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="57e7a-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="57e7a-104">\<configuration></span></span>  
<span data-ttu-id="57e7a-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="57e7a-105">\<system.net></span></span>  
<span data-ttu-id="57e7a-106">\<connectionmanagement — ></span><span class="sxs-lookup"><span data-stu-id="57e7a-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57e7a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="57e7a-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57e7a-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="57e7a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="57e7a-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="57e7a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57e7a-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="57e7a-110">Attributes</span></span>  
 <span data-ttu-id="57e7a-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="57e7a-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="57e7a-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="57e7a-112">Child Elements</span></span>  
  
|<span data-ttu-id="57e7a-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="57e7a-113">**Element**</span></span>|<span data-ttu-id="57e7a-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="57e7a-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="57e7a-115">Dodaj</span><span class="sxs-lookup"><span data-stu-id="57e7a-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="57e7a-116">Dodaje adres IP lub nazwa DNS do listy zarządzania połączenia.</span><span class="sxs-lookup"><span data-stu-id="57e7a-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="57e7a-117">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="57e7a-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="57e7a-118">Usuwa listy zarządzania połączenia.</span><span class="sxs-lookup"><span data-stu-id="57e7a-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="57e7a-119">Usuń</span><span class="sxs-lookup"><span data-stu-id="57e7a-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="57e7a-120">Usuwa adres IP lub nazwa DNS z listy zarządzania połączenia.</span><span class="sxs-lookup"><span data-stu-id="57e7a-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57e7a-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="57e7a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="57e7a-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="57e7a-122">**Element**</span></span>|<span data-ttu-id="57e7a-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="57e7a-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="57e7a-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="57e7a-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="57e7a-125">Zawiera ustawienia, które określają sposób programu .NET Framework łączy się z siecią.</span><span class="sxs-lookup"><span data-stu-id="57e7a-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57e7a-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57e7a-126">Remarks</span></span>  
 <span data-ttu-id="57e7a-127">`connectionManagement` Element definiuje maksymalną liczbę połączeń do serwera lub grupy serwerów.</span><span class="sxs-lookup"><span data-stu-id="57e7a-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="57e7a-128">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="57e7a-128">Configuration Files</span></span>  
 <span data-ttu-id="57e7a-129">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="57e7a-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="57e7a-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="57e7a-130">Example</span></span>  
 <span data-ttu-id="57e7a-131">Poniższy przykład konfiguruje aplikację do korzystania z połączeń cztery www.contoso.com serwera i dwa połączenia do innych serwerów.</span><span class="sxs-lookup"><span data-stu-id="57e7a-131">The following example configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="57e7a-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57e7a-132">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="57e7a-133">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="57e7a-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

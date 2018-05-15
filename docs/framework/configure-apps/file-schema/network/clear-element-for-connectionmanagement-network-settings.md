---
title: '&lt;Wyczyść&gt; elementu connectionmanagement — (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, connectionManagement
- connectionManagement, clear element
- clear element, connectionManagement
- <connectionManagement>, clear element
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5bcd17cfe1f3bd7531453b62552a4907df5b96bc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltcleargt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="8be44-102">&lt;Wyczyść&gt; elementu connectionmanagement — (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="8be44-102">&lt;clear&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="8be44-103">Usuwa listy zarządzania połączenia.</span><span class="sxs-lookup"><span data-stu-id="8be44-103">Clears the connection management list.</span></span>  
  
 <span data-ttu-id="8be44-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="8be44-104">\<configuration></span></span>  
<span data-ttu-id="8be44-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="8be44-105">\<system.net></span></span>  
<span data-ttu-id="8be44-106">\<connectionmanagement — ></span><span class="sxs-lookup"><span data-stu-id="8be44-106">\<connectionManagement></span></span>  
<span data-ttu-id="8be44-107">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="8be44-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8be44-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="8be44-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8be44-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8be44-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8be44-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8be44-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8be44-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8be44-111">Attributes</span></span>  
 <span data-ttu-id="8be44-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="8be44-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8be44-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8be44-113">Child Elements</span></span>  
 <span data-ttu-id="8be44-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="8be44-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8be44-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8be44-115">Parent Elements</span></span>  
  
|<span data-ttu-id="8be44-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="8be44-116">**Element**</span></span>|<span data-ttu-id="8be44-117">**Opis**</span><span class="sxs-lookup"><span data-stu-id="8be44-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8be44-118">connectionmanagement —</span><span class="sxs-lookup"><span data-stu-id="8be44-118">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="8be44-119">Określa maksymalną liczbę połączeń z hostem sieci.</span><span class="sxs-lookup"><span data-stu-id="8be44-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8be44-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8be44-120">Remarks</span></span>  
 <span data-ttu-id="8be44-121">`clear` Element czyści wszystkie wpisy z listy zarządzania połączenia.</span><span class="sxs-lookup"><span data-stu-id="8be44-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8be44-122">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8be44-122">Configuration Files</span></span>  
 <span data-ttu-id="8be44-123">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="8be44-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8be44-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="8be44-124">Example</span></span>  
 <span data-ttu-id="8be44-125">Poniższy przykład powoduje wyczyszczenie listy zarządzania połączenia, a następnie dodaje nowe wpisy zarządzania połączenia www.contoso.com serwera i innych hostów w sieci.</span><span class="sxs-lookup"><span data-stu-id="8be44-125">The following example clears the connection management list and then adds new connection management entries for the server www.contoso.com and all other network hosts.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <clear/>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8be44-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8be44-126">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="8be44-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="8be44-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

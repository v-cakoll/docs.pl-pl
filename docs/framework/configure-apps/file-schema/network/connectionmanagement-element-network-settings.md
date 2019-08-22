---
title: <connectionManagement>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: faaba1b9de302ed916ad1a81c7e80b3fb5a67170
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664166"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="806ce-102">\<connectionManagement >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="806ce-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="806ce-103">Określa maksymalną liczbę połączeń z hostem sieciowym.</span><span class="sxs-lookup"><span data-stu-id="806ce-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="806ce-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="806ce-104">\<configuration></span></span>  
<span data-ttu-id="806ce-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="806ce-105">\<system.net></span></span>  
<span data-ttu-id="806ce-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="806ce-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="806ce-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="806ce-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="806ce-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="806ce-108">Attributes and Elements</span></span>  
 <span data-ttu-id="806ce-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="806ce-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="806ce-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="806ce-110">Attributes</span></span>  
 <span data-ttu-id="806ce-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="806ce-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="806ce-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="806ce-112">Child Elements</span></span>  
  
|<span data-ttu-id="806ce-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="806ce-113">**Element**</span></span>|<span data-ttu-id="806ce-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="806ce-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="806ce-115">add</span><span class="sxs-lookup"><span data-stu-id="806ce-115">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="806ce-116">Dodaje adres IP lub nazwę DNS do listy zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="806ce-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="806ce-117">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="806ce-117">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="806ce-118">Czyści listę zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="806ce-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="806ce-119">remove</span><span class="sxs-lookup"><span data-stu-id="806ce-119">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="806ce-120">Usuwa adres IP lub nazwę DNS z listy zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="806ce-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="806ce-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="806ce-121">Parent Elements</span></span>  
  
|<span data-ttu-id="806ce-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="806ce-122">**Element**</span></span>|<span data-ttu-id="806ce-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="806ce-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="806ce-124">system.net</span><span class="sxs-lookup"><span data-stu-id="806ce-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="806ce-125">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="806ce-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="806ce-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="806ce-126">Remarks</span></span>  
 <span data-ttu-id="806ce-127">`connectionManagement` Element definiuje maksymalną liczbę połączeń z serwerem lub grupą serwerów.</span><span class="sxs-lookup"><span data-stu-id="806ce-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="806ce-128">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="806ce-128">Configuration Files</span></span>  
 <span data-ttu-id="806ce-129">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="806ce-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="806ce-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="806ce-130">Example</span></span>  
 <span data-ttu-id="806ce-131">Poniższy przykład służy do konfigurowania aplikacji do korzystania z czterech połączeń z serwerem `www.contoso.com` i dwóch połączeń z innymi serwerami.</span><span class="sxs-lookup"><span data-stu-id="806ce-131">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="806ce-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="806ce-132">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="806ce-133">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="806ce-133">Network Settings Schema</span></span>](index.md)

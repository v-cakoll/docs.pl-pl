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
ms.openlocfilehash: d377a77a4a1b4c57e9edd4fbfa364387f1bae479
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699427"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="ef511-102">\<connectionManagement >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="ef511-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="ef511-103">Określa maksymalną liczbę połączeń z hostem sieciowym.</span><span class="sxs-lookup"><span data-stu-id="ef511-103">Specifies the maximum number of connections to a network host.</span></span>  
  
[<span data-ttu-id="ef511-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="ef511-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="ef511-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="ef511-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="ef511-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<connectionManagement >**</span><span class="sxs-lookup"><span data-stu-id="ef511-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef511-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="ef511-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef511-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ef511-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ef511-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ef511-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef511-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ef511-110">Attributes</span></span>  
 <span data-ttu-id="ef511-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="ef511-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ef511-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ef511-112">Child Elements</span></span>  
  
|<span data-ttu-id="ef511-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="ef511-113">**Element**</span></span>|<span data-ttu-id="ef511-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="ef511-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ef511-115">add</span><span class="sxs-lookup"><span data-stu-id="ef511-115">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="ef511-116">Dodaje adres IP lub nazwę DNS do listy zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="ef511-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="ef511-117">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="ef511-117">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="ef511-118">Czyści listę zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="ef511-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="ef511-119">remove</span><span class="sxs-lookup"><span data-stu-id="ef511-119">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="ef511-120">Usuwa adres IP lub nazwę DNS z listy zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="ef511-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ef511-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ef511-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ef511-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="ef511-122">**Element**</span></span>|<span data-ttu-id="ef511-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="ef511-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="ef511-124">system.net</span><span class="sxs-lookup"><span data-stu-id="ef511-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="ef511-125">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="ef511-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef511-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ef511-126">Remarks</span></span>  
 <span data-ttu-id="ef511-127">Element `connectionManagement` określa maksymalną liczbę połączeń z serwerem lub grupą serwerów.</span><span class="sxs-lookup"><span data-stu-id="ef511-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ef511-128">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ef511-128">Configuration Files</span></span>  
 <span data-ttu-id="ef511-129">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="ef511-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef511-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef511-130">Example</span></span>  
 <span data-ttu-id="ef511-131">Poniższy przykład służy do konfigurowania aplikacji do używania czterech połączeń z serwerem `www.contoso.com` i dwóch połączeń z innymi serwerami.</span><span class="sxs-lookup"><span data-stu-id="ef511-131">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ef511-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef511-132">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="ef511-133">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="ef511-133">Network Settings Schema</span></span>](index.md)

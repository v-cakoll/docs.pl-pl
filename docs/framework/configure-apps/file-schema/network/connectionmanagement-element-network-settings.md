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
ms.openlocfilehash: 9f1e382bbbaad2cb95e2c33bbbdfb4c505378c9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154897"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="9d357-102">\<connectionManagement>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="9d357-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="9d357-103">Określa maksymalną liczbę połączeń z hostem sieciowym.</span><span class="sxs-lookup"><span data-stu-id="9d357-103">Specifies the maximum number of connections to a network host.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a><span data-ttu-id="9d357-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9d357-104">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d357-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9d357-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9d357-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9d357-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d357-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9d357-107">Attributes</span></span>  
 <span data-ttu-id="9d357-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="9d357-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9d357-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9d357-109">Child Elements</span></span>  
  
|<span data-ttu-id="9d357-110">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="9d357-110">**Element**</span></span>|<span data-ttu-id="9d357-111">**Opis**</span><span class="sxs-lookup"><span data-stu-id="9d357-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9d357-112">add</span><span class="sxs-lookup"><span data-stu-id="9d357-112">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="9d357-113">Dodaje adres IP lub nazwę DNS do listy zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="9d357-113">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="9d357-114">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="9d357-114">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="9d357-115">Czyści listę zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="9d357-115">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="9d357-116">usuwa</span><span class="sxs-lookup"><span data-stu-id="9d357-116">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="9d357-117">Usuwa adres IP lub nazwę DNS z listy zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="9d357-117">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9d357-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9d357-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9d357-119">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="9d357-119">**Element**</span></span>|<span data-ttu-id="9d357-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="9d357-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9d357-121">system.net</span><span class="sxs-lookup"><span data-stu-id="9d357-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="9d357-122">Zawiera ustawienia, które określają, w jaki sposób .NET Framework nawiązuje połączenie z siecią.</span><span class="sxs-lookup"><span data-stu-id="9d357-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d357-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d357-123">Remarks</span></span>  
 <span data-ttu-id="9d357-124">`connectionManagement`Element definiuje maksymalną liczbę połączeń z serwerem lub grupą serwerów.</span><span class="sxs-lookup"><span data-stu-id="9d357-124">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="9d357-125">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9d357-125">Configuration Files</span></span>  
 <span data-ttu-id="9d357-126">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="9d357-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d357-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d357-127">Example</span></span>  
 <span data-ttu-id="9d357-128">Poniższy przykład służy do konfigurowania aplikacji do korzystania z czterech połączeń z serwerem `www.contoso.com` i dwóch połączeń z innymi serwerami.</span><span class="sxs-lookup"><span data-stu-id="9d357-128">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d357-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d357-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="9d357-130">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="9d357-130">Network Settings Schema</span></span>](index.md)

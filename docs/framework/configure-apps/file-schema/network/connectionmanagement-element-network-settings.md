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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154897"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="81317-102">\<connectionManagement> Element (Ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="81317-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="81317-103">Określa maksymalną liczbę połączeń z hostem sieciowym.</span><span class="sxs-lookup"><span data-stu-id="81317-103">Specifies the maximum number of connections to a network host.</span></span>  

<span data-ttu-id="81317-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="81317-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="81317-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="81317-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="81317-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**</span><span class="sxs-lookup"><span data-stu-id="81317-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**</span></span>

## <a name="syntax"></a><span data-ttu-id="81317-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="81317-107">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81317-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="81317-108">Attributes and Elements</span></span>  
 <span data-ttu-id="81317-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="81317-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81317-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="81317-110">Attributes</span></span>  
 <span data-ttu-id="81317-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="81317-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="81317-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="81317-112">Child Elements</span></span>  
  
|<span data-ttu-id="81317-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="81317-113">**Element**</span></span>|<span data-ttu-id="81317-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="81317-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="81317-115">Dodaj</span><span class="sxs-lookup"><span data-stu-id="81317-115">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="81317-116">Dodaje adres IP lub nazwę DNS do listy zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="81317-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="81317-117">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="81317-117">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="81317-118">Czyści listę zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="81317-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="81317-119">Usunąć</span><span class="sxs-lookup"><span data-stu-id="81317-119">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="81317-120">Usuwa adres IP lub nazwę DNS z listy zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="81317-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="81317-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="81317-121">Parent Elements</span></span>  
  
|<span data-ttu-id="81317-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="81317-122">**Element**</span></span>|<span data-ttu-id="81317-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="81317-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="81317-124">system.net</span><span class="sxs-lookup"><span data-stu-id="81317-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="81317-125">Zawiera ustawienia określające sposób łączenia się programu .NET Framework z siecią.</span><span class="sxs-lookup"><span data-stu-id="81317-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81317-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="81317-126">Remarks</span></span>  
 <span data-ttu-id="81317-127">Element `connectionManagement` definiuje maksymalną liczbę połączeń z serwerem lub grupą serwerów.</span><span class="sxs-lookup"><span data-stu-id="81317-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="81317-128">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="81317-128">Configuration Files</span></span>  
 <span data-ttu-id="81317-129">Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="81317-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="81317-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="81317-130">Example</span></span>  
 <span data-ttu-id="81317-131">Poniższy przykład konfiguruje aplikację do używania `www.contoso.com` czterech połączeń z serwerem i dwóch połączeń ze wszystkimi innymi serwerami.</span><span class="sxs-lookup"><span data-stu-id="81317-131">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="81317-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81317-132">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="81317-133">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="81317-133">Network Settings Schema</span></span>](index.md)

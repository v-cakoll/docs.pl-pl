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
ms.openlocfilehash: 8ab7a43fbb3e8df5bb0c99b5947f2fafb362399a
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664029"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="67987-102">\<Usuń element > dla connectionManagement (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="67987-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="67987-103">Usuwa adres IP lub nazwę DNS z listy zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="67987-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
 <span data-ttu-id="67987-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="67987-104">\<configuration></span></span>  
<span data-ttu-id="67987-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="67987-105">\<system.net></span></span>  
<span data-ttu-id="67987-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="67987-106">\<connectionManagement></span></span>  
<span data-ttu-id="67987-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="67987-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67987-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="67987-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67987-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="67987-109">Attributes and Elements</span></span>  
 <span data-ttu-id="67987-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="67987-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67987-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="67987-111">Attributes</span></span>  
  
|<span data-ttu-id="67987-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="67987-112">**Attribute**</span></span>|<span data-ttu-id="67987-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="67987-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="67987-114">Adres IP lub nazwa DNS.</span><span class="sxs-lookup"><span data-stu-id="67987-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67987-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="67987-115">Child Elements</span></span>  
 <span data-ttu-id="67987-116">Brak.</span><span class="sxs-lookup"><span data-stu-id="67987-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67987-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="67987-117">Parent Elements</span></span>  
  
|<span data-ttu-id="67987-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="67987-118">**Element**</span></span>|<span data-ttu-id="67987-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="67987-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="67987-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="67987-120">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="67987-121">Określa maksymalną liczbę połączeń z hostem sieciowym.</span><span class="sxs-lookup"><span data-stu-id="67987-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67987-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="67987-122">Remarks</span></span>  
 <span data-ttu-id="67987-123">`remove` Element usuwa wpis listy zarządzania połączeniami dla określonego serwera.</span><span class="sxs-lookup"><span data-stu-id="67987-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="67987-124">Wartość `address` atrybutu powinna być prawidłowym adresem IP lub nazwą hosta.</span><span class="sxs-lookup"><span data-stu-id="67987-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="67987-125">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="67987-125">Configuration Files</span></span>  
 <span data-ttu-id="67987-126">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="67987-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="67987-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="67987-127">Example</span></span>  
 <span data-ttu-id="67987-128">Poniższy przykład usuwa wszystkie wpisy listy zarządzania połączeniami dla serwera `www.adventure-works.com` , a następnie konfiguruje aplikację do korzystania z czterech połączeń z serwerem `www.contoso.com` i dwóch połączeń z innymi serwerami.</span><span class="sxs-lookup"><span data-stu-id="67987-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="67987-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67987-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="67987-130">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="67987-130">Network Settings Schema</span></span>](index.md)

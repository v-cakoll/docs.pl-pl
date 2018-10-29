---
title: '&lt;Dodaj&gt; Element dla connectionManagement (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
ms.openlocfilehash: a3b8de254c28aedc21df5baf54bd67527e35b7f9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201296"
---
# <a name="ltaddgt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="63c9f-102">&lt;Dodaj&gt; Element dla connectionManagement (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="63c9f-102">&lt;add&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="63c9f-103">Dodaje adres IP lub nazwę DNS na liście zarządzania połączenia.</span><span class="sxs-lookup"><span data-stu-id="63c9f-103">Adds an IP address or DNS name to the connection management list.</span></span>  
  
 <span data-ttu-id="63c9f-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="63c9f-104">\<configuration></span></span>  
<span data-ttu-id="63c9f-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="63c9f-105">\<system.net></span></span>  
<span data-ttu-id="63c9f-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="63c9f-106">\<connectionManagement></span></span>  
<span data-ttu-id="63c9f-107">\<add></span><span class="sxs-lookup"><span data-stu-id="63c9f-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63c9f-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="63c9f-108">Syntax</span></span>  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63c9f-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="63c9f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="63c9f-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="63c9f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63c9f-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="63c9f-111">Attributes</span></span>  
  
|<span data-ttu-id="63c9f-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="63c9f-112">**Attribute**</span></span>|<span data-ttu-id="63c9f-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="63c9f-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="63c9f-114">Ciąg opisujący adresu IP lub nazwy DNS.</span><span class="sxs-lookup"><span data-stu-id="63c9f-114">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="63c9f-115">Maksymalna liczba dozwolonych połączeń z serwerem.</span><span class="sxs-lookup"><span data-stu-id="63c9f-115">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="63c9f-116">Jeśli nie zostanie podany, wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="63c9f-116">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63c9f-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="63c9f-117">Child Elements</span></span>  
 <span data-ttu-id="63c9f-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="63c9f-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="63c9f-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="63c9f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="63c9f-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="63c9f-120">**Element**</span></span>|<span data-ttu-id="63c9f-121">**Opis**</span><span class="sxs-lookup"><span data-stu-id="63c9f-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="63c9f-122">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="63c9f-122">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="63c9f-123">Określa maksymalną liczbę połączeń z hostem sieci.</span><span class="sxs-lookup"><span data-stu-id="63c9f-123">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63c9f-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63c9f-124">Remarks</span></span>  
 <span data-ttu-id="63c9f-125">Wartość `address` atrybut powinien być gwiazdki, aby pokazać wszystkie połączenia lub ciąg w postaci `<schema>://<idn_hostname>[:<port>]`.</span><span class="sxs-lookup"><span data-stu-id="63c9f-125">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="63c9f-126">Jeśli identyfikator URI przekazywany do żadnych interfejsów API protokołu HTTP zawiera Unicode, zostaną przekonwertowane nazwę wewnętrznie za pomocą <xref:System.Uri.DnsSafeHost%2A> której może zwrócić ciąg punicode (zachowanie zależy od bieżącej konfiguracji IDN).</span><span class="sxs-lookup"><span data-stu-id="63c9f-126">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="63c9f-127">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="63c9f-127">Configuration Files</span></span>  
 <span data-ttu-id="63c9f-128">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="63c9f-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63c9f-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="63c9f-129">Example</span></span>  
 <span data-ttu-id="63c9f-130">Poniższy przykład umożliwia skonfigurowanie aplikacji na używanie cztery połączenia z serwerem `www.contoso.com` i dwóch połączeń na inne serwery.</span><span class="sxs-lookup"><span data-stu-id="63c9f-130">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="63c9f-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63c9f-131">See Also</span></span>  
- <xref:System.Net.ServicePoint>  
- <xref:System.Net.ServicePointManager>  
- [<span data-ttu-id="63c9f-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="63c9f-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

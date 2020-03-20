---
title: <add>, element dla connectionManagement (ustawienia sieci)
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
ms.openlocfilehash: 093b68d31e03094bedefa96a2f2d53eb3d84edf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155014"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="83f48-102">\<dodaj element> do łączeniaManagement (Ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="83f48-102">\<add> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="83f48-103">Dodaje adres IP lub nazwę DNS do listy zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="83f48-103">Adds an IP address or DNS name to the connection management list.</span></span>  

<span data-ttu-id="83f48-104">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="83f48-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="83f48-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="83f48-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="83f48-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="83f48-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>\
<span data-ttu-id="83f48-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dodaj>**</span><span class="sxs-lookup"><span data-stu-id="83f48-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="83f48-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="83f48-108">Syntax</span></span>  
  
```xml  
<add
  address="address expression"
  maxconnection="integer"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83f48-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="83f48-109">Attributes and Elements</span></span>  
 <span data-ttu-id="83f48-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="83f48-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83f48-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="83f48-111">Attributes</span></span>  
  
|<span data-ttu-id="83f48-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="83f48-112">**Attribute**</span></span>|<span data-ttu-id="83f48-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="83f48-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="83f48-114">Ciąg opisujący adres IP lub nazwę DNS.</span><span class="sxs-lookup"><span data-stu-id="83f48-114">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="83f48-115">Maksymalna liczba połączeń dozwolonych z serwerem.</span><span class="sxs-lookup"><span data-stu-id="83f48-115">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="83f48-116">Jeśli nie podano, wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="83f48-116">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83f48-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="83f48-117">Child Elements</span></span>  
 <span data-ttu-id="83f48-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="83f48-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83f48-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="83f48-119">Parent Elements</span></span>  
  
|<span data-ttu-id="83f48-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="83f48-120">**Element**</span></span>|<span data-ttu-id="83f48-121">**Opis**</span><span class="sxs-lookup"><span data-stu-id="83f48-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="83f48-122">connectionManagement (PołączenieManagement)</span><span class="sxs-lookup"><span data-stu-id="83f48-122">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="83f48-123">Określa maksymalną liczbę połączeń z hostem sieciowym.</span><span class="sxs-lookup"><span data-stu-id="83f48-123">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83f48-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83f48-124">Remarks</span></span>  
 <span data-ttu-id="83f48-125">Wartość atrybutu `address` powinna być gwiazdką wskazującą wszystkie połączenia lub ciągiem formularza `<schema>://<idn_hostname>[:<port>]`.</span><span class="sxs-lookup"><span data-stu-id="83f48-125">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="83f48-126">Jeśli identyfikator URI przekazany do dowolnych interfejsów API HTTP zawiera Unicode, nazwa zostanie przekonwertowana wewnętrznie przy użyciu, <xref:System.Uri.DnsSafeHost%2A> który może zwrócić ciąg punicode (zachowanie zależne od bieżącej konfiguracji IDN).</span><span class="sxs-lookup"><span data-stu-id="83f48-126">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="83f48-127">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="83f48-127">Configuration Files</span></span>  
 <span data-ttu-id="83f48-128">Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="83f48-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="83f48-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="83f48-129">Example</span></span>  
 <span data-ttu-id="83f48-130">Poniższy przykład konfiguruje aplikację do używania `www.contoso.com` czterech połączeń z serwerem i dwóch połączeń ze wszystkimi innymi serwerami.</span><span class="sxs-lookup"><span data-stu-id="83f48-130">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="83f48-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83f48-131">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="83f48-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="83f48-132">Network Settings Schema</span></span>](index.md)

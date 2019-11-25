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
ms.openlocfilehash: 19ebbfba477eeba253a7af0742953cc6a4d45a0e
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088517"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="f8834-102">\<dodać elementu > dla connectionManagement (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="f8834-102">\<add> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="f8834-103">Dodaje adres IP lub nazwę DNS do listy zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="f8834-103">Adds an IP address or DNS name to the connection management list.</span></span>  

<span data-ttu-id="f8834-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f8834-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f8834-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f8834-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="f8834-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f8834-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>\
<span data-ttu-id="f8834-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dodaj >**</span><span class="sxs-lookup"><span data-stu-id="f8834-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f8834-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8834-108">Syntax</span></span>  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8834-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f8834-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f8834-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f8834-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8834-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f8834-111">Attributes</span></span>  
  
|<span data-ttu-id="f8834-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="f8834-112">**Attribute**</span></span>|<span data-ttu-id="f8834-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f8834-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="f8834-114">Ciąg opisujący adres IP lub nazwę DNS.</span><span class="sxs-lookup"><span data-stu-id="f8834-114">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="f8834-115">Maksymalna liczba połączeń dozwolonych dla serwera.</span><span class="sxs-lookup"><span data-stu-id="f8834-115">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="f8834-116">Jeśli nie zostanie podany, wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="f8834-116">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8834-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f8834-117">Child Elements</span></span>  
 <span data-ttu-id="f8834-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="f8834-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f8834-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f8834-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f8834-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="f8834-120">**Element**</span></span>|<span data-ttu-id="f8834-121">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f8834-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f8834-122">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="f8834-122">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="f8834-123">Określa maksymalną liczbę połączeń z hostem sieciowym.</span><span class="sxs-lookup"><span data-stu-id="f8834-123">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8834-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8834-124">Remarks</span></span>  
 <span data-ttu-id="f8834-125">Wartość atrybutu `address` powinna być gwiazdką wskazującą wszystkie połączenia lub ciąg `<schema>://<idn_hostname>[:<port>]`formularza.</span><span class="sxs-lookup"><span data-stu-id="f8834-125">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="f8834-126">Jeśli identyfikator URI przesłany do dowolnego interfejsu API protokołu HTTP zawiera Unicode, nazwa zostanie przekonwertowane wewnętrznie przy użyciu <xref:System.Uri.DnsSafeHost%2A>, co może zwrócić ciąg punicode (zachowanie zależne od bieżącej konfiguracji IDN).</span><span class="sxs-lookup"><span data-stu-id="f8834-126">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f8834-127">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f8834-127">Configuration Files</span></span>  
 <span data-ttu-id="f8834-128">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="f8834-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8834-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8834-129">Example</span></span>  
 <span data-ttu-id="f8834-130">Poniższy przykład służy do konfigurowania aplikacji do używania czterech połączeń z serwerem `www.contoso.com` i dwóch połączeń z innymi serwerami.</span><span class="sxs-lookup"><span data-stu-id="f8834-130">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f8834-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8834-131">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="f8834-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="f8834-132">Network Settings Schema</span></span>](index.md)

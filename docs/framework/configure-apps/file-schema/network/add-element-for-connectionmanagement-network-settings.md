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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155014"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="5b22f-102">\<add>, element dla connectionManagement (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="5b22f-102">\<add> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="5b22f-103">Dodaje adres IP lub nazwę DNS do listy zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="5b22f-103">Adds an IP address or DNS name to the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="5b22f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b22f-104">Syntax</span></span>  
  
```xml  
<add
  address="address expression"
  maxconnection="integer"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5b22f-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5b22f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5b22f-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5b22f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5b22f-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5b22f-107">Attributes</span></span>  
  
|<span data-ttu-id="5b22f-108">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="5b22f-108">**Attribute**</span></span>|<span data-ttu-id="5b22f-109">**Opis**</span><span class="sxs-lookup"><span data-stu-id="5b22f-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="5b22f-110">Ciąg opisujący adres IP lub nazwę DNS.</span><span class="sxs-lookup"><span data-stu-id="5b22f-110">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="5b22f-111">Maksymalna liczba połączeń dozwolonych dla serwera.</span><span class="sxs-lookup"><span data-stu-id="5b22f-111">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="5b22f-112">Jeśli nie zostanie podany, wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="5b22f-112">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5b22f-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5b22f-113">Child Elements</span></span>  
 <span data-ttu-id="5b22f-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="5b22f-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5b22f-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5b22f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5b22f-116">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="5b22f-116">**Element**</span></span>|<span data-ttu-id="5b22f-117">**Opis**</span><span class="sxs-lookup"><span data-stu-id="5b22f-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5b22f-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="5b22f-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="5b22f-119">Określa maksymalną liczbę połączeń z hostem sieciowym.</span><span class="sxs-lookup"><span data-stu-id="5b22f-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b22f-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b22f-120">Remarks</span></span>  
 <span data-ttu-id="5b22f-121">Wartość `address` atrybutu powinna być gwiazdką wskazującą wszystkie połączenia lub ciąg formularza `<schema>://<idn_hostname>[:<port>]` .</span><span class="sxs-lookup"><span data-stu-id="5b22f-121">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="5b22f-122">Jeśli identyfikator URI przesłany do dowolnego interfejsu API protokołu HTTP zawiera Unicode, nazwa zostanie przekonwertowane wewnętrznie przy użyciu, <xref:System.Uri.DnsSafeHost%2A> co może zwrócić ciąg punicode (zachowanie zależne od bieżącej konfiguracji IDN).</span><span class="sxs-lookup"><span data-stu-id="5b22f-122">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5b22f-123">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5b22f-123">Configuration Files</span></span>  
 <span data-ttu-id="5b22f-124">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="5b22f-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b22f-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b22f-125">Example</span></span>  
 <span data-ttu-id="5b22f-126">Poniższy przykład służy do konfigurowania aplikacji do korzystania z czterech połączeń z serwerem `www.contoso.com` i dwóch połączeń z innymi serwerami.</span><span class="sxs-lookup"><span data-stu-id="5b22f-126">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5b22f-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b22f-127">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="5b22f-128">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="5b22f-128">Network Settings Schema</span></span>](index.md)

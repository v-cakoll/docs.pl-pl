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
ms.openlocfilehash: 39ce85c3c15a2d4bdfce801a35e9ca088bd5091b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154741"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="8de23-102">\<remove>, element dla connectionManagement (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="8de23-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="8de23-103">Usuwa adres IP lub nazwę DNS z listy zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="8de23-103">Removes an IP address or DNS name from the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="8de23-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8de23-104">Syntax</span></span>  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8de23-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8de23-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8de23-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8de23-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8de23-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8de23-107">Attributes</span></span>  
  
|<span data-ttu-id="8de23-108">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="8de23-108">**Attribute**</span></span>|<span data-ttu-id="8de23-109">**Opis**</span><span class="sxs-lookup"><span data-stu-id="8de23-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="8de23-110">Adres IP lub nazwa DNS.</span><span class="sxs-lookup"><span data-stu-id="8de23-110">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8de23-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8de23-111">Child Elements</span></span>  
 <span data-ttu-id="8de23-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="8de23-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8de23-113">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8de23-113">Parent Elements</span></span>  
  
|<span data-ttu-id="8de23-114">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="8de23-114">**Element**</span></span>|<span data-ttu-id="8de23-115">**Opis**</span><span class="sxs-lookup"><span data-stu-id="8de23-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8de23-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="8de23-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="8de23-117">Określa maksymalną liczbę połączeń z hostem sieciowym.</span><span class="sxs-lookup"><span data-stu-id="8de23-117">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8de23-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8de23-118">Remarks</span></span>  
 <span data-ttu-id="8de23-119">`remove`Element usuwa wpis listy zarządzania połączeniami dla określonego serwera.</span><span class="sxs-lookup"><span data-stu-id="8de23-119">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="8de23-120">Wartość `address` atrybutu powinna być prawidłowym adresem IP lub nazwą hosta.</span><span class="sxs-lookup"><span data-stu-id="8de23-120">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8de23-121">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8de23-121">Configuration Files</span></span>  
 <span data-ttu-id="8de23-122">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="8de23-122">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8de23-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="8de23-123">Example</span></span>  
 <span data-ttu-id="8de23-124">Poniższy przykład usuwa wszystkie wpisy listy zarządzania połączeniami dla serwera `www.adventure-works.com` , a następnie konfiguruje aplikację do korzystania z czterech połączeń z serwerem `www.contoso.com` i dwóch połączeń z innymi serwerami.</span><span class="sxs-lookup"><span data-stu-id="8de23-124">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8de23-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8de23-125">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="8de23-126">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="8de23-126">Network Settings Schema</span></span>](index.md)

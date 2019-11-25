---
title: <clear>, element dla connectionManagement (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, connectionManagement
- connectionManagement, clear element
- clear element, connectionManagement
- <connectionManagement>, clear element
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
ms.openlocfilehash: a76df48a9de084e1121a5e96b22edf7aa3acba23
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088482"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="6249b-102">\<Wyczyść element > dla connectionManagement (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="6249b-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="6249b-103">Czyści listę zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="6249b-103">Clears the connection management list.</span></span>  

<span data-ttu-id="6249b-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6249b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6249b-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6249b-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="6249b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="6249b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>\
<span data-ttu-id="6249b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="6249b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="6249b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="6249b-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6249b-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6249b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6249b-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6249b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6249b-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6249b-111">Attributes</span></span>  
 <span data-ttu-id="6249b-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="6249b-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6249b-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6249b-113">Child Elements</span></span>  
 <span data-ttu-id="6249b-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="6249b-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6249b-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6249b-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6249b-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="6249b-116">**Element**</span></span>|<span data-ttu-id="6249b-117">**Opis**</span><span class="sxs-lookup"><span data-stu-id="6249b-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6249b-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="6249b-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="6249b-119">Określa maksymalną liczbę połączeń z hostem sieciowym.</span><span class="sxs-lookup"><span data-stu-id="6249b-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6249b-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6249b-120">Remarks</span></span>  
 <span data-ttu-id="6249b-121">Element `clear` czyści wszystkie wpisy z listy zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="6249b-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6249b-122">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6249b-122">Configuration Files</span></span>  
 <span data-ttu-id="6249b-123">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="6249b-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6249b-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="6249b-124">Example</span></span>  
 <span data-ttu-id="6249b-125">Poniższy przykład czyści listę zarządzanie połączeniami, a następnie dodaje nowe wpisy zarządzania połączeniami dla serwera `www.contoso.com` i wszystkich innych hostów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="6249b-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <clear/>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6249b-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6249b-126">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="6249b-127">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="6249b-127">Network Settings Schema</span></span>](index.md)

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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088482"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="65aa7-102">\<clear>, element dla connectionManagement (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="65aa7-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="65aa7-103">Czyści listę zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="65aa7-103">Clears the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="65aa7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65aa7-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65aa7-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="65aa7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="65aa7-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="65aa7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65aa7-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="65aa7-107">Attributes</span></span>  
 <span data-ttu-id="65aa7-108">Brak.</span><span class="sxs-lookup"><span data-stu-id="65aa7-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="65aa7-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="65aa7-109">Child Elements</span></span>  
 <span data-ttu-id="65aa7-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="65aa7-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="65aa7-111">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="65aa7-111">Parent Elements</span></span>  
  
|<span data-ttu-id="65aa7-112">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="65aa7-112">**Element**</span></span>|<span data-ttu-id="65aa7-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="65aa7-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="65aa7-114">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="65aa7-114">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="65aa7-115">Określa maksymalną liczbę połączeń z hostem sieciowym.</span><span class="sxs-lookup"><span data-stu-id="65aa7-115">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65aa7-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65aa7-116">Remarks</span></span>  
 <span data-ttu-id="65aa7-117">`clear`Element czyści wszystkie wpisy z listy zarządzania połączeniami.</span><span class="sxs-lookup"><span data-stu-id="65aa7-117">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="65aa7-118">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="65aa7-118">Configuration Files</span></span>  
 <span data-ttu-id="65aa7-119">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="65aa7-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="65aa7-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="65aa7-120">Example</span></span>  
 <span data-ttu-id="65aa7-121">Poniższy przykład czyści listę zarządzanie połączeniami, a następnie dodaje nowe wpisy zarządzania połączeniami dla serwera `www.contoso.com` i wszystkich innych hostów sieciowych.</span><span class="sxs-lookup"><span data-stu-id="65aa7-121">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="65aa7-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65aa7-122">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="65aa7-123">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="65aa7-123">Network Settings Schema</span></span>](index.md)

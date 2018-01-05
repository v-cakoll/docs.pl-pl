---
title: "&lt;usługi NET.pipe&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76bb94ded07eb0c1b31285db7ae64f6670608bec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetpipegt"></a><span data-ttu-id="e7fd1-102">&lt;usługi NET.pipe&gt;</span><span class="sxs-lookup"><span data-stu-id="e7fd1-102">&lt;net.pipe&gt;</span></span>
<span data-ttu-id="e7fd1-103">Określa ustawienia konfiguracji dla nazwanych potoków aktywacji usługi, która zarządza czasem istnienia połączenia nazwanego potoku i obsługuje żądania aktywacyjne przychodzące za pośrednictwem nazwanych potoków.</span><span class="sxs-lookup"><span data-stu-id="e7fd1-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
 <span data-ttu-id="e7fd1-104">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="e7fd1-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="e7fd1-105">\<NET.pipe ></span><span class="sxs-lookup"><span data-stu-id="e7fd1-105">\<net.pipe></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7fd1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e7fd1-106">Syntax</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel.activation>  
       <net.pipe maxPendingAccepts="Integer"  
                    maxPendingConnections="Integer"  
          receiveTimeout="TimeSpan">  
          <allowAccounts>  
             // LocalSystem account  
             <add securityIdentifier="S-1-5-18"/>  
             // LocalService account  
             <add securityIdentifier="S-1-5-19"/>  
             // Administrators account  
             <add securityIdentifier="S-1-5-20"/>  
             // Network Service account  
             <add securityIdentifier="S-1-5-32-544" />  
             // IIS_IUSRS account (Vista only)  
             <add securityIdentifier="S-1-5-32-568"/>  
           </allowAccounts>  
       </net.pipe>  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## <a name="type"></a><span data-ttu-id="e7fd1-107">Typ</span><span class="sxs-lookup"><span data-stu-id="e7fd1-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7fd1-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e7fd1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e7fd1-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e7fd1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7fd1-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e7fd1-110">Attributes</span></span>  
  
|<span data-ttu-id="e7fd1-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e7fd1-111">Attribute</span></span>|<span data-ttu-id="e7fd1-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e7fd1-112">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="e7fd1-113">Liczba całkowita określająca maksymalną liczbę oczekujących współbieżnych wątków na punkcie końcowym nasłuchiwania dla usługi udostępniania.</span><span class="sxs-lookup"><span data-stu-id="e7fd1-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="e7fd1-114">Wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="e7fd1-114">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="e7fd1-115">Liczba całkowita określająca maksymalną liczbę połączeń, które mogą poczekać na wysłanie.</span><span class="sxs-lookup"><span data-stu-id="e7fd1-115">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="e7fd1-116">Wartość domyślna to 100.</span><span class="sxs-lookup"><span data-stu-id="e7fd1-116">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="e7fd1-117">A `TimeSpan` , który określa limit czasu dla odczytu danych z ramek i wykonania przekazania połączenia z połączeń podkreślonych.</span><span class="sxs-lookup"><span data-stu-id="e7fd1-117">A `TimeSpan` that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="e7fd1-118">Wartość domyślna to "00: 00:10"</span><span class="sxs-lookup"><span data-stu-id="e7fd1-118">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7fd1-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e7fd1-119">Child Elements</span></span>  
  
|<span data-ttu-id="e7fd1-120">Element</span><span class="sxs-lookup"><span data-stu-id="e7fd1-120">Element</span></span>|<span data-ttu-id="e7fd1-121">Opis</span><span class="sxs-lookup"><span data-stu-id="e7fd1-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7fd1-122">\<allowAccounts ></span><span class="sxs-lookup"><span data-stu-id="e7fd1-122">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="e7fd1-123">Kolekcja elementów konfiguracji, które zawierają `securityIdentifier` atrybutu, aby określić konta użytkowników dla procesów obsługujących [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług i przyznano im dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="e7fd1-123">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e7fd1-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e7fd1-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e7fd1-125">Element</span><span class="sxs-lookup"><span data-stu-id="e7fd1-125">Element</span></span>|<span data-ttu-id="e7fd1-126">Opis</span><span class="sxs-lookup"><span data-stu-id="e7fd1-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e7fd1-127">\<system.serviceModel.activation ></span><span class="sxs-lookup"><span data-stu-id="e7fd1-127">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="e7fd1-128">Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="e7fd1-128">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7fd1-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7fd1-129">See Also</span></span>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>

---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: 885cfad7be42f7c48b4c061f3293d667eb5d4ad8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103403"
---
# <a name="netpipe"></a><span data-ttu-id="18837-102">\<net.pipe></span><span class="sxs-lookup"><span data-stu-id="18837-102">\<net.pipe></span></span>
<span data-ttu-id="18837-103">Określa ustawienia konfiguracyjne o nazwie potoku aktywacji usługi, która zarządza czasem istnienia połączenia nazwanego potoku i obsługuje żądania aktywacyjne przychodzące za pośrednictwem nazwanych potoków.</span><span class="sxs-lookup"><span data-stu-id="18837-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
 <span data-ttu-id="18837-104">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="18837-104">\<system.serviceModel.activation></span></span>  
<span data-ttu-id="18837-105">\<net.pipe></span><span class="sxs-lookup"><span data-stu-id="18837-105">\<net.pipe></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18837-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="18837-106">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <net.pipe maxPendingAccepts="Integer"
              maxPendingConnections="Integer"
              receiveTimeout="TimeSpan">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="18837-107">Typ</span><span class="sxs-lookup"><span data-stu-id="18837-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18837-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="18837-108">Attributes and Elements</span></span>  
 <span data-ttu-id="18837-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="18837-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18837-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="18837-110">Attributes</span></span>  
  
|<span data-ttu-id="18837-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="18837-111">Attribute</span></span>|<span data-ttu-id="18837-112">Opis</span><span class="sxs-lookup"><span data-stu-id="18837-112">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="18837-113">Liczba całkowita określająca maksymalną liczbę oczekujących współbieżnych wątków na punkcie końcowym nasłuchiwania dla usługi udostępniania.</span><span class="sxs-lookup"><span data-stu-id="18837-113">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="18837-114">Wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="18837-114">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="18837-115">Liczba całkowita określająca maksymalną liczbę połączeń, które mogą poczekać na wysłanie.</span><span class="sxs-lookup"><span data-stu-id="18837-115">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="18837-116">Wartość domyślna to 100.</span><span class="sxs-lookup"><span data-stu-id="18837-116">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="18837-117">Element <xref:System.TimeSpan> , który określa limit czasu dla odczytu danych z ramek i wykonania przekazania połączenia z połączeń podkreślonych.</span><span class="sxs-lookup"><span data-stu-id="18837-117">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="18837-118">Wartość domyślna to "00: 00:10"</span><span class="sxs-lookup"><span data-stu-id="18837-118">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18837-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="18837-119">Child Elements</span></span>  
  
|<span data-ttu-id="18837-120">Element</span><span class="sxs-lookup"><span data-stu-id="18837-120">Element</span></span>|<span data-ttu-id="18837-121">Opis</span><span class="sxs-lookup"><span data-stu-id="18837-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18837-122">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="18837-122">\<allowAccounts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|<span data-ttu-id="18837-123">Kolekcja elementów konfiguracji, które zawierają `securityIdentifier` atrybutu, aby określić konta użytkowników dla procesów, które prowadzą hosting usług WCF i przyznano im dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="18837-123">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="18837-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="18837-124">Parent Elements</span></span>  
  
|<span data-ttu-id="18837-125">Element</span><span class="sxs-lookup"><span data-stu-id="18837-125">Element</span></span>|<span data-ttu-id="18837-126">Opis</span><span class="sxs-lookup"><span data-stu-id="18837-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18837-127">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="18837-127">\<system.serviceModel.activation></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|<span data-ttu-id="18837-128">Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="18837-128">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="18837-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="18837-129">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>

---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: dd984b2ab89060451b1b2d02c324e803766908ce
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397713"
---
# <a name="netpipe"></a><span data-ttu-id="54dec-102">\<> net. pipe</span><span class="sxs-lookup"><span data-stu-id="54dec-102">\<net.pipe></span></span>
<span data-ttu-id="54dec-103">Określa ustawienia konfiguracji dla usługi aktywacji potoków nazwanych, która zarządza okresem istnienia połączenia nazwanego potoku i obsługuje żądania aktywacji, które docierają do potoków nazwanych.</span><span class="sxs-lookup"><span data-stu-id="54dec-103">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
<span data-ttu-id="54dec-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="54dec-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="54dec-105">&nbsp;&nbsp;[ **\<> System. serviceModel. Activation**](system-servicemodel-activation.md)</span><span class="sxs-lookup"><span data-stu-id="54dec-105">&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)</span></span>\
<span data-ttu-id="54dec-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<> net. pipe**</span><span class="sxs-lookup"><span data-stu-id="54dec-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<net.pipe>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54dec-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="54dec-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="54dec-108">Typ</span><span class="sxs-lookup"><span data-stu-id="54dec-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54dec-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="54dec-109">Attributes and Elements</span></span>  
 <span data-ttu-id="54dec-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="54dec-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54dec-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="54dec-111">Attributes</span></span>  
  
|<span data-ttu-id="54dec-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="54dec-112">Attribute</span></span>|<span data-ttu-id="54dec-113">Opis</span><span class="sxs-lookup"><span data-stu-id="54dec-113">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="54dec-114">Liczba całkowita określająca maksymalną liczbę oczekujących współbieżnych wątków w punkcie końcowym nasłuchiwania dla usługi udostępniania.</span><span class="sxs-lookup"><span data-stu-id="54dec-114">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="54dec-115">Wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="54dec-115">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="54dec-116">Liczba całkowita określająca maksymalną liczbę połączeń, które mogą poczekać na wysłanie.</span><span class="sxs-lookup"><span data-stu-id="54dec-116">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="54dec-117">Wartość domyślna to 100.</span><span class="sxs-lookup"><span data-stu-id="54dec-117">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="54dec-118">Wartość <xref:System.TimeSpan> określająca limit czasu odczytu danych ramek i wykonywania operacji wysyłania połączenia z podkreśleń.</span><span class="sxs-lookup"><span data-stu-id="54dec-118">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="54dec-119">Wartość domyślna to "00:00:10"</span><span class="sxs-lookup"><span data-stu-id="54dec-119">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54dec-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="54dec-120">Child Elements</span></span>  
  
|<span data-ttu-id="54dec-121">Element</span><span class="sxs-lookup"><span data-stu-id="54dec-121">Element</span></span>|<span data-ttu-id="54dec-122">Opis</span><span class="sxs-lookup"><span data-stu-id="54dec-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54dec-123">\<allowAccounts></span><span class="sxs-lookup"><span data-stu-id="54dec-123">\<allowAccounts></span></span>](allowaccounts.md)|<span data-ttu-id="54dec-124">Kolekcja elementów konfiguracji, które zawierają `securityIdentifier` atrybut służący do określania kont użytkowników dla procesów, które obsługują usługi WCF i mają dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="54dec-124">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="54dec-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="54dec-125">Parent Elements</span></span>  
  
|<span data-ttu-id="54dec-126">Element</span><span class="sxs-lookup"><span data-stu-id="54dec-126">Element</span></span>|<span data-ttu-id="54dec-127">Opis</span><span class="sxs-lookup"><span data-stu-id="54dec-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54dec-128">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="54dec-128">\<system.serviceModel.activation></span></span>](system-servicemodel-activation.md)|<span data-ttu-id="54dec-129">Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="54dec-129">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="54dec-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54dec-130">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>

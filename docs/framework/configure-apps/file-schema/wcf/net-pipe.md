---
title: <net.pipe>
ms.date: 03/30/2017
ms.assetid: 6a0f0318-f8f6-466c-9fae-199d7274a82e
ms.openlocfilehash: dd984b2ab89060451b1b2d02c324e803766908ce
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397713"
---
# \<net.pipe>
<span data-ttu-id="2488c-102">Określa ustawienia konfiguracji dla usługi aktywacji potoków nazwanych, która zarządza okresem istnienia połączenia nazwanego potoku i obsługuje żądania aktywacji, które docierają do potoków nazwanych.</span><span class="sxs-lookup"><span data-stu-id="2488c-102">Specifies configuration settings for the Named Pipe Activation Service, which manages the lifetime of the named pipe connection, and handles activation requests that arrive over named pipes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<net.pipe>**  
  
## <a name="syntax"></a><span data-ttu-id="2488c-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="2488c-103">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="2488c-104">Typ</span><span class="sxs-lookup"><span data-stu-id="2488c-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2488c-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2488c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2488c-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2488c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2488c-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2488c-107">Attributes</span></span>  
  
|<span data-ttu-id="2488c-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2488c-108">Attribute</span></span>|<span data-ttu-id="2488c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2488c-109">Description</span></span>|  
|---------------|-----------------|  
|`maxPendingAccepts`|<span data-ttu-id="2488c-110">Liczba całkowita określająca maksymalną liczbę oczekujących współbieżnych wątków w punkcie końcowym nasłuchiwania dla usługi udostępniania.</span><span class="sxs-lookup"><span data-stu-id="2488c-110">An integer that specifies the maximum outstanding concurrent accepting threads on the listening endpoint for the sharing service.</span></span> <span data-ttu-id="2488c-111">Wartość domyślna to 2.</span><span class="sxs-lookup"><span data-stu-id="2488c-111">The default is 2.</span></span>|  
|`maxPendingConnections`|<span data-ttu-id="2488c-112">Liczba całkowita określająca maksymalną liczbę połączeń, które mogą poczekać na wysłanie.</span><span class="sxs-lookup"><span data-stu-id="2488c-112">An integer that specifies the maximum number of connections that can wait for dispatch.</span></span> <span data-ttu-id="2488c-113">Wartość domyślna to 100.</span><span class="sxs-lookup"><span data-stu-id="2488c-113">The default is 100.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="2488c-114">Wartość określająca <xref:System.TimeSpan> limit czasu odczytu danych ramek i wykonywania operacji wysyłania połączenia z podkreśleń.</span><span class="sxs-lookup"><span data-stu-id="2488c-114">A <xref:System.TimeSpan> that specifies the timeout for reading the framing data and performing connection dispatching from the underlining connections.</span></span> <span data-ttu-id="2488c-115">Wartość domyślna to "00:00:10"</span><span class="sxs-lookup"><span data-stu-id="2488c-115">The default is "00:00:10"</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2488c-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2488c-116">Child Elements</span></span>  
  
|<span data-ttu-id="2488c-117">Element</span><span class="sxs-lookup"><span data-stu-id="2488c-117">Element</span></span>|<span data-ttu-id="2488c-118">Opis</span><span class="sxs-lookup"><span data-stu-id="2488c-118">Description</span></span>|  
|-------------|-----------------|  
|[\<allowAccounts>](allowaccounts.md)|<span data-ttu-id="2488c-119">Kolekcja elementów konfiguracji, które zawierają atrybut służący `securityIdentifier` do określania kont użytkowników dla procesów, które obsługują usługi WCF i mają dostęp do połączenia z usługą udostępniania.</span><span class="sxs-lookup"><span data-stu-id="2488c-119">A collection of configuration elements that contain a `securityIdentifier` attribute to specify user accounts for processes that host WCF services, and are granted connection access to the sharing service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2488c-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2488c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2488c-121">Element</span><span class="sxs-lookup"><span data-stu-id="2488c-121">Element</span></span>|<span data-ttu-id="2488c-122">Opis</span><span class="sxs-lookup"><span data-stu-id="2488c-122">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="2488c-123">Zawiera ustawienia konfiguracji dla procesu odbiornika SMSvcHost. exe.</span><span class="sxs-lookup"><span data-stu-id="2488c-123">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2488c-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2488c-124">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.NetPipeSection>

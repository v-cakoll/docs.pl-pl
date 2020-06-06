---
title: <backupLists>
ms.date: 03/30/2017
ms.assetid: 593b3390-f65b-4684-ad40-0596b62f0954
ms.openlocfilehash: 5f2bb030d13389e15cb44f1ddff3b8168b4f2140
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850256"
---
# \<backupLists>
<span data-ttu-id="4a074-101">Reprezentuje sekcję konfiguracji definiującą zestaw usług kopii zapasowych używanych w obsłudze błędów.</span><span class="sxs-lookup"><span data-stu-id="4a074-101">Represents a configuration section for defining a set of backup services used in error handling.</span></span> <span data-ttu-id="4a074-102">Każdy element podrzędny to lista kopii zapasowych, która wylicza zestaw punktów końcowych, które mają być używane przez usługę routingu w przypadku, gdy podstawowy punkt końcowy nie zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="4a074-102">Each child element is a backup list that enumerates a set of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="4a074-103">Jeśli pierwszy punkt końcowy na liście nie działa, usługa routingu automatycznie przejdzie w tryb failover do kolejnej listy.</span><span class="sxs-lookup"><span data-stu-id="4a074-103">If the first endpoint in the list is down, the Routing Service will automatically fail-over to the next one in the list.</span></span>  <span data-ttu-id="4a074-104">Dzięki temu można szybko dodać niezawodność do aplikacji bez konieczności uczenia się aplikacji klienckiej, jak obsługiwać złożone wzorce lub wszystkie usługi są wdrażane.</span><span class="sxs-lookup"><span data-stu-id="4a074-104">This gives you a quick way to add reliability to your application without having to teach your client application how to handle complex patterns or where all of your services are deployed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<backupLists>**  
  
## <a name="syntax"></a><span data-ttu-id="4a074-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a074-105">Syntax</span></span>  
  
```xml  
<routing>
  <backupLists>
    <backupList name="String">
      <add endpointName="String" />
    </backupList>
  </backupLists>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a074-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4a074-106">Attributes and Elements</span></span>  
 <span data-ttu-id="4a074-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4a074-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a074-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4a074-108">Attributes</span></span>  
 <span data-ttu-id="4a074-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="4a074-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4a074-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4a074-110">Child Elements</span></span>  
  
|<span data-ttu-id="4a074-111">Element</span><span class="sxs-lookup"><span data-stu-id="4a074-111">Element</span></span>|<span data-ttu-id="4a074-112">Opis</span><span class="sxs-lookup"><span data-stu-id="4a074-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter.md)|<span data-ttu-id="4a074-113">Zawiera listę punktów końcowych, które mają być używane przez usługę routingu w przypadku, gdy podstawowy punkt końcowy nie zostanie osiągnięty.</span><span class="sxs-lookup"><span data-stu-id="4a074-113">Contains a list of endpoints that you would like the Routing Service to use in case the primary endpoint can't be reached.</span></span> <span data-ttu-id="4a074-114">.</span><span class="sxs-lookup"><span data-stu-id="4a074-114">.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a074-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4a074-115">Parent Elements</span></span>  
  
|<span data-ttu-id="4a074-116">Element</span><span class="sxs-lookup"><span data-stu-id="4a074-116">Element</span></span>|<span data-ttu-id="4a074-117">Opis</span><span class="sxs-lookup"><span data-stu-id="4a074-117">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="4a074-118">Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> , który ma być używany podczas oceniania wiadomości przychodzących, a także tabele routingu, które definiują docelowe punkty końcowe do wysyłania komunikatów, gdy filtr jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="4a074-118">Represents a configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a074-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a074-119">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.BackupEndpointCollection?displayProperty=nameWithType>

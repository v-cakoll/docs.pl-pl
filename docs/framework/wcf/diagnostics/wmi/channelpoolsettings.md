---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: d763be92243768bce9fdaefcd3e3575effac464b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200486"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="b6258-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="b6258-102">ChannelPoolSettings</span></span>
<span data-ttu-id="b6258-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="b6258-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6258-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6258-104">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b6258-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b6258-105">Methods</span></span>  
 <span data-ttu-id="b6258-106">Klasa ChannelPoolSettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="b6258-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b6258-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b6258-107">Properties</span></span>  
 <span data-ttu-id="b6258-108">Klasa ChannelPoolSettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="b6258-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="b6258-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="b6258-109">IdleTimeout</span></span>  
 <span data-ttu-id="b6258-110">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="b6258-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="b6258-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b6258-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b6258-112">Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="b6258-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="b6258-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="b6258-113">LeaseTimeout</span></span>  
 <span data-ttu-id="b6258-114">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="b6258-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="b6258-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b6258-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b6258-116">Maksymalny czas dzierżawy na zakończenie operacji przed przekroczeniem limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="b6258-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="b6258-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="b6258-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="b6258-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="b6258-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="b6258-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b6258-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b6258-120">Maksymalna liczba wychodzących kanałów dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="b6258-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6258-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6258-121">Requirements</span></span>  
  
|<span data-ttu-id="b6258-122">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="b6258-122">MOF</span></span>|<span data-ttu-id="b6258-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b6258-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b6258-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="b6258-124">Namespace</span></span>|<span data-ttu-id="b6258-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b6258-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6258-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b6258-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>

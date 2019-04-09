---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 8900af77d0d385bb68b4b85e1d15be57bb7a8d14
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131914"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="fb2eb-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="fb2eb-102">ChannelPoolSettings</span></span>
<span data-ttu-id="fb2eb-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="fb2eb-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb2eb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb2eb-104">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="fb2eb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fb2eb-105">Methods</span></span>  
 <span data-ttu-id="fb2eb-106">Klasa ChannelPoolSettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="fb2eb-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fb2eb-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="fb2eb-107">Properties</span></span>  
 <span data-ttu-id="fb2eb-108">Klasa ChannelPoolSettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="fb2eb-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="fb2eb-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="fb2eb-109">IdleTimeout</span></span>  
 <span data-ttu-id="fb2eb-110">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="fb2eb-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="fb2eb-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fb2eb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb2eb-112">Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="fb2eb-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="fb2eb-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="fb2eb-113">LeaseTimeout</span></span>  
 <span data-ttu-id="fb2eb-114">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="fb2eb-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="fb2eb-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fb2eb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb2eb-116">Maksymalny czas dzierżawy na zakończenie operacji przed przekroczeniem limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="fb2eb-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="fb2eb-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="fb2eb-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="fb2eb-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="fb2eb-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="fb2eb-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fb2eb-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fb2eb-120">Maksymalna liczba wychodzących kanałów dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="fb2eb-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb2eb-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fb2eb-121">Requirements</span></span>  
  
|<span data-ttu-id="fb2eb-122">MOF</span><span class="sxs-lookup"><span data-stu-id="fb2eb-122">MOF</span></span>|<span data-ttu-id="fb2eb-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="fb2eb-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fb2eb-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="fb2eb-124">Namespace</span></span>|<span data-ttu-id="fb2eb-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fb2eb-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb2eb-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb2eb-126">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelPoolSettings>

---
title: ChannelPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3995b517b27a5565f7fcb9c11da27c9e1bb40887
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="channelpoolsettings"></a><span data-ttu-id="f192a-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="f192a-102">ChannelPoolSettings</span></span>
<span data-ttu-id="f192a-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="f192a-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f192a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f192a-104">Syntax</span></span>  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f192a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f192a-105">Methods</span></span>  
 <span data-ttu-id="f192a-106">Klasa ChannelPoolSettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="f192a-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f192a-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f192a-107">Properties</span></span>  
 <span data-ttu-id="f192a-108">Klasa ChannelPoolSettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="f192a-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="f192a-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="f192a-109">IdleTimeout</span></span>  
 <span data-ttu-id="f192a-110">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="f192a-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="f192a-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f192a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f192a-112">Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="f192a-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="f192a-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="f192a-113">LeaseTimeout</span></span>  
 <span data-ttu-id="f192a-114">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="f192a-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="f192a-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f192a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f192a-116">Maksymalny czas na zakończenie przed przekroczeniem limitu czasu operacji dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="f192a-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="f192a-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="f192a-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="f192a-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="f192a-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="f192a-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f192a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f192a-120">Maksymalna liczba kanałów wychodzących dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f192a-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f192a-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f192a-121">Requirements</span></span>  
  
|<span data-ttu-id="f192a-122">MOF</span><span class="sxs-lookup"><span data-stu-id="f192a-122">MOF</span></span>|<span data-ttu-id="f192a-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f192a-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f192a-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="f192a-124">Namespace</span></span>|<span data-ttu-id="f192a-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f192a-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f192a-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f192a-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>

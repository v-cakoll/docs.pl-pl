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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0a56616e97526b2d410d18d97dc1391c6fc32cc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="channelpoolsettings"></a><span data-ttu-id="4504e-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="4504e-102">ChannelPoolSettings</span></span>
<span data-ttu-id="4504e-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="4504e-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4504e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4504e-104">Syntax</span></span>  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4504e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4504e-105">Methods</span></span>  
 <span data-ttu-id="4504e-106">Klasa ChannelPoolSettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="4504e-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4504e-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4504e-107">Properties</span></span>  
 <span data-ttu-id="4504e-108">Klasa ChannelPoolSettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="4504e-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="4504e-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="4504e-109">IdleTimeout</span></span>  
 <span data-ttu-id="4504e-110">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="4504e-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="4504e-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4504e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4504e-112">Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="4504e-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="4504e-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="4504e-113">LeaseTimeout</span></span>  
 <span data-ttu-id="4504e-114">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="4504e-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="4504e-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4504e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4504e-116">Maksymalny czas na zakończenie przed przekroczeniem limitu czasu operacji dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="4504e-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="4504e-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="4504e-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="4504e-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="4504e-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="4504e-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4504e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4504e-120">Maksymalna liczba kanałów wychodzących dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="4504e-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4504e-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4504e-121">Requirements</span></span>  
  
|<span data-ttu-id="4504e-122">MOF</span><span class="sxs-lookup"><span data-stu-id="4504e-122">MOF</span></span>|<span data-ttu-id="4504e-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4504e-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4504e-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="4504e-124">Namespace</span></span>|<span data-ttu-id="4504e-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4504e-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4504e-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4504e-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>

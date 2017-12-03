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
ms.openlocfilehash: e97e934673efbc6d0f72751c7cb1de6fba84a141
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="channelpoolsettings"></a><span data-ttu-id="3a54b-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="3a54b-102">ChannelPoolSettings</span></span>
<span data-ttu-id="3a54b-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="3a54b-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a54b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a54b-104">Syntax</span></span>  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3a54b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3a54b-105">Methods</span></span>  
 <span data-ttu-id="3a54b-106">Klasa ChannelPoolSettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="3a54b-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3a54b-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3a54b-107">Properties</span></span>  
 <span data-ttu-id="3a54b-108">Klasa ChannelPoolSettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="3a54b-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="3a54b-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="3a54b-109">IdleTimeout</span></span>  
 <span data-ttu-id="3a54b-110">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="3a54b-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="3a54b-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3a54b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a54b-112">Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="3a54b-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="3a54b-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="3a54b-113">LeaseTimeout</span></span>  
 <span data-ttu-id="3a54b-114">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="3a54b-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="3a54b-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3a54b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a54b-116">Maksymalny czas na zakończenie przed przekroczeniem limitu czasu operacji dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="3a54b-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="3a54b-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="3a54b-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="3a54b-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="3a54b-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="3a54b-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3a54b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a54b-120">Maksymalna liczba kanałów wychodzących dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="3a54b-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a54b-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a54b-121">Requirements</span></span>  
  
|<span data-ttu-id="3a54b-122">MOF</span><span class="sxs-lookup"><span data-stu-id="3a54b-122">MOF</span></span>|<span data-ttu-id="3a54b-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3a54b-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3a54b-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="3a54b-124">Namespace</span></span>|<span data-ttu-id="3a54b-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3a54b-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a54b-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a54b-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>

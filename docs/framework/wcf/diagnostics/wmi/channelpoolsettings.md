---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 48b41d2f3f45cd9c590f87151253450962b994de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="channelpoolsettings"></a><span data-ttu-id="eb872-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="eb872-102">ChannelPoolSettings</span></span>
<span data-ttu-id="eb872-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="eb872-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb872-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb872-104">Syntax</span></span>  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="eb872-105">Metody</span><span class="sxs-lookup"><span data-stu-id="eb872-105">Methods</span></span>  
 <span data-ttu-id="eb872-106">Klasa ChannelPoolSettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="eb872-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="eb872-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="eb872-107">Properties</span></span>  
 <span data-ttu-id="eb872-108">Klasa ChannelPoolSettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="eb872-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="eb872-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="eb872-109">IdleTimeout</span></span>  
 <span data-ttu-id="eb872-110">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="eb872-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="eb872-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="eb872-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eb872-112">Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="eb872-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="eb872-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="eb872-113">LeaseTimeout</span></span>  
 <span data-ttu-id="eb872-114">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="eb872-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="eb872-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="eb872-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eb872-116">Maksymalny czas na zakończenie przed przekroczeniem limitu czasu operacji dzierżawy.</span><span class="sxs-lookup"><span data-stu-id="eb872-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="eb872-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="eb872-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="eb872-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="eb872-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="eb872-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="eb872-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="eb872-120">Maksymalna liczba kanałów wychodzących dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="eb872-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb872-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eb872-121">Requirements</span></span>  
  
|<span data-ttu-id="eb872-122">MOF</span><span class="sxs-lookup"><span data-stu-id="eb872-122">MOF</span></span>|<span data-ttu-id="eb872-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="eb872-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="eb872-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="eb872-124">Namespace</span></span>|<span data-ttu-id="eb872-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="eb872-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eb872-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb872-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>

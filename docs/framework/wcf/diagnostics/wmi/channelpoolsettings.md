---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 4a3e45140765f99f4a30b77fc9d02b167601b50b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591484"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="74dbb-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="74dbb-102">ChannelPoolSettings</span></span>
<span data-ttu-id="74dbb-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="74dbb-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74dbb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="74dbb-104">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="74dbb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="74dbb-105">Methods</span></span>  
 <span data-ttu-id="74dbb-106">Klasa ChannelPoolSettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="74dbb-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="74dbb-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="74dbb-107">Properties</span></span>  
 <span data-ttu-id="74dbb-108">Klasa ChannelPoolSettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="74dbb-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="74dbb-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="74dbb-109">IdleTimeout</span></span>  
 <span data-ttu-id="74dbb-110">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="74dbb-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="74dbb-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="74dbb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74dbb-112">Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="74dbb-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="74dbb-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="74dbb-113">LeaseTimeout</span></span>  
 <span data-ttu-id="74dbb-114">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="74dbb-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="74dbb-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="74dbb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74dbb-116">Maksymalny czas dzierżawy na zakończenie operacji przed przekroczeniem limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="74dbb-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="74dbb-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="74dbb-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="74dbb-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="74dbb-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="74dbb-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="74dbb-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74dbb-120">Maksymalna liczba wychodzących kanałów dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="74dbb-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74dbb-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="74dbb-121">Requirements</span></span>  
  
|<span data-ttu-id="74dbb-122">MOF</span><span class="sxs-lookup"><span data-stu-id="74dbb-122">MOF</span></span>|<span data-ttu-id="74dbb-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="74dbb-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="74dbb-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="74dbb-124">Namespace</span></span>|<span data-ttu-id="74dbb-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="74dbb-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74dbb-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="74dbb-126">See also</span></span>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>

---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 8900af77d0d385bb68b4b85e1d15be57bb7a8d14
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59972865"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="7f2e3-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="7f2e3-102">ChannelPoolSettings</span></span>
<span data-ttu-id="7f2e3-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="7f2e3-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f2e3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f2e3-104">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7f2e3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7f2e3-105">Methods</span></span>  
 <span data-ttu-id="7f2e3-106">Klasa ChannelPoolSettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="7f2e3-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7f2e3-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="7f2e3-107">Properties</span></span>  
 <span data-ttu-id="7f2e3-108">Klasa ChannelPoolSettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="7f2e3-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="7f2e3-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="7f2e3-109">IdleTimeout</span></span>  
 <span data-ttu-id="7f2e3-110">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="7f2e3-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="7f2e3-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7f2e3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f2e3-112">Maksymalny czas, który połączenie może być bezczynne, zanim zostanie rozłączone.</span><span class="sxs-lookup"><span data-stu-id="7f2e3-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="7f2e3-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="7f2e3-113">LeaseTimeout</span></span>  
 <span data-ttu-id="7f2e3-114">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="7f2e3-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="7f2e3-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7f2e3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f2e3-116">Maksymalny czas dzierżawy na zakończenie operacji przed przekroczeniem limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="7f2e3-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="7f2e3-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="7f2e3-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="7f2e3-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="7f2e3-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="7f2e3-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="7f2e3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7f2e3-120">Maksymalna liczba wychodzących kanałów dla każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="7f2e3-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f2e3-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f2e3-121">Requirements</span></span>  
  
|<span data-ttu-id="7f2e3-122">MOF</span><span class="sxs-lookup"><span data-stu-id="7f2e3-122">MOF</span></span>|<span data-ttu-id="7f2e3-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7f2e3-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7f2e3-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="7f2e3-124">Namespace</span></span>|<span data-ttu-id="7f2e3-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7f2e3-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f2e3-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f2e3-126">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelPoolSettings>

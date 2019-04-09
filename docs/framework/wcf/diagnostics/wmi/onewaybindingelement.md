---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 016ff823eb2c84a9f54c0763edadef1224e31517
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168743"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="87445-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="87445-102">OneWayBindingElement</span></span>
<span data-ttu-id="87445-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="87445-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87445-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87445-104">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="87445-105">Metody</span><span class="sxs-lookup"><span data-stu-id="87445-105">Methods</span></span>  
 <span data-ttu-id="87445-106">Klasa element OneWayBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="87445-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="87445-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="87445-107">Properties</span></span>  
 <span data-ttu-id="87445-108">Klasa element OneWayBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="87445-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="87445-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="87445-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="87445-110">Typ danych: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="87445-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="87445-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="87445-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="87445-112">Ustawienia puli kanału.</span><span class="sxs-lookup"><span data-stu-id="87445-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="87445-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="87445-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="87445-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="87445-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="87445-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="87445-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="87445-116">Maksymalna liczba zaakceptowanych kanałów.</span><span class="sxs-lookup"><span data-stu-id="87445-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="87445-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="87445-117">PacketRoutable</span></span>  
 <span data-ttu-id="87445-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="87445-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="87445-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="87445-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="87445-120">Wartość, która wskazuje, czy pakiet jest routing.</span><span class="sxs-lookup"><span data-stu-id="87445-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87445-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87445-121">Requirements</span></span>  
  
|<span data-ttu-id="87445-122">MOF</span><span class="sxs-lookup"><span data-stu-id="87445-122">MOF</span></span>|<span data-ttu-id="87445-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="87445-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="87445-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="87445-124">Namespace</span></span>|<span data-ttu-id="87445-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="87445-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="87445-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87445-126">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>

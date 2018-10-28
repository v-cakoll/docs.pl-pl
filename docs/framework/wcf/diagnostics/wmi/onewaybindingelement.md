---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 34220a3651819978f5f597fdc67d54630ec5e059
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195817"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="29d1f-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="29d1f-102">OneWayBindingElement</span></span>
<span data-ttu-id="29d1f-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="29d1f-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29d1f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29d1f-104">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="29d1f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="29d1f-105">Methods</span></span>  
 <span data-ttu-id="29d1f-106">Klasa element OneWayBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="29d1f-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="29d1f-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="29d1f-107">Properties</span></span>  
 <span data-ttu-id="29d1f-108">Klasa element OneWayBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="29d1f-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="29d1f-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="29d1f-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="29d1f-110">Typ danych: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="29d1f-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="29d1f-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="29d1f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29d1f-112">Ustawienia puli kanału.</span><span class="sxs-lookup"><span data-stu-id="29d1f-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="29d1f-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="29d1f-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="29d1f-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="29d1f-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="29d1f-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="29d1f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29d1f-116">Maksymalna liczba zaakceptowanych kanałów.</span><span class="sxs-lookup"><span data-stu-id="29d1f-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="29d1f-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="29d1f-117">PacketRoutable</span></span>  
 <span data-ttu-id="29d1f-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="29d1f-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="29d1f-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="29d1f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29d1f-120">Wartość, która wskazuje, czy pakiet jest routing.</span><span class="sxs-lookup"><span data-stu-id="29d1f-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29d1f-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29d1f-121">Requirements</span></span>  
  
|<span data-ttu-id="29d1f-122">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="29d1f-122">MOF</span></span>|<span data-ttu-id="29d1f-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="29d1f-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="29d1f-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="29d1f-124">Namespace</span></span>|<span data-ttu-id="29d1f-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="29d1f-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29d1f-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29d1f-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>

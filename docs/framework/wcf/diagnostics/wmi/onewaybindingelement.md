---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: ee7cfed20234175ba54dd25dbbbab4615c1ed7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485763"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="1b18a-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="1b18a-102">OneWayBindingElement</span></span>
<span data-ttu-id="1b18a-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="1b18a-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b18a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b18a-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1b18a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1b18a-105">Methods</span></span>  
 <span data-ttu-id="1b18a-106">Element OneWayBindingElement klasa nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="1b18a-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1b18a-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1b18a-107">Properties</span></span>  
 <span data-ttu-id="1b18a-108">Klasa element OneWayBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="1b18a-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="1b18a-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="1b18a-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="1b18a-110">Typ danych: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="1b18a-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="1b18a-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1b18a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1b18a-112">Ustawienia puli kanałów.</span><span class="sxs-lookup"><span data-stu-id="1b18a-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="1b18a-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="1b18a-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="1b18a-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="1b18a-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="1b18a-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1b18a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1b18a-116">Maksymalna liczba zaakceptowanych kanałów.</span><span class="sxs-lookup"><span data-stu-id="1b18a-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="1b18a-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="1b18a-117">PacketRoutable</span></span>  
 <span data-ttu-id="1b18a-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="1b18a-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="1b18a-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1b18a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1b18a-120">Wartość, która wskazuje, czy pakiet jest rutowalny.</span><span class="sxs-lookup"><span data-stu-id="1b18a-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b18a-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b18a-121">Requirements</span></span>  
  
|<span data-ttu-id="1b18a-122">MOF</span><span class="sxs-lookup"><span data-stu-id="1b18a-122">MOF</span></span>|<span data-ttu-id="1b18a-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1b18a-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1b18a-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="1b18a-124">Namespace</span></span>|<span data-ttu-id="1b18a-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1b18a-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1b18a-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b18a-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>

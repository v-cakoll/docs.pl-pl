---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: d84184febd6db3f233aae6fe558b8e0f50a9cb82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608839"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="647ef-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="647ef-102">OneWayBindingElement</span></span>
<span data-ttu-id="647ef-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="647ef-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="647ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="647ef-104">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="647ef-105">Metody</span><span class="sxs-lookup"><span data-stu-id="647ef-105">Methods</span></span>  
 <span data-ttu-id="647ef-106">Klasa element OneWayBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="647ef-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="647ef-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="647ef-107">Properties</span></span>  
 <span data-ttu-id="647ef-108">Klasa element OneWayBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="647ef-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="647ef-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="647ef-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="647ef-110">Typ danych: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="647ef-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="647ef-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="647ef-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="647ef-112">Ustawienia puli kanału.</span><span class="sxs-lookup"><span data-stu-id="647ef-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="647ef-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="647ef-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="647ef-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="647ef-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="647ef-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="647ef-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="647ef-116">Maksymalna liczba zaakceptowanych kanałów.</span><span class="sxs-lookup"><span data-stu-id="647ef-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="647ef-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="647ef-117">PacketRoutable</span></span>  
 <span data-ttu-id="647ef-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="647ef-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="647ef-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="647ef-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="647ef-120">Wartość, która wskazuje, czy pakiet jest routing.</span><span class="sxs-lookup"><span data-stu-id="647ef-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="647ef-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="647ef-121">Requirements</span></span>  
  
|<span data-ttu-id="647ef-122">MOF</span><span class="sxs-lookup"><span data-stu-id="647ef-122">MOF</span></span>|<span data-ttu-id="647ef-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="647ef-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="647ef-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="647ef-124">Namespace</span></span>|<span data-ttu-id="647ef-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="647ef-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="647ef-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="647ef-126">See also</span></span>
- <xref:System.ServiceModel.Channels.OneWayBindingElement>

---
title: OneWayBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47de8c2449c46b12b8d10ac2a5269a18d1454f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="onewaybindingelement"></a><span data-ttu-id="dc9db-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="dc9db-102">OneWayBindingElement</span></span>
<span data-ttu-id="dc9db-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="dc9db-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc9db-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dc9db-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="dc9db-105">Metody</span><span class="sxs-lookup"><span data-stu-id="dc9db-105">Methods</span></span>  
 <span data-ttu-id="dc9db-106">Element OneWayBindingElement klasa nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="dc9db-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="dc9db-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="dc9db-107">Properties</span></span>  
 <span data-ttu-id="dc9db-108">Klasa element OneWayBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="dc9db-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="dc9db-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="dc9db-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="dc9db-110">Typ danych: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="dc9db-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="dc9db-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dc9db-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dc9db-112">Ustawienia puli kanałów.</span><span class="sxs-lookup"><span data-stu-id="dc9db-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="dc9db-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="dc9db-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="dc9db-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="dc9db-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="dc9db-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dc9db-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dc9db-116">Maksymalna liczba zaakceptowanych kanałów.</span><span class="sxs-lookup"><span data-stu-id="dc9db-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="dc9db-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="dc9db-117">PacketRoutable</span></span>  
 <span data-ttu-id="dc9db-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="dc9db-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="dc9db-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dc9db-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dc9db-120">Wartość, która wskazuje, czy pakiet jest rutowalny.</span><span class="sxs-lookup"><span data-stu-id="dc9db-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc9db-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dc9db-121">Requirements</span></span>  
  
|<span data-ttu-id="dc9db-122">MOF</span><span class="sxs-lookup"><span data-stu-id="dc9db-122">MOF</span></span>|<span data-ttu-id="dc9db-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="dc9db-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="dc9db-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="dc9db-124">Namespace</span></span>|<span data-ttu-id="dc9db-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="dc9db-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc9db-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc9db-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>

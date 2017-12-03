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
ms.openlocfilehash: abaacfb6541d41019a8d0cd6df53913c6b7911f2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="onewaybindingelement"></a><span data-ttu-id="92a13-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="92a13-102">OneWayBindingElement</span></span>
<span data-ttu-id="92a13-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="92a13-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92a13-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92a13-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="92a13-105">Metody</span><span class="sxs-lookup"><span data-stu-id="92a13-105">Methods</span></span>  
 <span data-ttu-id="92a13-106">Element OneWayBindingElement klasa nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="92a13-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="92a13-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="92a13-107">Properties</span></span>  
 <span data-ttu-id="92a13-108">Klasa element OneWayBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="92a13-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="92a13-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="92a13-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="92a13-110">Typ danych: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="92a13-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="92a13-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="92a13-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="92a13-112">Ustawienia puli kanałów.</span><span class="sxs-lookup"><span data-stu-id="92a13-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="92a13-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="92a13-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="92a13-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="92a13-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="92a13-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="92a13-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="92a13-116">Maksymalna liczba zaakceptowanych kanałów.</span><span class="sxs-lookup"><span data-stu-id="92a13-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="92a13-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="92a13-117">PacketRoutable</span></span>  
 <span data-ttu-id="92a13-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="92a13-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="92a13-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="92a13-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="92a13-120">Wartość, która wskazuje, czy pakiet jest rutowalny.</span><span class="sxs-lookup"><span data-stu-id="92a13-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92a13-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92a13-121">Requirements</span></span>  
  
|<span data-ttu-id="92a13-122">MOF</span><span class="sxs-lookup"><span data-stu-id="92a13-122">MOF</span></span>|<span data-ttu-id="92a13-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="92a13-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="92a13-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="92a13-124">Namespace</span></span>|<span data-ttu-id="92a13-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="92a13-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92a13-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92a13-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>

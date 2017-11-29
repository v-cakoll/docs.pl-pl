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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a43707f25a9ee1beb1ce7adac36a2c4a55cab6d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="onewaybindingelement"></a><span data-ttu-id="141ef-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="141ef-102">OneWayBindingElement</span></span>
<span data-ttu-id="141ef-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="141ef-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="141ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="141ef-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="141ef-105">Metody</span><span class="sxs-lookup"><span data-stu-id="141ef-105">Methods</span></span>  
 <span data-ttu-id="141ef-106">Element OneWayBindingElement klasa nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="141ef-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="141ef-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="141ef-107">Properties</span></span>  
 <span data-ttu-id="141ef-108">Klasa element OneWayBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="141ef-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="141ef-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="141ef-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="141ef-110">Typ danych: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="141ef-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="141ef-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="141ef-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="141ef-112">Ustawienia puli kanałów.</span><span class="sxs-lookup"><span data-stu-id="141ef-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="141ef-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="141ef-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="141ef-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="141ef-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="141ef-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="141ef-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="141ef-116">Maksymalna liczba zaakceptowanych kanałów.</span><span class="sxs-lookup"><span data-stu-id="141ef-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="141ef-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="141ef-117">PacketRoutable</span></span>  
 <span data-ttu-id="141ef-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="141ef-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="141ef-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="141ef-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="141ef-120">Wartość, która wskazuje, czy pakiet jest rutowalny.</span><span class="sxs-lookup"><span data-stu-id="141ef-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="141ef-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="141ef-121">Requirements</span></span>  
  
|<span data-ttu-id="141ef-122">MOF</span><span class="sxs-lookup"><span data-stu-id="141ef-122">MOF</span></span>|<span data-ttu-id="141ef-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="141ef-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="141ef-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="141ef-124">Namespace</span></span>|<span data-ttu-id="141ef-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="141ef-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="141ef-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="141ef-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>

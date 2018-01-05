---
title: MsmqTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c4cfa3d58127fa560f39ce0dcfe51b97ded6223a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="701dd-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="701dd-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="701dd-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="701dd-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="701dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="701dd-104">Syntax</span></span>  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="701dd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="701dd-105">Methods</span></span>  
 <span data-ttu-id="701dd-106">Klasa elementem MsmqTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="701dd-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="701dd-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="701dd-107">Properties</span></span>  
 <span data-ttu-id="701dd-108">Klasa elementem MsmqTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="701dd-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="701dd-109">maxPoolSize</span><span class="sxs-lookup"><span data-stu-id="701dd-109">MaxPoolSize</span></span>  
 <span data-ttu-id="701dd-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="701dd-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="701dd-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="701dd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="701dd-112">Maksymalny rozmiar puli zawierającej wewnętrzne obiekty komunikatów MSMQ.</span><span class="sxs-lookup"><span data-stu-id="701dd-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="701dd-113">Właściwość queueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="701dd-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="701dd-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="701dd-114">Data type: string</span></span>  
  
 <span data-ttu-id="701dd-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="701dd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="701dd-116">Wartość wyliczenia wskazująca kolejkowany kanał komunikacyjny transportu przez to wiązanie.</span><span class="sxs-lookup"><span data-stu-id="701dd-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="701dd-117">Właściwość UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="701dd-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="701dd-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="701dd-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="701dd-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="701dd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="701dd-120">Zwraca wartość logiczną, wskazującą, czy adresy kolejek powinny być konwertowane przy użyciu usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="701dd-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="701dd-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="701dd-121">Requirements</span></span>  
  
|<span data-ttu-id="701dd-122">MOF</span><span class="sxs-lookup"><span data-stu-id="701dd-122">MOF</span></span>|<span data-ttu-id="701dd-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="701dd-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="701dd-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="701dd-124">Namespace</span></span>|<span data-ttu-id="701dd-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="701dd-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="701dd-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="701dd-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

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
ms.openlocfilehash: 572a19723583a6bc717a71b3b46040148f29e1cd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="b149f-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b149f-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="b149f-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b149f-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b149f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b149f-104">Syntax</span></span>  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b149f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b149f-105">Methods</span></span>  
 <span data-ttu-id="b149f-106">Klasa elementem MsmqTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="b149f-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b149f-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b149f-107">Properties</span></span>  
 <span data-ttu-id="b149f-108">Klasa elementem MsmqTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="b149f-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="b149f-109">maxPoolSize</span><span class="sxs-lookup"><span data-stu-id="b149f-109">MaxPoolSize</span></span>  
 <span data-ttu-id="b149f-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="b149f-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="b149f-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b149f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b149f-112">Maksymalny rozmiar puli zawierającej wewnętrzne obiekty komunikatów MSMQ.</span><span class="sxs-lookup"><span data-stu-id="b149f-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="b149f-113">Właściwość queueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="b149f-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="b149f-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="b149f-114">Data type: string</span></span>  
  
 <span data-ttu-id="b149f-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b149f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b149f-116">Wartość wyliczenia wskazująca kolejkowany kanał komunikacyjny transportu przez to wiązanie.</span><span class="sxs-lookup"><span data-stu-id="b149f-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="b149f-117">Właściwość UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="b149f-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="b149f-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="b149f-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="b149f-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b149f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b149f-120">Zwraca wartość logiczną, wskazującą, czy adresy kolejek powinny być konwertowane przy użyciu usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b149f-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b149f-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b149f-121">Requirements</span></span>  
  
|<span data-ttu-id="b149f-122">MOF</span><span class="sxs-lookup"><span data-stu-id="b149f-122">MOF</span></span>|<span data-ttu-id="b149f-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b149f-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b149f-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="b149f-124">Namespace</span></span>|<span data-ttu-id="b149f-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b149f-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b149f-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b149f-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

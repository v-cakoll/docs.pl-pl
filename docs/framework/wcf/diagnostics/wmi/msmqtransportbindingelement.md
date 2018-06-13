---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 643ab0f30c771f79df8ef7dd885013d5186fba59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485911"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="a5098-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="a5098-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="a5098-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="a5098-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5098-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5098-104">Syntax</span></span>  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a5098-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a5098-105">Methods</span></span>  
 <span data-ttu-id="a5098-106">Klasa elementem MsmqTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="a5098-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a5098-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a5098-107">Properties</span></span>  
 <span data-ttu-id="a5098-108">Klasa elementem MsmqTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="a5098-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="a5098-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="a5098-109">MaxPoolSize</span></span>  
 <span data-ttu-id="a5098-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="a5098-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="a5098-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a5098-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a5098-112">Maksymalny rozmiar puli zawierającej wewnętrzne obiekty komunikatów MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a5098-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="a5098-113">Właściwość queueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="a5098-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="a5098-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="a5098-114">Data type: string</span></span>  
  
 <span data-ttu-id="a5098-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a5098-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a5098-116">Wartość wyliczenia wskazująca kolejkowany kanał komunikacyjny transportu przez to wiązanie.</span><span class="sxs-lookup"><span data-stu-id="a5098-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="a5098-117">Właściwość UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="a5098-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="a5098-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="a5098-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="a5098-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="a5098-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a5098-120">Zwraca wartość logiczną, wskazującą, czy adresy kolejek powinny być konwertowane przy użyciu usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="a5098-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5098-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5098-121">Requirements</span></span>  
  
|<span data-ttu-id="a5098-122">MOF</span><span class="sxs-lookup"><span data-stu-id="a5098-122">MOF</span></span>|<span data-ttu-id="a5098-123">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a5098-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a5098-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="a5098-124">Namespace</span></span>|<span data-ttu-id="a5098-125">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a5098-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a5098-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5098-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

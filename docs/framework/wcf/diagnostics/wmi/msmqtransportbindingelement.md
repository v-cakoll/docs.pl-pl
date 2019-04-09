---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 706cec5c414197ebabda7939728b95be32582e0f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197935"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="42d4a-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="42d4a-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="42d4a-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="42d4a-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42d4a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="42d4a-104">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="42d4a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="42d4a-105">Methods</span></span>  
 <span data-ttu-id="42d4a-106">Klasa elementem MsmqTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="42d4a-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="42d4a-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="42d4a-107">Properties</span></span>  
 <span data-ttu-id="42d4a-108">Klasa elementem MsmqTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="42d4a-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="42d4a-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="42d4a-109">MaxPoolSize</span></span>  
 <span data-ttu-id="42d4a-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="42d4a-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="42d4a-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="42d4a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="42d4a-112">Maksymalny rozmiar puli, która zawiera obiekty wewnętrzne wiadomości usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="42d4a-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="42d4a-113">QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="42d4a-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="42d4a-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="42d4a-114">Data type: string</span></span>  
  
 <span data-ttu-id="42d4a-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="42d4a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="42d4a-116">Wartość wyliczenia, która wskazuje kanał transportowy komunikacji z obsługą kolejek, który używa tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="42d4a-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="42d4a-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="42d4a-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="42d4a-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="42d4a-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="42d4a-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="42d4a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="42d4a-120">Zwraca wartość logiczną wskazującą, czy adresy kolejki powinny być konwertowane przy użyciu usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="42d4a-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42d4a-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="42d4a-121">Requirements</span></span>  
  
|<span data-ttu-id="42d4a-122">MOF</span><span class="sxs-lookup"><span data-stu-id="42d4a-122">MOF</span></span>|<span data-ttu-id="42d4a-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="42d4a-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="42d4a-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="42d4a-124">Namespace</span></span>|<span data-ttu-id="42d4a-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="42d4a-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="42d4a-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42d4a-126">See also</span></span>

- <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

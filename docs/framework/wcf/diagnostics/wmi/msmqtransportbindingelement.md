---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 33cd9c427ed5ad04eaf9e9889f60f091f335d1e7
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50045991"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="408f5-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="408f5-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="408f5-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="408f5-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="408f5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="408f5-104">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="408f5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="408f5-105">Methods</span></span>  
 <span data-ttu-id="408f5-106">Klasa elementem MsmqTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="408f5-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="408f5-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="408f5-107">Properties</span></span>  
 <span data-ttu-id="408f5-108">Klasa elementem MsmqTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="408f5-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="408f5-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="408f5-109">MaxPoolSize</span></span>  
 <span data-ttu-id="408f5-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="408f5-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="408f5-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="408f5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="408f5-112">Maksymalny rozmiar puli, która zawiera obiekty wewnętrzne wiadomości usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="408f5-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="408f5-113">Właściwość queueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="408f5-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="408f5-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="408f5-114">Data type: string</span></span>  
  
 <span data-ttu-id="408f5-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="408f5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="408f5-116">Wartość wyliczenia, która wskazuje kanał transportowy komunikacji z obsługą kolejek, który używa tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="408f5-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="408f5-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="408f5-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="408f5-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="408f5-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="408f5-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="408f5-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="408f5-120">Zwraca wartość logiczną wskazującą, czy adresy kolejki powinny być konwertowane przy użyciu usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="408f5-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="408f5-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="408f5-121">Requirements</span></span>  
  
|<span data-ttu-id="408f5-122">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="408f5-122">MOF</span></span>|<span data-ttu-id="408f5-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="408f5-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="408f5-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="408f5-124">Namespace</span></span>|<span data-ttu-id="408f5-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="408f5-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="408f5-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="408f5-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

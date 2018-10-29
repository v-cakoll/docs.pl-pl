---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 33cd9c427ed5ad04eaf9e9889f60f091f335d1e7
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198110"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="6607f-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="6607f-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="6607f-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="6607f-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6607f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6607f-104">Syntax</span></span>  
  
```csharp
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6607f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6607f-105">Methods</span></span>  
 <span data-ttu-id="6607f-106">Klasa elementem MsmqTransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="6607f-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6607f-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="6607f-107">Properties</span></span>  
 <span data-ttu-id="6607f-108">Klasa elementem MsmqTransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="6607f-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="6607f-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="6607f-109">MaxPoolSize</span></span>  
 <span data-ttu-id="6607f-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="6607f-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="6607f-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6607f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6607f-112">Maksymalny rozmiar puli, która zawiera obiekty wewnętrzne wiadomości usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6607f-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="6607f-113">Właściwość queueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="6607f-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="6607f-114">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="6607f-114">Data type: string</span></span>  
  
 <span data-ttu-id="6607f-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6607f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6607f-116">Wartość wyliczenia, która wskazuje kanał transportowy komunikacji z obsługą kolejek, który używa tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="6607f-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="6607f-117">UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="6607f-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="6607f-118">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="6607f-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="6607f-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6607f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6607f-120">Zwraca wartość logiczną wskazującą, czy adresy kolejki powinny być konwertowane przy użyciu usługi Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6607f-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6607f-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6607f-121">Requirements</span></span>  
  
|<span data-ttu-id="6607f-122">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="6607f-122">MOF</span></span>|<span data-ttu-id="6607f-123">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6607f-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6607f-124">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="6607f-124">Namespace</span></span>|<span data-ttu-id="6607f-125">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6607f-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6607f-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6607f-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

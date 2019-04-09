---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: bdb5ca7400a41dd724c2ad7fc76695a82874ded6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112375"
---
# <a name="transportbindingelement"></a><span data-ttu-id="b31d2-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b31d2-102">TransportBindingElement</span></span>
<span data-ttu-id="b31d2-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="b31d2-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b31d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b31d2-104">Syntax</span></span>  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b31d2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b31d2-105">Methods</span></span>  
 <span data-ttu-id="b31d2-106">Klasa elementu TransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="b31d2-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b31d2-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b31d2-107">Properties</span></span>  
 <span data-ttu-id="b31d2-108">Klasa elementu TransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="b31d2-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="b31d2-109">opcję manualAddressing</span><span class="sxs-lookup"><span data-stu-id="b31d2-109">ManualAddressing</span></span>  
 <span data-ttu-id="b31d2-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="b31d2-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="b31d2-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b31d2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b31d2-112">Wartość logiczna określająca, czy użytkownik chce, aby przejąć kontrolę nad adresowaniem komunikatów.</span><span class="sxs-lookup"><span data-stu-id="b31d2-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="b31d2-113">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="b31d2-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="b31d2-114">Typ danych: sint64</span><span class="sxs-lookup"><span data-stu-id="b31d2-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="b31d2-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b31d2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b31d2-116">Maksymalny rozmiar puli buforów dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="b31d2-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="b31d2-117">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="b31d2-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="b31d2-118">Typ danych: sint64</span><span class="sxs-lookup"><span data-stu-id="b31d2-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="b31d2-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b31d2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b31d2-120">Maksymalny rozmiar komunikatu, który jest przetwarzany przez to wiązanie.</span><span class="sxs-lookup"><span data-stu-id="b31d2-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="b31d2-121">Schemat</span><span class="sxs-lookup"><span data-stu-id="b31d2-121">Scheme</span></span>  
 <span data-ttu-id="b31d2-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="b31d2-122">Data type: string</span></span>  
  
 <span data-ttu-id="b31d2-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b31d2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b31d2-124">Schemat identyfikatora URI dla transportu.</span><span class="sxs-lookup"><span data-stu-id="b31d2-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b31d2-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b31d2-125">Requirements</span></span>  
  
|<span data-ttu-id="b31d2-126">MOF</span><span class="sxs-lookup"><span data-stu-id="b31d2-126">MOF</span></span>|<span data-ttu-id="b31d2-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b31d2-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b31d2-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="b31d2-128">Namespace</span></span>|<span data-ttu-id="b31d2-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b31d2-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b31d2-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b31d2-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TransportBindingElement>

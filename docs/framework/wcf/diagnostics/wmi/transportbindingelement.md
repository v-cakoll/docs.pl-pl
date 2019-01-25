---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 303e5523befb68c65bc50ee3933af58897929363
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668460"
---
# <a name="transportbindingelement"></a><span data-ttu-id="43f1a-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="43f1a-102">TransportBindingElement</span></span>
<span data-ttu-id="43f1a-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="43f1a-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43f1a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43f1a-104">Syntax</span></span>  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="43f1a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="43f1a-105">Methods</span></span>  
 <span data-ttu-id="43f1a-106">Klasa elementu TransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="43f1a-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="43f1a-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="43f1a-107">Properties</span></span>  
 <span data-ttu-id="43f1a-108">Klasa elementu TransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="43f1a-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="43f1a-109">opcję manualAddressing</span><span class="sxs-lookup"><span data-stu-id="43f1a-109">ManualAddressing</span></span>  
 <span data-ttu-id="43f1a-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="43f1a-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="43f1a-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="43f1a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43f1a-112">Wartość logiczna określająca, czy użytkownik chce, aby przejąć kontrolę nad adresowaniem komunikatów.</span><span class="sxs-lookup"><span data-stu-id="43f1a-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="43f1a-113">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="43f1a-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="43f1a-114">Typ danych: sint64</span><span class="sxs-lookup"><span data-stu-id="43f1a-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="43f1a-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="43f1a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43f1a-116">Maksymalny rozmiar puli buforów dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="43f1a-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="43f1a-117">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="43f1a-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="43f1a-118">Typ danych: sint64</span><span class="sxs-lookup"><span data-stu-id="43f1a-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="43f1a-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="43f1a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43f1a-120">Maksymalny rozmiar komunikatu, który jest przetwarzany przez to wiązanie.</span><span class="sxs-lookup"><span data-stu-id="43f1a-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="43f1a-121">Schemat</span><span class="sxs-lookup"><span data-stu-id="43f1a-121">Scheme</span></span>  
 <span data-ttu-id="43f1a-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="43f1a-122">Data type: string</span></span>  
  
 <span data-ttu-id="43f1a-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="43f1a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43f1a-124">Schemat identyfikatora URI dla transportu.</span><span class="sxs-lookup"><span data-stu-id="43f1a-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43f1a-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43f1a-125">Requirements</span></span>  
  
|<span data-ttu-id="43f1a-126">MOF</span><span class="sxs-lookup"><span data-stu-id="43f1a-126">MOF</span></span>|<span data-ttu-id="43f1a-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="43f1a-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="43f1a-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="43f1a-128">Namespace</span></span>|<span data-ttu-id="43f1a-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="43f1a-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43f1a-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43f1a-130">See also</span></span>
- <xref:System.ServiceModel.Channels.TransportBindingElement>

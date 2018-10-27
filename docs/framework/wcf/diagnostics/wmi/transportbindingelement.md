---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: 79d8b1f4a5127ca36eb57954cff6ee6a97e55e41
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182661"
---
# <a name="transportbindingelement"></a><span data-ttu-id="df881-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="df881-102">TransportBindingElement</span></span>
<span data-ttu-id="df881-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="df881-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df881-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="df881-104">Syntax</span></span>  
  
```csharp
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="df881-105">Metody</span><span class="sxs-lookup"><span data-stu-id="df881-105">Methods</span></span>  
 <span data-ttu-id="df881-106">Klasa elementu TransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="df881-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="df881-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="df881-107">Properties</span></span>  
 <span data-ttu-id="df881-108">Klasa elementu TransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="df881-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="df881-109">opcję manualAddressing</span><span class="sxs-lookup"><span data-stu-id="df881-109">ManualAddressing</span></span>  
 <span data-ttu-id="df881-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="df881-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="df881-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="df881-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="df881-112">Wartość logiczna określająca, czy użytkownik chce, aby przejąć kontrolę nad adresowaniem komunikatów.</span><span class="sxs-lookup"><span data-stu-id="df881-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="df881-113">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="df881-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="df881-114">Typ danych: sint64</span><span class="sxs-lookup"><span data-stu-id="df881-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="df881-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="df881-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="df881-116">Maksymalny rozmiar puli buforów dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="df881-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="df881-117">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="df881-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="df881-118">Typ danych: sint64</span><span class="sxs-lookup"><span data-stu-id="df881-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="df881-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="df881-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="df881-120">Maksymalny rozmiar komunikatu, który jest przetwarzany przez to wiązanie.</span><span class="sxs-lookup"><span data-stu-id="df881-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="df881-121">Schemat</span><span class="sxs-lookup"><span data-stu-id="df881-121">Scheme</span></span>  
 <span data-ttu-id="df881-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="df881-122">Data type: string</span></span>  
  
 <span data-ttu-id="df881-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="df881-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="df881-124">Schemat identyfikatora URI dla transportu.</span><span class="sxs-lookup"><span data-stu-id="df881-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df881-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df881-125">Requirements</span></span>  
  
|<span data-ttu-id="df881-126">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="df881-126">MOF</span></span>|<span data-ttu-id="df881-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="df881-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="df881-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="df881-128">Namespace</span></span>|<span data-ttu-id="df881-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="df881-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df881-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df881-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>

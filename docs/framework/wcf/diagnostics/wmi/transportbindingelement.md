---
title: TransportBindingElement
ms.date: 03/30/2017
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
ms.openlocfilehash: dc7a29e5911a9d0a774e36f5be8c1f3cacad69b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486620"
---
# <a name="transportbindingelement"></a><span data-ttu-id="e51ad-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e51ad-102">TransportBindingElement</span></span>
<span data-ttu-id="e51ad-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e51ad-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e51ad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e51ad-104">Syntax</span></span>  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e51ad-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e51ad-105">Methods</span></span>  
 <span data-ttu-id="e51ad-106">Klasy TransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="e51ad-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e51ad-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e51ad-107">Properties</span></span>  
 <span data-ttu-id="e51ad-108">Klasy TransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="e51ad-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="e51ad-109">Opcję ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="e51ad-109">ManualAddressing</span></span>  
 <span data-ttu-id="e51ad-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="e51ad-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="e51ad-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e51ad-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e51ad-112">Wartość logiczna określająca, czy użytkownik chce przejąć kontrolę nad adresowaniem komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e51ad-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="e51ad-113">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="e51ad-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="e51ad-114">Typ danych: sint64</span><span class="sxs-lookup"><span data-stu-id="e51ad-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="e51ad-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e51ad-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e51ad-116">Maksymalny rozmiar puli buforów powiązania.</span><span class="sxs-lookup"><span data-stu-id="e51ad-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="e51ad-117">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="e51ad-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="e51ad-118">Typ danych: sint64</span><span class="sxs-lookup"><span data-stu-id="e51ad-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="e51ad-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e51ad-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e51ad-120">Maksymalny rozmiar komunikatu przetwarzanego przez to powiązanie.</span><span class="sxs-lookup"><span data-stu-id="e51ad-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="e51ad-121">Schemat</span><span class="sxs-lookup"><span data-stu-id="e51ad-121">Scheme</span></span>  
 <span data-ttu-id="e51ad-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="e51ad-122">Data type: string</span></span>  
  
 <span data-ttu-id="e51ad-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e51ad-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e51ad-124">Schemat identyfikatora URI dla transportu.</span><span class="sxs-lookup"><span data-stu-id="e51ad-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e51ad-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e51ad-125">Requirements</span></span>  
  
|<span data-ttu-id="e51ad-126">MOF</span><span class="sxs-lookup"><span data-stu-id="e51ad-126">MOF</span></span>|<span data-ttu-id="e51ad-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e51ad-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e51ad-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="e51ad-128">Namespace</span></span>|<span data-ttu-id="e51ad-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e51ad-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e51ad-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e51ad-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>

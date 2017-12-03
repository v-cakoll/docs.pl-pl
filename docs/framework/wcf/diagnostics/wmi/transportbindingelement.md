---
title: TransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c2605e1a1f88434a9052059ac3ebdce429d6d6c8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="transportbindingelement"></a><span data-ttu-id="37805-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="37805-102">TransportBindingElement</span></span>
<span data-ttu-id="37805-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="37805-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37805-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="37805-104">Syntax</span></span>  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="37805-105">Metody</span><span class="sxs-lookup"><span data-stu-id="37805-105">Methods</span></span>  
 <span data-ttu-id="37805-106">Klasy TransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="37805-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="37805-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="37805-107">Properties</span></span>  
 <span data-ttu-id="37805-108">Klasy TransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="37805-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="37805-109">Opcję ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="37805-109">ManualAddressing</span></span>  
 <span data-ttu-id="37805-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="37805-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="37805-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="37805-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37805-112">Wartość logiczna określająca, czy użytkownik chce przejąć kontrolę nad adresowaniem komunikatów.</span><span class="sxs-lookup"><span data-stu-id="37805-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="37805-113">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="37805-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="37805-114">Typ danych: sint64</span><span class="sxs-lookup"><span data-stu-id="37805-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="37805-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="37805-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37805-116">Maksymalny rozmiar puli buforów powiązania.</span><span class="sxs-lookup"><span data-stu-id="37805-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="37805-117">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="37805-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="37805-118">Typ danych: sint64</span><span class="sxs-lookup"><span data-stu-id="37805-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="37805-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="37805-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37805-120">Maksymalny rozmiar komunikatu przetwarzanego przez to powiązanie.</span><span class="sxs-lookup"><span data-stu-id="37805-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="37805-121">Schemat</span><span class="sxs-lookup"><span data-stu-id="37805-121">Scheme</span></span>  
 <span data-ttu-id="37805-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="37805-122">Data type: string</span></span>  
  
 <span data-ttu-id="37805-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="37805-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37805-124">Schemat identyfikatora URI dla transportu.</span><span class="sxs-lookup"><span data-stu-id="37805-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37805-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37805-125">Requirements</span></span>  
  
|<span data-ttu-id="37805-126">MOF</span><span class="sxs-lookup"><span data-stu-id="37805-126">MOF</span></span>|<span data-ttu-id="37805-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="37805-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="37805-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="37805-128">Namespace</span></span>|<span data-ttu-id="37805-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="37805-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37805-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37805-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>

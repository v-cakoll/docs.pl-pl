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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c130093b9600c324e7179febce6857341b8a7d3c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="transportbindingelement"></a><span data-ttu-id="c1ef1-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c1ef1-102">TransportBindingElement</span></span>
<span data-ttu-id="c1ef1-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="c1ef1-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1ef1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1ef1-104">Syntax</span></span>  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c1ef1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c1ef1-105">Methods</span></span>  
 <span data-ttu-id="c1ef1-106">Klasy TransportBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="c1ef1-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c1ef1-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c1ef1-107">Properties</span></span>  
 <span data-ttu-id="c1ef1-108">Klasy TransportBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="c1ef1-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="c1ef1-109">Opcję ManualAddressing</span><span class="sxs-lookup"><span data-stu-id="c1ef1-109">ManualAddressing</span></span>  
 <span data-ttu-id="c1ef1-110">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="c1ef1-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="c1ef1-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c1ef1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1ef1-112">Wartość logiczna określająca, czy użytkownik chce przejąć kontrolę nad adresowaniem komunikatów.</span><span class="sxs-lookup"><span data-stu-id="c1ef1-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="c1ef1-113">MaxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="c1ef1-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="c1ef1-114">Typ danych: sint64</span><span class="sxs-lookup"><span data-stu-id="c1ef1-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="c1ef1-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c1ef1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1ef1-116">Maksymalny rozmiar puli buforów powiązania.</span><span class="sxs-lookup"><span data-stu-id="c1ef1-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="c1ef1-117">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="c1ef1-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="c1ef1-118">Typ danych: sint64</span><span class="sxs-lookup"><span data-stu-id="c1ef1-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="c1ef1-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c1ef1-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1ef1-120">Maksymalny rozmiar komunikatu przetwarzanego przez to powiązanie.</span><span class="sxs-lookup"><span data-stu-id="c1ef1-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="c1ef1-121">Schemat</span><span class="sxs-lookup"><span data-stu-id="c1ef1-121">Scheme</span></span>  
 <span data-ttu-id="c1ef1-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="c1ef1-122">Data type: string</span></span>  
  
 <span data-ttu-id="c1ef1-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c1ef1-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c1ef1-124">Schemat identyfikatora URI dla transportu.</span><span class="sxs-lookup"><span data-stu-id="c1ef1-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1ef1-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c1ef1-125">Requirements</span></span>  
  
|<span data-ttu-id="c1ef1-126">MOF</span><span class="sxs-lookup"><span data-stu-id="c1ef1-126">MOF</span></span>|<span data-ttu-id="c1ef1-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c1ef1-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c1ef1-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="c1ef1-128">Namespace</span></span>|<span data-ttu-id="c1ef1-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c1ef1-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1ef1-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1ef1-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>

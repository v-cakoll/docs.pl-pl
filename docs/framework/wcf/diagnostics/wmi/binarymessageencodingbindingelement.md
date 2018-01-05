---
title: BinaryMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: adac65808853ec75e37245c8c9fa031a533c22a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="48b70-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="48b70-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="48b70-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="48b70-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48b70-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="48b70-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="48b70-105">Metody</span><span class="sxs-lookup"><span data-stu-id="48b70-105">Methods</span></span>  
 <span data-ttu-id="48b70-106">Klasa elementu BinaryMessageEncodingBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="48b70-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="48b70-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="48b70-107">Properties</span></span>  
 <span data-ttu-id="48b70-108">Klasa elementu BinaryMessageEncodingBindingElement ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="48b70-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="48b70-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="48b70-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="48b70-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="48b70-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="48b70-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="48b70-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="48b70-112">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="48b70-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="48b70-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="48b70-113">MaxSessionSize</span></span>  
 <span data-ttu-id="48b70-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="48b70-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="48b70-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="48b70-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="48b70-116">Wartość, która określa rozmiar w bajtach buforu używany do kodowania.</span><span class="sxs-lookup"><span data-stu-id="48b70-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="48b70-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="48b70-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="48b70-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="48b70-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="48b70-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="48b70-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="48b70-120">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="48b70-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="48b70-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="48b70-121">ReaderQuotas</span></span>  
 <span data-ttu-id="48b70-122">Typ danych: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="48b70-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="48b70-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="48b70-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="48b70-124">Przydziały czytników.</span><span class="sxs-lookup"><span data-stu-id="48b70-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48b70-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="48b70-125">Requirements</span></span>  
  
|<span data-ttu-id="48b70-126">MOF</span><span class="sxs-lookup"><span data-stu-id="48b70-126">MOF</span></span>|<span data-ttu-id="48b70-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="48b70-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="48b70-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="48b70-128">Namespace</span></span>|<span data-ttu-id="48b70-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="48b70-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="48b70-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48b70-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 09d43ed76ef70f4478aa1029c254a7b1686a8d08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="c2daf-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="c2daf-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="c2daf-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="c2daf-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2daf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2daf-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c2daf-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c2daf-105">Methods</span></span>  
 <span data-ttu-id="c2daf-106">Klasa elementu BinaryMessageEncodingBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="c2daf-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c2daf-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c2daf-107">Properties</span></span>  
 <span data-ttu-id="c2daf-108">Klasa elementu BinaryMessageEncodingBindingElement ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="c2daf-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="c2daf-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="c2daf-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="c2daf-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="c2daf-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="c2daf-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c2daf-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c2daf-112">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="c2daf-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="c2daf-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="c2daf-113">MaxSessionSize</span></span>  
 <span data-ttu-id="c2daf-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="c2daf-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="c2daf-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c2daf-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c2daf-116">Wartość, która określa rozmiar w bajtach buforu używany do kodowania.</span><span class="sxs-lookup"><span data-stu-id="c2daf-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="c2daf-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="c2daf-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="c2daf-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="c2daf-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="c2daf-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c2daf-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c2daf-120">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="c2daf-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="c2daf-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="c2daf-121">ReaderQuotas</span></span>  
 <span data-ttu-id="c2daf-122">Typ danych: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="c2daf-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="c2daf-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c2daf-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c2daf-124">Przydziały czytników.</span><span class="sxs-lookup"><span data-stu-id="c2daf-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2daf-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c2daf-125">Requirements</span></span>  
  
|<span data-ttu-id="c2daf-126">MOF</span><span class="sxs-lookup"><span data-stu-id="c2daf-126">MOF</span></span>|<span data-ttu-id="c2daf-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c2daf-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c2daf-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="c2daf-128">Namespace</span></span>|<span data-ttu-id="c2daf-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c2daf-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2daf-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2daf-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

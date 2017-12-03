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
ms.openlocfilehash: 45f80b9ac7ca052ea3a8d7d89b35413b167eacfa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="26f54-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="26f54-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="26f54-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="26f54-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26f54-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26f54-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="26f54-105">Metody</span><span class="sxs-lookup"><span data-stu-id="26f54-105">Methods</span></span>  
 <span data-ttu-id="26f54-106">Klasa elementu BinaryMessageEncodingBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="26f54-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="26f54-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="26f54-107">Properties</span></span>  
 <span data-ttu-id="26f54-108">Klasa elementu BinaryMessageEncodingBindingElement ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="26f54-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="26f54-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="26f54-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="26f54-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="26f54-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="26f54-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="26f54-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="26f54-112">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="26f54-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="26f54-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="26f54-113">MaxSessionSize</span></span>  
 <span data-ttu-id="26f54-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="26f54-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="26f54-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="26f54-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="26f54-116">Wartość, która określa rozmiar w bajtach buforu używany do kodowania.</span><span class="sxs-lookup"><span data-stu-id="26f54-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="26f54-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="26f54-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="26f54-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="26f54-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="26f54-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="26f54-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="26f54-120">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="26f54-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="26f54-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="26f54-121">ReaderQuotas</span></span>  
 <span data-ttu-id="26f54-122">Typ danych: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="26f54-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="26f54-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="26f54-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="26f54-124">Przydziały czytników.</span><span class="sxs-lookup"><span data-stu-id="26f54-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26f54-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26f54-125">Requirements</span></span>  
  
|<span data-ttu-id="26f54-126">MOF</span><span class="sxs-lookup"><span data-stu-id="26f54-126">MOF</span></span>|<span data-ttu-id="26f54-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="26f54-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="26f54-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="26f54-128">Namespace</span></span>|<span data-ttu-id="26f54-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="26f54-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="26f54-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26f54-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

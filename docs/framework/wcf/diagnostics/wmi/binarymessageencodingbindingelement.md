---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: 03a33f01fe6b6f75e81749c96c31770009350b05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486566"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="e5cbe-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="e5cbe-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="e5cbe-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="e5cbe-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5cbe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5cbe-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e5cbe-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e5cbe-105">Methods</span></span>  
 <span data-ttu-id="e5cbe-106">Klasa elementu BinaryMessageEncodingBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="e5cbe-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e5cbe-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="e5cbe-107">Properties</span></span>  
 <span data-ttu-id="e5cbe-108">Klasa elementu BinaryMessageEncodingBindingElement ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="e5cbe-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="e5cbe-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="e5cbe-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="e5cbe-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="e5cbe-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="e5cbe-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e5cbe-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5cbe-112">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="e5cbe-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="e5cbe-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="e5cbe-113">MaxSessionSize</span></span>  
 <span data-ttu-id="e5cbe-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="e5cbe-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e5cbe-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e5cbe-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5cbe-116">Wartość, która określa rozmiar w bajtach buforu używany do kodowania.</span><span class="sxs-lookup"><span data-stu-id="e5cbe-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="e5cbe-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="e5cbe-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="e5cbe-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="e5cbe-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="e5cbe-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e5cbe-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5cbe-120">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="e5cbe-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="e5cbe-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="e5cbe-121">ReaderQuotas</span></span>  
 <span data-ttu-id="e5cbe-122">Typ danych: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="e5cbe-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="e5cbe-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="e5cbe-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5cbe-124">Przydziały czytników.</span><span class="sxs-lookup"><span data-stu-id="e5cbe-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5cbe-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e5cbe-125">Requirements</span></span>  
  
|<span data-ttu-id="e5cbe-126">MOF</span><span class="sxs-lookup"><span data-stu-id="e5cbe-126">MOF</span></span>|<span data-ttu-id="e5cbe-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e5cbe-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e5cbe-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="e5cbe-128">Namespace</span></span>|<span data-ttu-id="e5cbe-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e5cbe-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5cbe-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5cbe-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

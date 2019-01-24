---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: 330496d5f0f80affcb6bc44a1f66f4321a635f00
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580593"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="2a4f2-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="2a4f2-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="2a4f2-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="2a4f2-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a4f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a4f2-104">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2a4f2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2a4f2-105">Methods</span></span>  
 <span data-ttu-id="2a4f2-106">Klasa BinaryMessageEncodingBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="2a4f2-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2a4f2-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="2a4f2-107">Properties</span></span>  
 <span data-ttu-id="2a4f2-108">Klasa BinaryMessageEncodingBindingElement ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="2a4f2-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="2a4f2-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="2a4f2-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="2a4f2-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="2a4f2-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="2a4f2-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="2a4f2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a4f2-112">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="2a4f2-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="2a4f2-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="2a4f2-113">MaxSessionSize</span></span>  
 <span data-ttu-id="2a4f2-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="2a4f2-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="2a4f2-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="2a4f2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a4f2-116">Wartość, która określa rozmiar w bajtach buforu używany do kodowania.</span><span class="sxs-lookup"><span data-stu-id="2a4f2-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="2a4f2-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="2a4f2-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="2a4f2-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="2a4f2-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="2a4f2-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="2a4f2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a4f2-120">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="2a4f2-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="2a4f2-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="2a4f2-121">ReaderQuotas</span></span>  
 <span data-ttu-id="2a4f2-122">Typ danych: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="2a4f2-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="2a4f2-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="2a4f2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2a4f2-124">Przydziały czytników.</span><span class="sxs-lookup"><span data-stu-id="2a4f2-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a4f2-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2a4f2-125">Requirements</span></span>  
  
|<span data-ttu-id="2a4f2-126">MOF</span><span class="sxs-lookup"><span data-stu-id="2a4f2-126">MOF</span></span>|<span data-ttu-id="2a4f2-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2a4f2-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2a4f2-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="2a4f2-128">Namespace</span></span>|<span data-ttu-id="2a4f2-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2a4f2-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a4f2-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a4f2-130">See also</span></span>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

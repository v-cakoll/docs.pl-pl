---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: e0551e7b4b05151490625912742aa6b26ef0216e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145681"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="94f6c-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="94f6c-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="94f6c-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="94f6c-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94f6c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="94f6c-104">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="94f6c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="94f6c-105">Methods</span></span>  
 <span data-ttu-id="94f6c-106">Klasa BinaryMessageEncodingBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="94f6c-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="94f6c-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="94f6c-107">Properties</span></span>  
 <span data-ttu-id="94f6c-108">Klasa BinaryMessageEncodingBindingElement ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="94f6c-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="94f6c-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="94f6c-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="94f6c-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="94f6c-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="94f6c-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="94f6c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94f6c-112">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="94f6c-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="94f6c-113">MaxSessionSize</span><span class="sxs-lookup"><span data-stu-id="94f6c-113">MaxSessionSize</span></span>  
 <span data-ttu-id="94f6c-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="94f6c-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="94f6c-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="94f6c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94f6c-116">Wartość, która określa rozmiar w bajtach buforu używany do kodowania.</span><span class="sxs-lookup"><span data-stu-id="94f6c-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="94f6c-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="94f6c-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="94f6c-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="94f6c-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="94f6c-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="94f6c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94f6c-120">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="94f6c-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="94f6c-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="94f6c-121">ReaderQuotas</span></span>  
 <span data-ttu-id="94f6c-122">Typ danych: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="94f6c-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="94f6c-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="94f6c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94f6c-124">Przydziały czytników.</span><span class="sxs-lookup"><span data-stu-id="94f6c-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94f6c-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94f6c-125">Requirements</span></span>  
  
|<span data-ttu-id="94f6c-126">MOF</span><span class="sxs-lookup"><span data-stu-id="94f6c-126">MOF</span></span>|<span data-ttu-id="94f6c-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="94f6c-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="94f6c-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="94f6c-128">Namespace</span></span>|<span data-ttu-id="94f6c-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="94f6c-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94f6c-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94f6c-130">See also</span></span>

- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

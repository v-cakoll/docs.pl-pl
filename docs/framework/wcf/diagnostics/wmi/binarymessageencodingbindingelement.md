---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: 326fe6a7ca8dc5dba0dd64b1c5fc97cec49279c7
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180890"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="dab06-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="dab06-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="dab06-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="dab06-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dab06-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dab06-104">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="dab06-105">Metody</span><span class="sxs-lookup"><span data-stu-id="dab06-105">Methods</span></span>  
 <span data-ttu-id="dab06-106">Klasa BinaryMessageEncodingBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="dab06-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="dab06-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="dab06-107">Properties</span></span>  
 <span data-ttu-id="dab06-108">Klasa BinaryMessageEncodingBindingElement ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="dab06-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="dab06-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="dab06-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="dab06-110">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="dab06-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="dab06-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dab06-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dab06-112">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="dab06-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="dab06-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="dab06-113">MaxSessionSize</span></span>  
 <span data-ttu-id="dab06-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="dab06-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="dab06-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dab06-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dab06-116">Wartość, która określa rozmiar w bajtach buforu używany do kodowania.</span><span class="sxs-lookup"><span data-stu-id="dab06-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="dab06-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="dab06-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="dab06-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="dab06-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="dab06-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dab06-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dab06-120">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="dab06-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="dab06-121">readerQuotas</span><span class="sxs-lookup"><span data-stu-id="dab06-121">ReaderQuotas</span></span>  
 <span data-ttu-id="dab06-122">Typ danych: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="dab06-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="dab06-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="dab06-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dab06-124">Przydziały czytników.</span><span class="sxs-lookup"><span data-stu-id="dab06-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dab06-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dab06-125">Requirements</span></span>  
  
|<span data-ttu-id="dab06-126">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="dab06-126">MOF</span></span>|<span data-ttu-id="dab06-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="dab06-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="dab06-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="dab06-128">Namespace</span></span>|<span data-ttu-id="dab06-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="dab06-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dab06-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dab06-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

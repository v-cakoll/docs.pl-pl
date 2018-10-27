---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: 49a640a666131491366646d6d486d25a515e35bf
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185709"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="1ecec-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="1ecec-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="1ecec-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="1ecec-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ecec-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ecec-104">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1ecec-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1ecec-105">Methods</span></span>  
 <span data-ttu-id="1ecec-106">Klasa MtomMessageEncodingBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="1ecec-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1ecec-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1ecec-107">Properties</span></span>  
 <span data-ttu-id="1ecec-108">Klasa MtomMessageEncodingBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="1ecec-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="1ecec-109">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="1ecec-109">Encoding</span></span>  
 <span data-ttu-id="1ecec-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="1ecec-110">Data type: string</span></span>  
  
 <span data-ttu-id="1ecec-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1ecec-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ecec-112">Kodowanie do użycia dla emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="1ecec-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="1ecec-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="1ecec-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="1ecec-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="1ecec-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="1ecec-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1ecec-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ecec-116">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="1ecec-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="1ecec-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="1ecec-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="1ecec-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="1ecec-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="1ecec-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1ecec-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ecec-120">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="1ecec-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="1ecec-121">readerQuotas</span><span class="sxs-lookup"><span data-stu-id="1ecec-121">ReaderQuotas</span></span>  
 <span data-ttu-id="1ecec-122">Typ danych: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="1ecec-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="1ecec-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="1ecec-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1ecec-124">Przydziały czytników.</span><span class="sxs-lookup"><span data-stu-id="1ecec-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ecec-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ecec-125">Requirements</span></span>  
  
|<span data-ttu-id="1ecec-126">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="1ecec-126">MOF</span></span>|<span data-ttu-id="1ecec-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1ecec-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1ecec-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="1ecec-128">Namespace</span></span>|<span data-ttu-id="1ecec-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1ecec-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ecec-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ecec-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

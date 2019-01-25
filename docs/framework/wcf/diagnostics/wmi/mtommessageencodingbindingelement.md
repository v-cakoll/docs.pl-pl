---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: ad4f2cc3b03111854d10d6a1c1128f090a629a07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490985"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="b1f38-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="b1f38-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="b1f38-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="b1f38-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1f38-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1f38-104">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b1f38-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b1f38-105">Methods</span></span>  
 <span data-ttu-id="b1f38-106">Klasa MtomMessageEncodingBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="b1f38-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b1f38-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b1f38-107">Properties</span></span>  
 <span data-ttu-id="b1f38-108">Klasa MtomMessageEncodingBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="b1f38-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="b1f38-109">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="b1f38-109">Encoding</span></span>  
 <span data-ttu-id="b1f38-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="b1f38-110">Data type: string</span></span>  
  
 <span data-ttu-id="b1f38-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b1f38-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1f38-112">Kodowanie do użycia dla emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="b1f38-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="b1f38-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="b1f38-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="b1f38-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="b1f38-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="b1f38-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b1f38-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1f38-116">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="b1f38-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="b1f38-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="b1f38-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="b1f38-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="b1f38-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="b1f38-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b1f38-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1f38-120">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="b1f38-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="b1f38-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="b1f38-121">ReaderQuotas</span></span>  
 <span data-ttu-id="b1f38-122">Typ danych: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="b1f38-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="b1f38-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="b1f38-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b1f38-124">Przydziały czytników.</span><span class="sxs-lookup"><span data-stu-id="b1f38-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1f38-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1f38-125">Requirements</span></span>  
  
|<span data-ttu-id="b1f38-126">MOF</span><span class="sxs-lookup"><span data-stu-id="b1f38-126">MOF</span></span>|<span data-ttu-id="b1f38-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b1f38-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b1f38-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="b1f38-128">Namespace</span></span>|<span data-ttu-id="b1f38-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b1f38-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1f38-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1f38-130">See also</span></span>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

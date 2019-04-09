---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 67c1083daa9acfd204d4de50d4e9178b25aafcf0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097489"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="4377d-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="4377d-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="4377d-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="4377d-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4377d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4377d-104">Syntax</span></span>  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4377d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4377d-105">Methods</span></span>  
 <span data-ttu-id="4377d-106">Klasa TextMessageEncodingBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="4377d-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4377d-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4377d-107">Properties</span></span>  
 <span data-ttu-id="4377d-108">Klasa TextMessageEncodingBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="4377d-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="4377d-109">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="4377d-109">Encoding</span></span>  
 <span data-ttu-id="4377d-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4377d-110">Data type: string</span></span>  
  
 <span data-ttu-id="4377d-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4377d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4377d-112">Kodowanie do użycia dla emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="4377d-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="4377d-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="4377d-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="4377d-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="4377d-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="4377d-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4377d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4377d-116">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="4377d-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="4377d-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="4377d-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="4377d-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="4377d-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="4377d-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4377d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4377d-120">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="4377d-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="4377d-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4377d-121">ReaderQuotas</span></span>  
 <span data-ttu-id="4377d-122">Typ danych: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4377d-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="4377d-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4377d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4377d-124">Przydziały czytników.</span><span class="sxs-lookup"><span data-stu-id="4377d-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4377d-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4377d-125">Requirements</span></span>  
  
|<span data-ttu-id="4377d-126">MOF</span><span class="sxs-lookup"><span data-stu-id="4377d-126">MOF</span></span>|<span data-ttu-id="4377d-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4377d-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4377d-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="4377d-128">Namespace</span></span>|<span data-ttu-id="4377d-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4377d-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4377d-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4377d-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

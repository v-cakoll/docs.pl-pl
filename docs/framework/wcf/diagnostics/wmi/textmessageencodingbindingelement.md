---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 188a766807cd779ac51df390b1332641584dbb06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662715"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="019e7-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="019e7-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="019e7-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="019e7-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="019e7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="019e7-104">Syntax</span></span>  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="019e7-105">Metody</span><span class="sxs-lookup"><span data-stu-id="019e7-105">Methods</span></span>  
 <span data-ttu-id="019e7-106">Klasa TextMessageEncodingBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="019e7-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="019e7-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="019e7-107">Properties</span></span>  
 <span data-ttu-id="019e7-108">Klasa TextMessageEncodingBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="019e7-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="019e7-109">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="019e7-109">Encoding</span></span>  
 <span data-ttu-id="019e7-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="019e7-110">Data type: string</span></span>  
  
 <span data-ttu-id="019e7-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="019e7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="019e7-112">Kodowanie do użycia dla emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="019e7-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="019e7-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="019e7-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="019e7-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="019e7-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="019e7-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="019e7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="019e7-116">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="019e7-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="019e7-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="019e7-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="019e7-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="019e7-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="019e7-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="019e7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="019e7-120">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="019e7-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="019e7-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="019e7-121">ReaderQuotas</span></span>  
 <span data-ttu-id="019e7-122">Typ danych: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="019e7-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="019e7-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="019e7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="019e7-124">Przydziały czytników.</span><span class="sxs-lookup"><span data-stu-id="019e7-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="019e7-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="019e7-125">Requirements</span></span>  
  
|<span data-ttu-id="019e7-126">MOF</span><span class="sxs-lookup"><span data-stu-id="019e7-126">MOF</span></span>|<span data-ttu-id="019e7-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="019e7-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="019e7-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="019e7-128">Namespace</span></span>|<span data-ttu-id="019e7-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="019e7-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="019e7-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="019e7-130">See also</span></span>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 2371c38aebe2bd8d6da93d702801556fad986ef9
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452576"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="52009-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="52009-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="52009-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="52009-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52009-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="52009-104">Syntax</span></span>  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="52009-105">Metody</span><span class="sxs-lookup"><span data-stu-id="52009-105">Methods</span></span>  
 <span data-ttu-id="52009-106">Klasa TextMessageEncodingBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="52009-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="52009-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="52009-107">Properties</span></span>  
 <span data-ttu-id="52009-108">Klasa TextMessageEncodingBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="52009-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="52009-109">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="52009-109">Encoding</span></span>  
 <span data-ttu-id="52009-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="52009-110">Data type: string</span></span>  
  
 <span data-ttu-id="52009-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="52009-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52009-112">Kodowanie do użycia dla emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="52009-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="52009-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="52009-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="52009-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="52009-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="52009-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="52009-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52009-116">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="52009-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="52009-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="52009-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="52009-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="52009-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="52009-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="52009-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52009-120">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="52009-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="52009-121">readerQuotas</span><span class="sxs-lookup"><span data-stu-id="52009-121">ReaderQuotas</span></span>  
 <span data-ttu-id="52009-122">Typ danych: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="52009-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="52009-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="52009-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52009-124">Przydziały czytników.</span><span class="sxs-lookup"><span data-stu-id="52009-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52009-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="52009-125">Requirements</span></span>  
  
|<span data-ttu-id="52009-126">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="52009-126">MOF</span></span>|<span data-ttu-id="52009-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="52009-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="52009-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="52009-128">Namespace</span></span>|<span data-ttu-id="52009-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="52009-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52009-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="52009-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

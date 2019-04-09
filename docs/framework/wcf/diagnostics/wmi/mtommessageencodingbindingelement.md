---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: aed65311d2b36a5dc764511de04e34c4bfb69d7b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140481"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="055d6-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="055d6-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="055d6-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="055d6-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="055d6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="055d6-104">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="055d6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="055d6-105">Methods</span></span>  
 <span data-ttu-id="055d6-106">Klasa MtomMessageEncodingBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="055d6-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="055d6-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="055d6-107">Properties</span></span>  
 <span data-ttu-id="055d6-108">Klasa MtomMessageEncodingBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="055d6-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="055d6-109">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="055d6-109">Encoding</span></span>  
 <span data-ttu-id="055d6-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="055d6-110">Data type: string</span></span>  
  
 <span data-ttu-id="055d6-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="055d6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="055d6-112">Kodowanie do użycia dla emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="055d6-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="055d6-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="055d6-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="055d6-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="055d6-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="055d6-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="055d6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="055d6-116">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="055d6-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="055d6-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="055d6-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="055d6-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="055d6-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="055d6-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="055d6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="055d6-120">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="055d6-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="055d6-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="055d6-121">ReaderQuotas</span></span>  
 <span data-ttu-id="055d6-122">Typ danych: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="055d6-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="055d6-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="055d6-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="055d6-124">Przydziały czytników.</span><span class="sxs-lookup"><span data-stu-id="055d6-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="055d6-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="055d6-125">Requirements</span></span>  
  
|<span data-ttu-id="055d6-126">MOF</span><span class="sxs-lookup"><span data-stu-id="055d6-126">MOF</span></span>|<span data-ttu-id="055d6-127">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="055d6-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="055d6-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="055d6-128">Namespace</span></span>|<span data-ttu-id="055d6-129">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="055d6-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="055d6-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="055d6-130">See also</span></span>

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

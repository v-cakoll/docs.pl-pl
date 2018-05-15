---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: 83fa879fbef94e2dc9c142dfb92a51a54a7b60cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="05514-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="05514-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="05514-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="05514-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05514-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="05514-104">Syntax</span></span>  
  
```  
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="05514-105">Metody</span><span class="sxs-lookup"><span data-stu-id="05514-105">Methods</span></span>  
 <span data-ttu-id="05514-106">Klasa MtomMessageEncodingBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="05514-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="05514-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="05514-107">Properties</span></span>  
 <span data-ttu-id="05514-108">Klasa MtomMessageEncodingBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="05514-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="05514-109">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="05514-109">Encoding</span></span>  
 <span data-ttu-id="05514-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="05514-110">Data type: string</span></span>  
  
 <span data-ttu-id="05514-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="05514-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="05514-112">Zestaw znaków kodowania używanego w celu emisji komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="05514-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="05514-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="05514-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="05514-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="05514-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="05514-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="05514-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="05514-116">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="05514-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="05514-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="05514-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="05514-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="05514-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="05514-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="05514-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="05514-120">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="05514-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="05514-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="05514-121">ReaderQuotas</span></span>  
 <span data-ttu-id="05514-122">Typ danych: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="05514-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="05514-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="05514-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="05514-124">Przydziały czytników.</span><span class="sxs-lookup"><span data-stu-id="05514-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05514-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05514-125">Requirements</span></span>  
  
|<span data-ttu-id="05514-126">MOF</span><span class="sxs-lookup"><span data-stu-id="05514-126">MOF</span></span>|<span data-ttu-id="05514-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="05514-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="05514-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="05514-128">Namespace</span></span>|<span data-ttu-id="05514-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="05514-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="05514-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05514-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

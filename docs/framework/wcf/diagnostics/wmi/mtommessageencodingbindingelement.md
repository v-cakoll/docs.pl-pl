---
title: MtomMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3cc36d7daed1a2cfaf050cbfe9661951117ff66d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="9a0ac-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="9a0ac-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="9a0ac-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="9a0ac-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a0ac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a0ac-104">Syntax</span></span>  
  
```  
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="9a0ac-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9a0ac-105">Methods</span></span>  
 <span data-ttu-id="9a0ac-106">Klasa MtomMessageEncodingBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="9a0ac-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9a0ac-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="9a0ac-107">Properties</span></span>  
 <span data-ttu-id="9a0ac-108">Klasa MtomMessageEncodingBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="9a0ac-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="9a0ac-109">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="9a0ac-109">Encoding</span></span>  
 <span data-ttu-id="9a0ac-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="9a0ac-110">Data type: string</span></span>  
  
 <span data-ttu-id="9a0ac-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9a0ac-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9a0ac-112">Zestaw znaków kodowania używanego w celu emisji komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="9a0ac-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="9a0ac-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="9a0ac-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="9a0ac-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="9a0ac-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="9a0ac-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9a0ac-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9a0ac-116">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="9a0ac-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="9a0ac-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="9a0ac-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="9a0ac-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="9a0ac-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="9a0ac-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9a0ac-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9a0ac-120">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="9a0ac-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="9a0ac-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="9a0ac-121">ReaderQuotas</span></span>  
 <span data-ttu-id="9a0ac-122">Typ danych: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="9a0ac-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="9a0ac-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9a0ac-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9a0ac-124">Przydziały czytników.</span><span class="sxs-lookup"><span data-stu-id="9a0ac-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a0ac-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a0ac-125">Requirements</span></span>  
  
|<span data-ttu-id="9a0ac-126">MOF</span><span class="sxs-lookup"><span data-stu-id="9a0ac-126">MOF</span></span>|<span data-ttu-id="9a0ac-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9a0ac-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9a0ac-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="9a0ac-128">Namespace</span></span>|<span data-ttu-id="9a0ac-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9a0ac-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9a0ac-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9a0ac-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

---
title: TextMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f1e026296745f6fc40171866c81f91818789e01
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="51508-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="51508-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="51508-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="51508-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51508-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="51508-104">Syntax</span></span>  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="51508-105">Metody</span><span class="sxs-lookup"><span data-stu-id="51508-105">Methods</span></span>  
 <span data-ttu-id="51508-106">Klasa TextMessageEncodingBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="51508-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="51508-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="51508-107">Properties</span></span>  
 <span data-ttu-id="51508-108">Klasa TextMessageEncodingBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="51508-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="51508-109">Kodowanie</span><span class="sxs-lookup"><span data-stu-id="51508-109">Encoding</span></span>  
 <span data-ttu-id="51508-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="51508-110">Data type: string</span></span>  
  
 <span data-ttu-id="51508-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="51508-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51508-112">Zestaw znaków kodowania używanego w celu emisji komunikatów w powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="51508-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="51508-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="51508-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="51508-114">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="51508-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="51508-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="51508-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51508-116">Liczba całkowita definiująca, ile komunikatów można jednocześnie odczytać bez przydziału nowych czytników.</span><span class="sxs-lookup"><span data-stu-id="51508-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="51508-117">MaxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="51508-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="51508-118">Typ danych: sint32</span><span class="sxs-lookup"><span data-stu-id="51508-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="51508-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="51508-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51508-120">Liczba całkowita definiująca, ile komunikatów można jednocześnie wysłać bez przydziału nowych modułów zapisujących.</span><span class="sxs-lookup"><span data-stu-id="51508-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="51508-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="51508-121">ReaderQuotas</span></span>  
 <span data-ttu-id="51508-122">Typ danych: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="51508-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="51508-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="51508-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51508-124">Przydziały czytników.</span><span class="sxs-lookup"><span data-stu-id="51508-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51508-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="51508-125">Requirements</span></span>  
  
|<span data-ttu-id="51508-126">MOF</span><span class="sxs-lookup"><span data-stu-id="51508-126">MOF</span></span>|<span data-ttu-id="51508-127">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="51508-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="51508-128">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="51508-128">Namespace</span></span>|<span data-ttu-id="51508-129">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="51508-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="51508-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51508-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

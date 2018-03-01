---
title: "ISymUnmanagedDocument — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e176679b4fdb4d0a2c5c4fbcbc09403e45f1ad1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="eb4a7-102">ISymUnmanagedDocument — Interfejs</span><span class="sxs-lookup"><span data-stu-id="eb4a7-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="eb4a7-103">Reprezentuje dokument odwołuje się magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="eb4a7-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="eb4a7-104">Dokument jest zdefiniowany przez adres URL (adres URL) i identyfikator GUID typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="eb4a7-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="eb4a7-105">Można zlokalizować dokument, niezależnie od tego, jak są przechowywane przy użyciu adresu URL i identyfikator GUID typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="eb4a7-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="eb4a7-106">Można przechowywać źródło dokumentu w magazynie symboli i pobrać go za pośrednictwem tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="eb4a7-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb4a7-107">Metody</span><span class="sxs-lookup"><span data-stu-id="eb4a7-107">Methods</span></span>  
  
|<span data-ttu-id="eb4a7-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="eb4a7-108">Method</span></span>|<span data-ttu-id="eb4a7-109">Opis</span><span class="sxs-lookup"><span data-stu-id="eb4a7-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb4a7-110">FindClosestLine, metoda</span><span class="sxs-lookup"><span data-stu-id="eb4a7-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="eb4a7-111">Zwraca najbliższego wiersza, który jest punktem sekwencji danego wiersza w tym dokumencie, który może lub nie może być punktu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="eb4a7-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="eb4a7-112">GetCheckSum, metoda</span><span class="sxs-lookup"><span data-stu-id="eb4a7-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="eb4a7-113">Pobiera sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="eb4a7-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="eb4a7-114">GetCheckSumAlgorithmId, metoda</span><span class="sxs-lookup"><span data-stu-id="eb4a7-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="eb4a7-115">Pobiera identyfikator algorytmu sumy kontrolnej, lub zwraca identyfikator GUID z samych zer, jeśli nie istnieje żadne sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="eb4a7-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="eb4a7-116">GetDocumentType, metoda</span><span class="sxs-lookup"><span data-stu-id="eb4a7-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="eb4a7-117">Pobiera typ dokumentu z tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="eb4a7-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="eb4a7-118">GetLanguage, metoda</span><span class="sxs-lookup"><span data-stu-id="eb4a7-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="eb4a7-119">Pobiera identyfikator języka tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="eb4a7-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="eb4a7-120">GetLanguageVendor, metoda</span><span class="sxs-lookup"><span data-stu-id="eb4a7-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="eb4a7-121">Pobiera dostawcy języka tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="eb4a7-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="eb4a7-122">GetSourceLength, metoda</span><span class="sxs-lookup"><span data-stu-id="eb4a7-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="eb4a7-123">Pobiera długość w bajtach osadzonego źródła.</span><span class="sxs-lookup"><span data-stu-id="eb4a7-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="eb4a7-124">GetSourceRange, metoda</span><span class="sxs-lookup"><span data-stu-id="eb4a7-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="eb4a7-125">Zwraca określony zakres osadzone źródło do danego buforu.</span><span class="sxs-lookup"><span data-stu-id="eb4a7-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="eb4a7-126">GetURL, metoda</span><span class="sxs-lookup"><span data-stu-id="eb4a7-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="eb4a7-127">Zwraca adres URL dla tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="eb4a7-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="eb4a7-128">HasEmbeddedSource, metoda</span><span class="sxs-lookup"><span data-stu-id="eb4a7-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="eb4a7-129">Zwraca `true` Jeśli dokument ma źródła osadzone w symbole debugowania; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="eb4a7-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="eb4a7-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb4a7-130">See Also</span></span>  
 [<span data-ttu-id="eb4a7-131">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="eb4a7-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)

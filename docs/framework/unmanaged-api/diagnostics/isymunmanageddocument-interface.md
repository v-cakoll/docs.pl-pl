---
title: ISymUnmanagedDocument — Interfejs
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33213aced635549dd439cf679d89367a71baa7c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168808"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="9eabe-102">ISymUnmanagedDocument — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9eabe-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="9eabe-103">Reprezentuje dokument odwołuje się w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="9eabe-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="9eabe-104">Dokument jest definiowany przez adres URL (adres URL) i identyfikator GUID typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9eabe-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="9eabe-105">Można zlokalizować dokument, niezależnie od tego, w jaki sposób są przechowywane przy użyciu adresu URL i identyfikator GUID typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9eabe-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="9eabe-106">Można przechowywać źródło dokumentu w magazynie symboli i pobrać go przy użyciu tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9eabe-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9eabe-107">Metody</span><span class="sxs-lookup"><span data-stu-id="9eabe-107">Methods</span></span>  
  
|<span data-ttu-id="9eabe-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="9eabe-108">Method</span></span>|<span data-ttu-id="9eabe-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9eabe-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9eabe-110">FindClosestLine, metoda</span><span class="sxs-lookup"><span data-stu-id="9eabe-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="9eabe-111">Zwraca najbliższego wiersz, który jest punktem sekwencji, rozpoczynając od podanej linię w tym dokumencie, który może być lub może nie być punktu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="9eabe-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="9eabe-112">GetCheckSum, metoda</span><span class="sxs-lookup"><span data-stu-id="9eabe-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="9eabe-113">Pobiera sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="9eabe-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="9eabe-114">GetCheckSumAlgorithmId, metoda</span><span class="sxs-lookup"><span data-stu-id="9eabe-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="9eabe-115">Pobiera identyfikator algorytmu sumy kontrolnej lub zwraca identyfikator GUID same zera, jeśli nie określono żadnych sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="9eabe-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="9eabe-116">GetDocumentType, metoda</span><span class="sxs-lookup"><span data-stu-id="9eabe-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="9eabe-117">Pobiera typ dokumentu w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="9eabe-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="9eabe-118">GetLanguage, metoda</span><span class="sxs-lookup"><span data-stu-id="9eabe-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="9eabe-119">Pobiera identyfikator języka w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="9eabe-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="9eabe-120">GetLanguageVendor, metoda</span><span class="sxs-lookup"><span data-stu-id="9eabe-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="9eabe-121">Pobiera dostawcę język tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9eabe-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="9eabe-122">GetSourceLength, metoda</span><span class="sxs-lookup"><span data-stu-id="9eabe-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="9eabe-123">Pobiera długość w bajtach osadzonego źródła.</span><span class="sxs-lookup"><span data-stu-id="9eabe-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="9eabe-124">GetSourceRange, metoda</span><span class="sxs-lookup"><span data-stu-id="9eabe-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="9eabe-125">Zwraca określony zakres osadzonego źródła do podanego buforu.</span><span class="sxs-lookup"><span data-stu-id="9eabe-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="9eabe-126">GetURL, metoda</span><span class="sxs-lookup"><span data-stu-id="9eabe-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="9eabe-127">Zwraca adres URL dla tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="9eabe-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="9eabe-128">HasEmbeddedSource, metoda</span><span class="sxs-lookup"><span data-stu-id="9eabe-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="9eabe-129">Zwraca `true` Jeśli dokument ma źródło osadzone w symbole debugowania; w przeciwnym razie zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="9eabe-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9eabe-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9eabe-130">See also</span></span>

- [<span data-ttu-id="9eabe-131">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="9eabe-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)

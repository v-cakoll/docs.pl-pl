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
ms.openlocfilehash: a8ff6d3a925773e58e0713a87b167420c246f85b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615569"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="19c45-102">ISymUnmanagedDocument — Interfejs</span><span class="sxs-lookup"><span data-stu-id="19c45-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="19c45-103">Reprezentuje dokument, do którego odwołuje się magazyn symboli.</span><span class="sxs-lookup"><span data-stu-id="19c45-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="19c45-104">Dokument jest zdefiniowany przez adres URL (Uniform Resource Locator) i identyfikator GUID typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="19c45-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="19c45-105">Możesz zlokalizować dokument niezależnie od tego, w jaki sposób jest przechowywany przy użyciu adresu URL i identyfikatora GUID typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="19c45-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="19c45-106">Źródło dokumentu można zapisać w magazynie symboli i pobrać je za pomocą tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="19c45-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19c45-107">Metody</span><span class="sxs-lookup"><span data-stu-id="19c45-107">Methods</span></span>  
  
|<span data-ttu-id="19c45-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="19c45-108">Method</span></span>|<span data-ttu-id="19c45-109">Opis</span><span class="sxs-lookup"><span data-stu-id="19c45-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19c45-110">FindClosestLine, metoda</span><span class="sxs-lookup"><span data-stu-id="19c45-110">FindClosestLine Method</span></span>](isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="19c45-111">Zwraca najbliższy wiersz będący punktem sekwencji, uwzględniając wiersz w tym dokumencie, który może lub nie jest punktem sekwencji.</span><span class="sxs-lookup"><span data-stu-id="19c45-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="19c45-112">GetCheckSum, metoda</span><span class="sxs-lookup"><span data-stu-id="19c45-112">GetCheckSum Method</span></span>](isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="19c45-113">Pobiera sumę kontrolną.</span><span class="sxs-lookup"><span data-stu-id="19c45-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="19c45-114">GetCheckSumAlgorithmId, metoda</span><span class="sxs-lookup"><span data-stu-id="19c45-114">GetCheckSumAlgorithmId Method</span></span>](isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="19c45-115">Pobiera identyfikator algorytmu sum kontrolnych lub zwraca identyfikator GUID wszystkich zer, jeśli nie ma sumy kontrolnej.</span><span class="sxs-lookup"><span data-stu-id="19c45-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="19c45-116">GetDocumentType, metoda</span><span class="sxs-lookup"><span data-stu-id="19c45-116">GetDocumentType Method</span></span>](isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="19c45-117">Pobiera typ dokumentu tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="19c45-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="19c45-118">GetLanguage, metoda</span><span class="sxs-lookup"><span data-stu-id="19c45-118">GetLanguage Method</span></span>](isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="19c45-119">Pobiera identyfikator języka tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="19c45-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="19c45-120">GetLanguageVendor, metoda</span><span class="sxs-lookup"><span data-stu-id="19c45-120">GetLanguageVendor Method</span></span>](isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="19c45-121">Pobiera dostawcę języka tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="19c45-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="19c45-122">GetSourceLength, metoda</span><span class="sxs-lookup"><span data-stu-id="19c45-122">GetSourceLength Method</span></span>](isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="19c45-123">Pobiera długość (w bajtach) osadzonego źródła.</span><span class="sxs-lookup"><span data-stu-id="19c45-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="19c45-124">GetSourceRange, metoda</span><span class="sxs-lookup"><span data-stu-id="19c45-124">GetSourceRange Method</span></span>](isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="19c45-125">Zwraca określony zakres osadzonego źródła do podanego buforu.</span><span class="sxs-lookup"><span data-stu-id="19c45-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="19c45-126">GetURL, metoda</span><span class="sxs-lookup"><span data-stu-id="19c45-126">GetURL Method</span></span>](isymunmanageddocument-geturl-method.md)|<span data-ttu-id="19c45-127">Zwraca adres URL tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="19c45-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="19c45-128">HasEmbeddedSource, metoda</span><span class="sxs-lookup"><span data-stu-id="19c45-128">HasEmbeddedSource Method</span></span>](isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="19c45-129">Zwraca `true` czy dokument ma osadzone źródło w symbolach debugowania; w przeciwnym razie zwraca `false` .</span><span class="sxs-lookup"><span data-stu-id="19c45-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="19c45-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="19c45-130">See also</span></span>

- [<span data-ttu-id="19c45-131">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="19c45-131">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)

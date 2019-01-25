---
title: ISymUnmanagedReader — Interfejs
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d3c05715ffb4f7a366e3b3c9951ab68477c5c32
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561494"
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="28c6b-102">ISymUnmanagedReader — Interfejs</span><span class="sxs-lookup"><span data-stu-id="28c6b-102">ISymUnmanagedReader Interface</span></span>
<span data-ttu-id="28c6b-103">Reprezentuje czytnik symbolu, który zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="28c6b-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="28c6b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="28c6b-104">Methods</span></span>  
  
|<span data-ttu-id="28c6b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-105">Method</span></span>|<span data-ttu-id="28c6b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="28c6b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="28c6b-107">GetDocument, metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-107">GetDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="28c6b-108">Umożliwia znalezienie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="28c6b-108">Finds a document.</span></span>|  
|[<span data-ttu-id="28c6b-109">GetDocuments, metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-109">GetDocuments Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="28c6b-110">Zwraca tablicę wszystkich dokumentów, które są zdefiniowane w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="28c6b-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="28c6b-111">GetDocumentVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-111">GetDocumentVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="28c6b-112">Pobiera określoną wersję określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="28c6b-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="28c6b-113">GetGlobalVariables, metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-113">GetGlobalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="28c6b-114">Zwraca wszystkie zmienne globalne.</span><span class="sxs-lookup"><span data-stu-id="28c6b-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="28c6b-115">GetMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="28c6b-116">Pobiera metodę czytnika symboli podany token metody.</span><span class="sxs-lookup"><span data-stu-id="28c6b-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="28c6b-117">GetMethodByVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-117">GetMethodByVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="28c6b-118">Pobiera metodę czytnika symboli podany token metody i numeru wersji edycji i kopiowania.</span><span class="sxs-lookup"><span data-stu-id="28c6b-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="28c6b-119">GetMethodFromDocumentPosition, metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-119">GetMethodFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="28c6b-120">Zwraca metodę, która zawiera punkt przerwania na pozycji w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="28c6b-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="28c6b-121">GetMethodsFromDocumentPosition, metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-121">GetMethodsFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="28c6b-122">Zwraca tablicę z metod, z których każdy zawiera punkt przerwania na pozycji w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="28c6b-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="28c6b-123">GetMethodVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-123">GetMethodVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="28c6b-124">Pobiera wersję metody.</span><span class="sxs-lookup"><span data-stu-id="28c6b-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="28c6b-125">GetNamespaces, metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-125">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="28c6b-126">Pobiera przestrzenie nazw zdefiniowane w zakresie globalnym, w tym magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="28c6b-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="28c6b-127">GetSymAttribute, metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-127">GetSymAttribute Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="28c6b-128">Pobiera atrybut niestandardowy na podstawie jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="28c6b-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="28c6b-129">GetSymbolStoreFileName, metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-129">GetSymbolStoreFileName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="28c6b-130">Zawiera nazwę pliku na dysku w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="28c6b-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="28c6b-131">GetUserEntryPoint, metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-131">GetUserEntryPoint Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="28c6b-132">Zwraca metodę, która została określona jako punkt wejścia użytkownika dla modułu, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="28c6b-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="28c6b-133">GetVariables, metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-133">GetVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="28c6b-134">Zwracają zmienną inną niż lokalna, biorąc pod uwagę jej nadrzędnej i nazwę.</span><span class="sxs-lookup"><span data-stu-id="28c6b-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="28c6b-135">Initialize, metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-135">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|<span data-ttu-id="28c6b-136">Inicjuje czytnika symboli z interfejsem importera metadanych, które ten czytnik będzie skojarzona, wraz z nazwą pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="28c6b-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="28c6b-137">ReplaceSymbolStore, metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-137">ReplaceSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="28c6b-138">Zamienia istniejący magazyn symboli w magazynie symboli delta.</span><span class="sxs-lookup"><span data-stu-id="28c6b-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="28c6b-139">UpdateSymbolStore, metoda</span><span class="sxs-lookup"><span data-stu-id="28c6b-139">UpdateSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="28c6b-140">Aktualizuje istniejący magazyn symboli w magazynie symboli delta.</span><span class="sxs-lookup"><span data-stu-id="28c6b-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="28c6b-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28c6b-141">Requirements</span></span>  
 <span data-ttu-id="28c6b-142">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="28c6b-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28c6b-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28c6b-143">See also</span></span>
- [<span data-ttu-id="28c6b-144">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="28c6b-144">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="28c6b-145">ISymUnmanagedReader2, interfejs</span><span class="sxs-lookup"><span data-stu-id="28c6b-145">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)

---
title: "ISymUnmanagedReader — Interfejs"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9e8daea11292cb37deb8e956e6a666c14579fbfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="2108f-102">ISymUnmanagedReader — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2108f-102">ISymUnmanagedReader Interface</span></span>
<span data-ttu-id="2108f-103">Reprezentuje czytnika symboli, która zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="2108f-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2108f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2108f-104">Methods</span></span>  
  
|<span data-ttu-id="2108f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-105">Method</span></span>|<span data-ttu-id="2108f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2108f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2108f-107">GetDocument, metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-107">GetDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="2108f-108">Umożliwia znalezienie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2108f-108">Finds a document.</span></span>|  
|[<span data-ttu-id="2108f-109">GetDocuments, metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-109">GetDocuments Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="2108f-110">Zwraca tablicę wszystkich dokumentów, które są zdefiniowane w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="2108f-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="2108f-111">GetDocumentVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-111">GetDocumentVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="2108f-112">Pobiera określoną wersję określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="2108f-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="2108f-113">GetGlobalVariables, metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-113">GetGlobalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="2108f-114">Zwraca wszystkie zmienne globalne.</span><span class="sxs-lookup"><span data-stu-id="2108f-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="2108f-115">GetMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="2108f-116">Pobiera metodę czytnika symboli podany token metody.</span><span class="sxs-lookup"><span data-stu-id="2108f-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="2108f-117">GetMethodByVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-117">GetMethodByVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="2108f-118">Pobiera metodę czytnika symboli podany token metody i numer wersji edycji i kopii.</span><span class="sxs-lookup"><span data-stu-id="2108f-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="2108f-119">GetMethodFromDocumentPosition, metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-119">GetMethodFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="2108f-120">Zwraca metodę, która zawiera punkt przerwania w danej pozycji w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="2108f-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="2108f-121">GetMethodsFromDocumentPosition, metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-121">GetMethodsFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="2108f-122">Zwraca tablicę z metod, z których każdy zawiera punkt przerwania w danej pozycji w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="2108f-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="2108f-123">GetMethodVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-123">GetMethodVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="2108f-124">Pobiera wersję metody.</span><span class="sxs-lookup"><span data-stu-id="2108f-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="2108f-125">GetNamespaces, metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-125">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="2108f-126">Pobiera przestrzenie nazw zdefiniowane w zakresie globalnym, w tym magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="2108f-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="2108f-127">GetSymAttribute, metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-127">GetSymAttribute Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="2108f-128">Pobiera atrybut niestandardowy ustalane na podstawie jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="2108f-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="2108f-129">GetSymbolStoreFileName, metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-129">GetSymbolStoreFileName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="2108f-130">Zawiera nazwę pliku na dysku magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="2108f-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="2108f-131">GetUserEntryPoint, metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-131">GetUserEntryPoint Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="2108f-132">Zwraca metodę, która została określona jako punktu wejścia użytkownika dla modułu, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="2108f-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="2108f-133">GetVariables, metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-133">GetVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="2108f-134">Zwracają zmienną innego niż lokalne jego nadrzędny i nazwę.</span><span class="sxs-lookup"><span data-stu-id="2108f-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="2108f-135">Initialize, metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-135">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|<span data-ttu-id="2108f-136">Inicjuje czytnika symboli z interfejsem importer metadanych, który tego czytnika zostanie skojarzona z, wraz z nazwą modułu.</span><span class="sxs-lookup"><span data-stu-id="2108f-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="2108f-137">ReplaceSymbolStore, metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-137">ReplaceSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="2108f-138">Zamienia istniejący magazyn symbol magazynu symboli delta.</span><span class="sxs-lookup"><span data-stu-id="2108f-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="2108f-139">UpdateSymbolStore, metoda</span><span class="sxs-lookup"><span data-stu-id="2108f-139">UpdateSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="2108f-140">Aktualizuje istniejący magazyn symbol magazynu symboli delta.</span><span class="sxs-lookup"><span data-stu-id="2108f-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2108f-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2108f-141">Requirements</span></span>  
 <span data-ttu-id="2108f-142">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2108f-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2108f-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2108f-143">See Also</span></span>  
 [<span data-ttu-id="2108f-144">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="2108f-144">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="2108f-145">ISymUnmanagedReader2, interfejs</span><span class="sxs-lookup"><span data-stu-id="2108f-145">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)

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
ms.openlocfilehash: b372021fcda39d9973d96a9c39e93e38617887a6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615465"
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="34837-102">ISymUnmanagedReader — Interfejs</span><span class="sxs-lookup"><span data-stu-id="34837-102">ISymUnmanagedReader Interface</span></span>
<span data-ttu-id="34837-103">Reprezentuje czytnik symboli, który zapewnia dostęp do dokumentów, metod i zmiennych w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="34837-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="34837-104">Metody</span><span class="sxs-lookup"><span data-stu-id="34837-104">Methods</span></span>  
  
|<span data-ttu-id="34837-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="34837-105">Method</span></span>|<span data-ttu-id="34837-106">Opis</span><span class="sxs-lookup"><span data-stu-id="34837-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="34837-107">GetDocument, metoda</span><span class="sxs-lookup"><span data-stu-id="34837-107">GetDocument Method</span></span>](isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="34837-108">Znajduje dokument.</span><span class="sxs-lookup"><span data-stu-id="34837-108">Finds a document.</span></span>|  
|[<span data-ttu-id="34837-109">GetDocuments, metoda</span><span class="sxs-lookup"><span data-stu-id="34837-109">GetDocuments Method</span></span>](isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="34837-110">Zwraca tablicę wszystkich dokumentów zdefiniowanych w magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="34837-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="34837-111">GetDocumentVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="34837-111">GetDocumentVersion Method</span></span>](isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="34837-112">Pobiera określoną wersję określonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="34837-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="34837-113">GetGlobalVariables, metoda</span><span class="sxs-lookup"><span data-stu-id="34837-113">GetGlobalVariables Method</span></span>](isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="34837-114">Zwraca wszystkie zmienne globalne.</span><span class="sxs-lookup"><span data-stu-id="34837-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="34837-115">GetMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="34837-115">GetMethod Method</span></span>](isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="34837-116">Pobiera metodę czytnika symboli, używając tokenu metody.</span><span class="sxs-lookup"><span data-stu-id="34837-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="34837-117">GetMethodByVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="34837-117">GetMethodByVersion Method</span></span>](isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="34837-118">Pobiera metodę czytnika symboli, uwzględniając token metody i numer wersji do edycji i kopiowania.</span><span class="sxs-lookup"><span data-stu-id="34837-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="34837-119">GetMethodFromDocumentPosition, metoda</span><span class="sxs-lookup"><span data-stu-id="34837-119">GetMethodFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="34837-120">Zwraca metodę, która zawiera punkt przerwania w podanym miejscu w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="34837-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="34837-121">GetMethodsFromDocumentPosition, metoda</span><span class="sxs-lookup"><span data-stu-id="34837-121">GetMethodsFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="34837-122">Zwraca tablicę metod, z których każdy zawiera punkt przerwania w podanym miejscu w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="34837-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="34837-123">GetMethodVersion, metoda</span><span class="sxs-lookup"><span data-stu-id="34837-123">GetMethodVersion Method</span></span>](isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="34837-124">Pobiera wersję metody.</span><span class="sxs-lookup"><span data-stu-id="34837-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="34837-125">GetNamespaces, metoda</span><span class="sxs-lookup"><span data-stu-id="34837-125">GetNamespaces Method</span></span>](isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="34837-126">Pobiera przestrzenie nazw zdefiniowane w globalnym zakresie w ramach tego magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="34837-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="34837-127">GetSymAttribute, metoda</span><span class="sxs-lookup"><span data-stu-id="34837-127">GetSymAttribute Method</span></span>](isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="34837-128">Pobiera atrybut niestandardowy na podstawie jego nazwy.</span><span class="sxs-lookup"><span data-stu-id="34837-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="34837-129">GetSymbolStoreFileName, metoda</span><span class="sxs-lookup"><span data-stu-id="34837-129">GetSymbolStoreFileName Method</span></span>](isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="34837-130">Udostępnia nazwę pliku na dysku magazynu symboli.</span><span class="sxs-lookup"><span data-stu-id="34837-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="34837-131">GetUserEntryPoint, metoda</span><span class="sxs-lookup"><span data-stu-id="34837-131">GetUserEntryPoint Method</span></span>](isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="34837-132">Zwraca metodę, która została określona jako punkt wejścia użytkownika dla modułu, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="34837-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="34837-133">GetVariables, metoda</span><span class="sxs-lookup"><span data-stu-id="34837-133">GetVariables Method</span></span>](isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="34837-134">Zwróć zmienną nielokalną, używając jej elementu nadrzędnego i nazwy.</span><span class="sxs-lookup"><span data-stu-id="34837-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="34837-135">Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="34837-135">Initialize Method</span></span>](isymunmanagedreader-initialize-method.md)|<span data-ttu-id="34837-136">Inicjuje czytnik symboli z interfejsem importera metadanych, z którym zostanie skojarzony ten czytnik, wraz z nazwą pliku modułu.</span><span class="sxs-lookup"><span data-stu-id="34837-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="34837-137">ReplaceSymbolStore, metoda</span><span class="sxs-lookup"><span data-stu-id="34837-137">ReplaceSymbolStore Method</span></span>](isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="34837-138">Zamienia istniejący magazyn symboli na magazyn symboli różnicowych.</span><span class="sxs-lookup"><span data-stu-id="34837-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="34837-139">UpdateSymbolStore, metoda</span><span class="sxs-lookup"><span data-stu-id="34837-139">UpdateSymbolStore Method</span></span>](isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="34837-140">Aktualizuje istniejący magazyn symboli przy użyciu magazynu symboli różnicowych.</span><span class="sxs-lookup"><span data-stu-id="34837-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="34837-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="34837-141">Requirements</span></span>  
 <span data-ttu-id="34837-142">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="34837-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34837-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34837-143">See also</span></span>

- [<span data-ttu-id="34837-144">Interfejsy magazynu symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="34837-144">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="34837-145">ISymUnmanagedReader2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="34837-145">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)

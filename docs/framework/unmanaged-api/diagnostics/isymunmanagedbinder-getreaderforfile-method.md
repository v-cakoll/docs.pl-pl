---
title: "ISymUnmanagedBinder::GetReaderForFile — Metoda"
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
- ISymUnmanagedBinder.GetReaderForFile
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c50bb4ca36043fc2491c9a0615b682c94c422e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="f2789-102">ISymUnmanagedBinder::GetReaderForFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="f2789-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="f2789-103">Podany interfejs metadanych i nazwę pliku, zwraca poprawny <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> Struktura, która będzie odczytywać symbole debugowania skojarzone z modułu.</span><span class="sxs-lookup"><span data-stu-id="f2789-103">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="f2789-104">Ta metoda zostanie otwarty plik programu (PDB) bazy danych tylko wtedy, gdy jest obok pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="f2789-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="f2789-105">Ta zmiana została wprowadzona ze względów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="f2789-105">This change has been made for security purposes.</span></span> <span data-ttu-id="f2789-106">Jeśli potrzebujesz bardziej zaawansowane wyszukiwanie dla pliku PDB, użyj [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="f2789-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2789-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2789-107">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2789-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2789-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="f2789-109">[in] Wskaźnik do interfejsu importu metadanych.</span><span class="sxs-lookup"><span data-stu-id="f2789-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="f2789-110">[in] Wskaźnik do nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="f2789-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="f2789-111">[in] Wskaźnik do ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="f2789-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="f2789-112">[out] Wskaźnik, który jest ustawiony na zwracana <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f2789-112">[out] A pointer that is set to the returned <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2789-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f2789-113">Return Value</span></span>  
 <span data-ttu-id="f2789-114">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="f2789-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2789-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f2789-115">Requirements</span></span>  
 <span data-ttu-id="f2789-116">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f2789-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2789-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2789-117">See Also</span></span>  
 [<span data-ttu-id="f2789-118">ISymUnmanagedBinder, interfejs</span><span class="sxs-lookup"><span data-stu-id="f2789-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="f2789-119">GetReaderForFile2, metoda</span><span class="sxs-lookup"><span data-stu-id="f2789-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)

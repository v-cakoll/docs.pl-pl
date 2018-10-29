---
title: ISymUnmanagedBinder::GetReaderForFile — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: df6a35dcaebc681aa5463a014d3283c81efea617
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199867"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="12a5a-102">ISymUnmanagedBinder::GetReaderForFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="12a5a-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="12a5a-103">Podany interfejs metadanych i nazwę pliku, zwraca poprawny [isymunmanagedreader —](isymunmanagedreader-interface.md) interfejs, który zostanie odczytany symbole debugowania, skojarzone z modułem.</span><span class="sxs-lookup"><span data-stu-id="12a5a-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="12a5a-104">Ta metoda zostanie otwarty plik bazy danych (PDB) programu, tylko wtedy, gdy znajduje się obok pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="12a5a-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="12a5a-105">Ta zmiana została wprowadzona ze względów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="12a5a-105">This change has been made for security purposes.</span></span> <span data-ttu-id="12a5a-106">Jeśli potrzebujesz bardziej rozbudowane wyszukiwanie pliku PDB, użyj [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="12a5a-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12a5a-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="12a5a-107">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12a5a-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="12a5a-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="12a5a-109">[in] Wskaźnik do interfejsu Importowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="12a5a-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="12a5a-110">[in] Wskaźnik na nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="12a5a-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="12a5a-111">[in] Wskaźnik do ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="12a5a-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="12a5a-112">[out] Wskaźnik, który jest ustawiony do zwracanego [isymunmanagedreader —](isymunmanagedreader-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="12a5a-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12a5a-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="12a5a-113">Return Value</span></span>  
 <span data-ttu-id="12a5a-114">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="12a5a-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12a5a-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="12a5a-115">Requirements</span></span>  
 <span data-ttu-id="12a5a-116">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="12a5a-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12a5a-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12a5a-117">See Also</span></span>  
 [<span data-ttu-id="12a5a-118">ISymUnmanagedBinder, interfejs</span><span class="sxs-lookup"><span data-stu-id="12a5a-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="12a5a-119">GetReaderForFile2, metoda</span><span class="sxs-lookup"><span data-stu-id="12a5a-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)

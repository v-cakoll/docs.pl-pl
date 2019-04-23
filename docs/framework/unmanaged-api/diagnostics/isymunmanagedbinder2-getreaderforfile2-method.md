---
title: ISymUnmanagedBinder2::GetReaderForFile2 — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fed289b2776e8ac4a12969060cd16c6163ebed2f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091970"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="bac14-102">ISymUnmanagedBinder2::GetReaderForFile2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="bac14-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>
<span data-ttu-id="bac14-103">Podany interfejs metadanych i nazwę pliku, zwraca poprawny [isymunmanagedreader —](isymunmanagedreader-interface.md) interfejs, który zostanie odczytany symbole debugowania, skojarzone z modułem.</span><span class="sxs-lookup"><span data-stu-id="bac14-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="bac14-104">Ta metoda zapewnia bardziej rozbudowane wyszukiwanie pliku bazy danych (PDB) programu niż [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="bac14-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bac14-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bac14-105">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bac14-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bac14-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="bac14-107">[in] Wskaźnik do interfejsu Importowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="bac14-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="bac14-108">[in] Wskaźnik na nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="bac14-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="bac14-109">[in] Wskaźnik do ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="bac14-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="bac14-110">[in] Wartość [corsymsearchpolicyattributes —](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) wyliczenie, które określa zasady, które ma być używany podczas wyszukiwania dla czytnika symboli.</span><span class="sxs-lookup"><span data-stu-id="bac14-110">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="bac14-111">[out] Wskaźnik, który jest ustawiony do zwracanego [isymunmanagedreader —](isymunmanagedreader-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="bac14-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bac14-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bac14-112">Return Value</span></span>  
 <span data-ttu-id="bac14-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="bac14-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bac14-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bac14-114">Requirements</span></span>  
 <span data-ttu-id="bac14-115">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bac14-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bac14-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bac14-116">Remarks</span></span>  
 <span data-ttu-id="bac14-117">Ta wersja metody wyszukać plik PDB w obszarach innych niż obok modułu.</span><span class="sxs-lookup"><span data-stu-id="bac14-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="bac14-118">Zasady wyszukiwania mogą być kontrolowane przez łączenie [corsymsearchpolicyattributes —](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="bac14-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="bac14-119">Na przykład `AllowReferencePathAccess | AllowSymbolServerAccess` szuka pliku PDB, obok pliku wykonywalnego i na serwerze symboli, nie wykonaj zapytanie dotyczące rejestru lub użyj ścieżki w pliku wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="bac14-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="bac14-120">Jeśli `searchPath` parametr zostanie podany, zawsze będą przeszukiwane te katalogi.</span><span class="sxs-lookup"><span data-stu-id="bac14-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bac14-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bac14-121">See also</span></span>

- [<span data-ttu-id="bac14-122">ISymUnmanagedBinder2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bac14-122">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="bac14-123">GetReaderForFile, metoda</span><span class="sxs-lookup"><span data-stu-id="bac14-123">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)

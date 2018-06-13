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
ms.openlocfilehash: cea8a322fab6ef76873e668c622ac63e3a3f2862
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428228"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="a1fe7-102">ISymUnmanagedBinder2::GetReaderForFile2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="a1fe7-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>
<span data-ttu-id="a1fe7-103">Podany interfejs metadanych i nazwę pliku, zwraca poprawny <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interfejs, który będzie odczytywać symbole debugowania skojarzone z modułu.</span><span class="sxs-lookup"><span data-stu-id="a1fe7-103">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="a1fe7-104">Ta metoda zapewnia bardziej rozległych Wyszukaj plik programu (PDB) bazy danych niż [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a1fe7-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1fe7-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1fe7-105">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1fe7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1fe7-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="a1fe7-107">[in] Wskaźnik do interfejsu importu metadanych.</span><span class="sxs-lookup"><span data-stu-id="a1fe7-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="a1fe7-108">[in] Wskaźnik do nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="a1fe7-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="a1fe7-109">[in] Wskaźnik do ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="a1fe7-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="a1fe7-110">[in] Wartość [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) wyliczenia, która określa zasady, która ma być używane podczas wyszukiwania dla czytnika symboli.</span><span class="sxs-lookup"><span data-stu-id="a1fe7-110">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="a1fe7-111">[out] Wskaźnik, który jest ustawiony na zwracana <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a1fe7-111">[out] A pointer that is set to the returned <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1fe7-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a1fe7-112">Return Value</span></span>  
 <span data-ttu-id="a1fe7-113">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="a1fe7-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1fe7-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1fe7-114">Requirements</span></span>  
 <span data-ttu-id="a1fe7-115">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a1fe7-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1fe7-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1fe7-116">Remarks</span></span>  
 <span data-ttu-id="a1fe7-117">Ta wersja metody można wyszukiwać pliku PDB w obszarach innych niż prawo obok modułu.</span><span class="sxs-lookup"><span data-stu-id="a1fe7-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="a1fe7-118">Wyszukiwanie zasad mogą być kontrolowane przez połączenie [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="a1fe7-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="a1fe7-119">Na przykład `AllowReferencePathAccess | AllowSymbolServerAccess` szuka pliku PDB obok pliku wykonywalnego i na serwerze symboli nie zapytanie dotyczące rejestru lub użyj ścieżki pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="a1fe7-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="a1fe7-120">Jeśli `searchPath` podano parametru, te katalogi zawsze będą wyszukiwane.</span><span class="sxs-lookup"><span data-stu-id="a1fe7-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1fe7-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1fe7-121">See Also</span></span>  
 [<span data-ttu-id="a1fe7-122">ISymUnmanagedBinder2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1fe7-122">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="a1fe7-123">GetReaderForFile, metoda</span><span class="sxs-lookup"><span data-stu-id="a1fe7-123">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)

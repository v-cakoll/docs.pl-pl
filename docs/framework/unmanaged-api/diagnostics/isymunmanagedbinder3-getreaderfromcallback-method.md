---
title: "ISymUnmanagedBinder3::GetReaderFromCallback — Metoda"
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
- ISymUnmanagedBinder3.GetReaderFromCallback
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 648559936259e7412011f9fb7613bd0e938e4ecb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="1d38d-102">ISymUnmanagedBinder3::GetReaderFromCallback — Metoda</span><span class="sxs-lookup"><span data-stu-id="1d38d-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="1d38d-103">Zezwala użytkownikowi na wdrożenie lub podać za pośrednictwem wywołania zwrotnego albo `IID_IDiaReadExeAtRVACallback` lub `IID_IDiaReadExeAtOffsetCallback` Aby uzyskać informacje o debugowaniu katalogu z pamięci.</span><span class="sxs-lookup"><span data-stu-id="1d38d-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d38d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d38d-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d38d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d38d-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="1d38d-106">[in] Wskaźnik do interfejsu importu metadanych.</span><span class="sxs-lookup"><span data-stu-id="1d38d-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="1d38d-107">[in] Wskaźnik do nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="1d38d-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="1d38d-108">[in] Wskaźnik do ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="1d38d-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="1d38d-109">[in] Wartość [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) wyliczenia, która określa zasady, która ma być używane podczas wyszukiwania dla czytnika symboli.</span><span class="sxs-lookup"><span data-stu-id="1d38d-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="1d38d-110">[in] Wskaźnik do funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="1d38d-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1d38d-111">[out] Wskaźnik, który jest ustawiony na zwróconego [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1d38d-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d38d-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1d38d-112">Return Value</span></span>  
 <span data-ttu-id="1d38d-113">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="1d38d-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d38d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1d38d-114">Requirements</span></span>  
 <span data-ttu-id="1d38d-115">**Nagłówek:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="1d38d-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d38d-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d38d-116">See Also</span></span>  
 [<span data-ttu-id="1d38d-117">ISymUnmanagedBinder3, interfejs</span><span class="sxs-lookup"><span data-stu-id="1d38d-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)

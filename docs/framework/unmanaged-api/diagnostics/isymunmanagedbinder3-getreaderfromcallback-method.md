---
title: ISymUnmanagedBinder3::GetReaderFromCallback — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9487cf89d87b5f373302dc49a08c4fabb719e746
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160774"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="d7bef-102">ISymUnmanagedBinder3::GetReaderFromCallback — Metoda</span><span class="sxs-lookup"><span data-stu-id="d7bef-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="d7bef-103">Zezwala użytkownikowi na implementowanie lub podać za pośrednictwem wywołania zwrotnego albo `IID_IDiaReadExeAtRVACallback` lub `IID_IDiaReadExeAtOffsetCallback` Aby uzyskać informacje o debugowaniu katalogu z pamięci.</span><span class="sxs-lookup"><span data-stu-id="d7bef-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7bef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7bef-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7bef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d7bef-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="d7bef-106">[in] Wskaźnik do interfejsu Importowanie metadanych.</span><span class="sxs-lookup"><span data-stu-id="d7bef-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="d7bef-107">[in] Wskaźnik na nazwę pliku.</span><span class="sxs-lookup"><span data-stu-id="d7bef-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="d7bef-108">[in] Wskaźnik do ścieżki wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="d7bef-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="d7bef-109">[in] Wartość [corsymsearchpolicyattributes —](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) wyliczenie, które określa zasady, które ma być używany podczas wyszukiwania dla czytnika symboli.</span><span class="sxs-lookup"><span data-stu-id="d7bef-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="d7bef-110">[in] Wskaźnik do funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="d7bef-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="d7bef-111">[out] Wskaźnik, który jest ustawiony do zwracanego [isymunmanagedreader —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d7bef-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7bef-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d7bef-112">Return Value</span></span>  
 <span data-ttu-id="d7bef-113">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="d7bef-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7bef-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d7bef-114">Requirements</span></span>  
 <span data-ttu-id="d7bef-115">**Nagłówek:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="d7bef-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7bef-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d7bef-116">See also</span></span>

- [<span data-ttu-id="d7bef-117">ISymUnmanagedBinder3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d7bef-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)

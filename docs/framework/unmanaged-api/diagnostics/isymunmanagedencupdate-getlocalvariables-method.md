---
title: ISymUnmanagedENCUpdate::GetLocalVariables — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82e657e91e586d7fe409646ea4fb8946c026e84c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="6922e-102">ISymUnmanagedENCUpdate::GetLocalVariables — Metoda</span><span class="sxs-lookup"><span data-stu-id="6922e-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>
<span data-ttu-id="6922e-103">Pobiera zmienne lokalne.</span><span class="sxs-lookup"><span data-stu-id="6922e-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6922e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6922e-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6922e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6922e-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="6922e-106">[in] Token metadanych metody.</span><span class="sxs-lookup"><span data-stu-id="6922e-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="6922e-107">[in] A `ULONG` wskazuje, że rozmiar `rgLocals` parametru.</span><span class="sxs-lookup"><span data-stu-id="6922e-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="6922e-108">[out] Tablica zwrócona <!--zz<xref:ISymUnmanagedVariable>--> `ISymUnmanagedVariable` wystąpień.</span><span class="sxs-lookup"><span data-stu-id="6922e-108">[out] The returned array of <!--zz<xref:ISymUnmanagedVariable>--> `ISymUnmanagedVariable`  instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6922e-109">[out] Wskaźnik do `ULONG` odbierająca rozmiar `rgLocals` buforu, muszą zawierać zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="6922e-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6922e-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6922e-110">Return Value</span></span>  
 <span data-ttu-id="6922e-111">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="6922e-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6922e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6922e-112">Requirements</span></span>  
 <span data-ttu-id="6922e-113">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6922e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6922e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6922e-114">See Also</span></span>  
 [<span data-ttu-id="6922e-115">ISymUnmanagedENCUpdate, interfejs</span><span class="sxs-lookup"><span data-stu-id="6922e-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

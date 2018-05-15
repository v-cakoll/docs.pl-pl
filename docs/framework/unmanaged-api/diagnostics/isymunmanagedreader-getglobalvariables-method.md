---
title: ISymUnmanagedReader::GetGlobalVariables — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetGlobalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetGlobalVariables
helpviewer_keywords:
- GetGlobalVariables method [.NET Framework debugging]
- ISymUnmanagedReader::GetGlobalVariables method [.NET Framework debugging]
ms.assetid: a2dd5098-3e58-4be5-b7a2-e4160b3b505a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6574c4d30b963ce571343d1a584bfccb48ffd195
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="7bca1-102">ISymUnmanagedReader::GetGlobalVariables — Metoda</span><span class="sxs-lookup"><span data-stu-id="7bca1-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="7bca1-103">Zwraca wszystkie zmienne globalne.</span><span class="sxs-lookup"><span data-stu-id="7bca1-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bca1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7bca1-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7bca1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7bca1-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="7bca1-106">[in] Długość buforu wskazywana przez `pcVars`.</span><span class="sxs-lookup"><span data-stu-id="7bca1-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="7bca1-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać zmiennych.</span><span class="sxs-lookup"><span data-stu-id="7bca1-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="7bca1-108">[out] Bufor, który zawiera zmienne.</span><span class="sxs-lookup"><span data-stu-id="7bca1-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bca1-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7bca1-109">Return Value</span></span>  
 <span data-ttu-id="7bca1-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="7bca1-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bca1-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7bca1-111">Requirements</span></span>  
 <span data-ttu-id="7bca1-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7bca1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bca1-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7bca1-113">See Also</span></span>  
 [<span data-ttu-id="7bca1-114">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="7bca1-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

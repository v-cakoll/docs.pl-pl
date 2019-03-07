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
ms.openlocfilehash: 00078d1d405eb2abc0d34f7b455fa045ac17c261
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485838"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="9db5d-102">ISymUnmanagedReader::GetGlobalVariables — Metoda</span><span class="sxs-lookup"><span data-stu-id="9db5d-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="9db5d-103">Zwraca wszystkie zmienne globalne.</span><span class="sxs-lookup"><span data-stu-id="9db5d-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9db5d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9db5d-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9db5d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9db5d-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="9db5d-106">[in] Długość buforu wskazywany przez `pcVars`.</span><span class="sxs-lookup"><span data-stu-id="9db5d-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="9db5d-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać zmiennych.</span><span class="sxs-lookup"><span data-stu-id="9db5d-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="9db5d-108">[out] Bufor, który zawiera zmienne.</span><span class="sxs-lookup"><span data-stu-id="9db5d-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9db5d-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9db5d-109">Return Value</span></span>  
 <span data-ttu-id="9db5d-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="9db5d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9db5d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9db5d-111">Requirements</span></span>  
 <span data-ttu-id="9db5d-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9db5d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9db5d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9db5d-113">See also</span></span>
- [<span data-ttu-id="9db5d-114">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="9db5d-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

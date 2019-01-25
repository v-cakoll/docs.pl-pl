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
ms.openlocfilehash: 61dd9f8a668904bb9b9e0b6b4d1d84d1ed07045d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737887"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="53138-102">ISymUnmanagedReader::GetGlobalVariables — Metoda</span><span class="sxs-lookup"><span data-stu-id="53138-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="53138-103">Zwraca wszystkie zmienne globalne.</span><span class="sxs-lookup"><span data-stu-id="53138-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53138-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="53138-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53138-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53138-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="53138-106">[in] Długość buforu wskazywany przez `pcVars`.</span><span class="sxs-lookup"><span data-stu-id="53138-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="53138-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać zmiennych.</span><span class="sxs-lookup"><span data-stu-id="53138-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="53138-108">[out] Bufor, który zawiera zmienne.</span><span class="sxs-lookup"><span data-stu-id="53138-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="53138-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="53138-109">Return Value</span></span>  
 <span data-ttu-id="53138-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="53138-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53138-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="53138-111">Requirements</span></span>  
 <span data-ttu-id="53138-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="53138-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53138-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53138-113">See also</span></span>
- [<span data-ttu-id="53138-114">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="53138-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

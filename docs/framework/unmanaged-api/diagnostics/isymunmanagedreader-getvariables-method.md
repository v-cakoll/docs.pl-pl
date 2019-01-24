---
title: ISymUnmanagedReader::GetVariables — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec1e2b59c15c956a4657b224a937829dbd3b14cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549905"
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="49bba-102">ISymUnmanagedReader::GetVariables — Metoda</span><span class="sxs-lookup"><span data-stu-id="49bba-102">ISymUnmanagedReader::GetVariables Method</span></span>
<span data-ttu-id="49bba-103">Zwraca wartość zmiennej inną niż lokalna, na jej nadrzędnej i nazwę.</span><span class="sxs-lookup"><span data-stu-id="49bba-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49bba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49bba-104">Syntax</span></span>  
  
```  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="49bba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49bba-105">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="49bba-106">[in] Element nadrzędny zmiennej.</span><span class="sxs-lookup"><span data-stu-id="49bba-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="49bba-107">[in] Rozmiar `pVars` tablicy.</span><span class="sxs-lookup"><span data-stu-id="49bba-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="49bba-108">[out] Wskaźnik do zmiennej, która odbiera liczbę zwracanych w zmiennych `pVars`.</span><span class="sxs-lookup"><span data-stu-id="49bba-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="49bba-109">[out] Wskaźnik do zmiennej, która odbiera zmienne.</span><span class="sxs-lookup"><span data-stu-id="49bba-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49bba-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="49bba-110">Return Value</span></span>  
 <span data-ttu-id="49bba-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="49bba-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49bba-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49bba-112">Requirements</span></span>  
 <span data-ttu-id="49bba-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="49bba-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49bba-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49bba-114">See also</span></span>
- [<span data-ttu-id="49bba-115">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="49bba-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

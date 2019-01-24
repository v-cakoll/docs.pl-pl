---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f068b4cae3832802ab53404d35a5a30673cd967d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561858"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="0da69-102">ISymUnmanagedENCUpdate::GetLocalVariableCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="0da69-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="0da69-103">Pobiera liczbę zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="0da69-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0da69-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0da69-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0da69-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0da69-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="0da69-106">[in] Token metadanych z metod.</span><span class="sxs-lookup"><span data-stu-id="0da69-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="0da69-107">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera w postaci, buforu, muszą zawierać liczbę zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="0da69-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0da69-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0da69-108">Return Value</span></span>  
 <span data-ttu-id="0da69-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="0da69-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0da69-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0da69-110">Requirements</span></span>  
 <span data-ttu-id="0da69-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0da69-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0da69-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0da69-112">See also</span></span>
- [<span data-ttu-id="0da69-113">ISymUnmanagedENCUpdate, interfejs</span><span class="sxs-lookup"><span data-stu-id="0da69-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

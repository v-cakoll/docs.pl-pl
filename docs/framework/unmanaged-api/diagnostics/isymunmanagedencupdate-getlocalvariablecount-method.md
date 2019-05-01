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
ms.openlocfilehash: 11a75ca89a3537ce8ee72e8ba24401800eacff20
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939740"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a><span data-ttu-id="722a9-102">ISymUnmanagedENCUpdate::GetLocalVariableCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="722a9-102">ISymUnmanagedENCUpdate::GetLocalVariableCount Method</span></span>
<span data-ttu-id="722a9-103">Pobiera liczbę zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="722a9-103">Gets the number of local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="722a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="722a9-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a><span data-ttu-id="722a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="722a9-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="722a9-106">[in] Token metadanych z metod.</span><span class="sxs-lookup"><span data-stu-id="722a9-106">[in] The metadata token of methods.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="722a9-107">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera w postaci, buforu, muszą zawierać liczbę zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="722a9-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the number of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="722a9-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="722a9-108">Return Value</span></span>  
 <span data-ttu-id="722a9-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="722a9-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="722a9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="722a9-110">Requirements</span></span>  
 <span data-ttu-id="722a9-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="722a9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="722a9-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="722a9-112">See also</span></span>

- [<span data-ttu-id="722a9-113">ISymUnmanagedENCUpdate, interfejs</span><span class="sxs-lookup"><span data-stu-id="722a9-113">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

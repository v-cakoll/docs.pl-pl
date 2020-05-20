---
title: ISymUnmanagedMethod::GetScopeFromOffset — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetScopeFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetScopeFromOffset
helpviewer_keywords:
- GetScopeFromOffset method [.NET Framework debugging]
- ISymUnmanagedMethod::GetScopeFromOffset method [.NET Framework debugging]
ms.assetid: d14cf210-81f8-46e1-8b19-6ddec0ba8b11
topic_type:
- apiref
ms.openlocfilehash: 4eefd019280f501a6ce194e5ce84388e32cc66e1
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615166"
---
# <a name="isymunmanagedmethodgetscopefromoffset-method"></a><span data-ttu-id="61e4a-102">ISymUnmanagedMethod::GetScopeFromOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="61e4a-102">ISymUnmanagedMethod::GetScopeFromOffset Method</span></span>
<span data-ttu-id="61e4a-103">Pobiera najbardziej otaczający zakres leksykalny w ramach tej metody, który obejmuje określone przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="61e4a-103">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span> <span data-ttu-id="61e4a-104">Służy do uruchamiania wyszukiwania zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="61e4a-104">This can be used to start local variable searches.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61e4a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="61e4a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeFromOffset(  
    [in]  ULONG32 offset,  
    [out, retval] ISymUnmanagedScope**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61e4a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="61e4a-106">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="61e4a-107">podczas A `ULONG` , który zawiera przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="61e4a-107">[in] A `ULONG` that contains the offset.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="61e4a-108">określoną Wskaźnik, który jest ustawiony na zwracany Interfejs [ISymUnmanagedScope](isymunmanagedscope-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="61e4a-108">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61e4a-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="61e4a-109">Return Value</span></span>  
 <span data-ttu-id="61e4a-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="61e4a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61e4a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61e4a-111">Requirements</span></span>  
 <span data-ttu-id="61e4a-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="61e4a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61e4a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61e4a-113">See also</span></span>

- [<span data-ttu-id="61e4a-114">ISymUnmanagedMethod — Interfejs</span><span class="sxs-lookup"><span data-stu-id="61e4a-114">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)

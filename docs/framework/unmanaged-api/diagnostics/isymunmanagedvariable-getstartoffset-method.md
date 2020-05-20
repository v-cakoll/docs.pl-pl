---
title: ISymUnmanagedVariable::GetStartOffset — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type:
- apiref
ms.openlocfilehash: f2996349fd2bf1765a3de5b67d3296a25b1eaa5e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610369"
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="90d13-102">ISymUnmanagedVariable::GetStartOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="90d13-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="90d13-103">Pobiera przesunięcie początku tej zmiennej w elemencie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="90d13-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="90d13-104">Jeśli jest to zmienna lokalna w zakresie, przesunięcie rozpoczęcia będzie należeć do przesunięć zdefiniowanych dla zakresu.</span><span class="sxs-lookup"><span data-stu-id="90d13-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90d13-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="90d13-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90d13-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="90d13-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="90d13-107">określoną Wskaźnik do elementu `ULONG32` , który odbiera przesunięcie rozpoczęcia.</span><span class="sxs-lookup"><span data-stu-id="90d13-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90d13-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="90d13-108">Return Value</span></span>  
 <span data-ttu-id="90d13-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="90d13-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90d13-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="90d13-110">Requirements</span></span>  
 <span data-ttu-id="90d13-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="90d13-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90d13-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90d13-112">See also</span></span>

- [<span data-ttu-id="90d13-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="90d13-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="90d13-114">GetEndOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="90d13-114">GetEndOffset Method</span></span>](isymunmanagedvariable-getendoffset-method.md)

---
title: ISymUnmanagedVariable::GetEndOffset — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type:
- apiref
ms.openlocfilehash: 91117eae23d38f3bc608f3203ebe53f92516c9c9
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610499"
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="edc9e-102">ISymUnmanagedVariable::GetEndOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="edc9e-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="edc9e-103">Pobiera przesunięcie końca tej zmiennej w elemencie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="edc9e-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="edc9e-104">Jeśli jest to zmienna lokalna w zakresie, przesunięcie końcowe będzie należeć do przesunięć zdefiniowanych dla zakresu.</span><span class="sxs-lookup"><span data-stu-id="edc9e-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edc9e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="edc9e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="edc9e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="edc9e-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="edc9e-107">określoną Wskaźnik do elementu `ULONG32` , który odbiera przesunięcie końcowe.</span><span class="sxs-lookup"><span data-stu-id="edc9e-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="edc9e-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="edc9e-108">Return Value</span></span>  
 <span data-ttu-id="edc9e-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="edc9e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edc9e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="edc9e-110">Requirements</span></span>  
 <span data-ttu-id="edc9e-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="edc9e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edc9e-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="edc9e-112">See also</span></span>

- [<span data-ttu-id="edc9e-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="edc9e-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="edc9e-114">GetStartOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="edc9e-114">GetStartOffset Method</span></span>](isymunmanagedvariable-getstartoffset-method.md)

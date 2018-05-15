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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e0f11614c6fa15034ef5fa3d68e41a936a9ff764
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="5dd03-102">ISymUnmanagedVariable::GetEndOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="5dd03-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="5dd03-103">Pobiera przesunięcia końcowego tej zmiennej w ramach jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="5dd03-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="5dd03-104">Jeśli to jest zmienną lokalną w zakresie, przesunięcie zakończenia będzie mieścić się w przesunięcia zdefiniowane dla zakresu.</span><span class="sxs-lookup"><span data-stu-id="5dd03-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dd03-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5dd03-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5dd03-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5dd03-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="5dd03-107">[out] Wskaźnik do `ULONG32` odbierająca przesunięcie zakończenia.</span><span class="sxs-lookup"><span data-stu-id="5dd03-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5dd03-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5dd03-108">Return Value</span></span>  
 <span data-ttu-id="5dd03-109">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="5dd03-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dd03-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5dd03-110">Requirements</span></span>  
 <span data-ttu-id="5dd03-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5dd03-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dd03-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5dd03-112">See Also</span></span>  
 [<span data-ttu-id="5dd03-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="5dd03-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="5dd03-114">GetStartOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="5dd03-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)

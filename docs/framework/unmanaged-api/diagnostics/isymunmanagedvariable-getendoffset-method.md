---
title: "ISymUnmanagedVariable::GetEndOffset — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetEndOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedVariable::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
ms.assetid: e5d777c5-d450-4c0f-999c-b3953ee22cfb
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b7a2dac8425cd852c6c17ee1674710f6798d3b1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetendoffset-method"></a><span data-ttu-id="a7e3a-102">ISymUnmanagedVariable::GetEndOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="a7e3a-102">ISymUnmanagedVariable::GetEndOffset Method</span></span>
<span data-ttu-id="a7e3a-103">Pobiera przesunięcia końcowego tej zmiennej w ramach jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-103">Gets the end offset of this variable within its parent.</span></span> <span data-ttu-id="a7e3a-104">Jeśli to jest zmienną lokalną w zakresie, przesunięcie zakończenia będzie mieścić się w przesunięcia zdefiniowane dla zakresu.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-104">If this is a local variable within a scope, the end offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7e3a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7e3a-105">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7e3a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7e3a-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a7e3a-107">[out] Wskaźnik do `ULONG32` odbierająca przesunięcie zakończenia.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-107">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7e3a-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a7e3a-108">Return Value</span></span>  
 <span data-ttu-id="a7e3a-109">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="a7e3a-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7e3a-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7e3a-110">Requirements</span></span>  
 <span data-ttu-id="a7e3a-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a7e3a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e3a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7e3a-112">See Also</span></span>  
 [<span data-ttu-id="a7e3a-113">ISymUnmanagedVariable — interfejs</span><span class="sxs-lookup"><span data-stu-id="a7e3a-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="a7e3a-114">GetStartOffset — metoda</span><span class="sxs-lookup"><span data-stu-id="a7e3a-114">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getstartoffset-method.md)

---
title: "ISymUnmanagedVariable::GetStartOffset — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetStartOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetStartOffset method [.NET Framework debugging]
ms.assetid: 63021fc1-9c2d-4788-811f-fe8ca077206a
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5b7fd3a64202224ef5a7cc348ee8e9974a664d09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedvariablegetstartoffset-method"></a><span data-ttu-id="0786e-102">ISymUnmanagedVariable::GetStartOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="0786e-102">ISymUnmanagedVariable::GetStartOffset Method</span></span>
<span data-ttu-id="0786e-103">Pobiera Przesunięcie początku tej zmiennej w ramach jego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="0786e-103">Gets the start offset of this variable within its parent.</span></span> <span data-ttu-id="0786e-104">Jeśli jest zmienną lokalną w zakresie, Przesunięcie początkowe będzie należeć przesunięcia zdefiniowane dla zakresu.</span><span class="sxs-lookup"><span data-stu-id="0786e-104">If this is a local variable within a scope, the start offset will fall within the offsets defined for the scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0786e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0786e-105">Syntax</span></span>  
  
```  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0786e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0786e-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="0786e-107">[out] Wskaźnik do `ULONG32` odbierająca Przesunięcie początku.</span><span class="sxs-lookup"><span data-stu-id="0786e-107">[out] A pointer to a `ULONG32` that receives the start offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0786e-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0786e-108">Return Value</span></span>  
 <span data-ttu-id="0786e-109">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="0786e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0786e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0786e-110">Requirements</span></span>  
 <span data-ttu-id="0786e-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0786e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0786e-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0786e-112">See Also</span></span>  
 [<span data-ttu-id="0786e-113">ISymUnmanagedVariable — interfejs</span><span class="sxs-lookup"><span data-stu-id="0786e-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="0786e-114">GetEndOffset — metoda</span><span class="sxs-lookup"><span data-stu-id="0786e-114">GetEndOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getendoffset-method.md)

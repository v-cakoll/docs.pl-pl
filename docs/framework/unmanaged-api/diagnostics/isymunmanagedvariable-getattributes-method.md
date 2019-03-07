---
title: ISymUnmanagedVariable::GetAttributes — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAttributes
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d1585ccfa560d31fc32dce2f39dd525c51711797
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466339"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="69c70-102">ISymUnmanagedVariable::GetAttributes — Metoda</span><span class="sxs-lookup"><span data-stu-id="69c70-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="69c70-103">Pobiera flagi atrybutów dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="69c70-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69c70-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69c70-104">Syntax</span></span>  
  
```  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69c70-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69c70-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="69c70-106">[out] Wskaźnik do `ULONG32` odbierająca atrybutów.</span><span class="sxs-lookup"><span data-stu-id="69c70-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="69c70-107">Zwrócona wartość będzie jedna z wartości zdefiniowanych w [corsymvarflag —](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="69c70-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69c70-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="69c70-108">Return Value</span></span>  
 <span data-ttu-id="69c70-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="69c70-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69c70-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69c70-110">Requirements</span></span>  
 <span data-ttu-id="69c70-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="69c70-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69c70-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69c70-112">See also</span></span>
- [<span data-ttu-id="69c70-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="69c70-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)

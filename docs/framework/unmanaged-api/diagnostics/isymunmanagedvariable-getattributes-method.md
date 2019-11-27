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
ms.openlocfilehash: cfc28dfcda7bf4b3d1fc6fe3530a212ee76fadd2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446088"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="ce3b7-102">ISymUnmanagedVariable::GetAttributes — Metoda</span><span class="sxs-lookup"><span data-stu-id="ce3b7-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="ce3b7-103">Pobiera flagi atrybutu dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ce3b7-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce3b7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce3b7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce3b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce3b7-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="ce3b7-106">określoną Wskaźnik do `ULONG32`, który odbiera atrybuty.</span><span class="sxs-lookup"><span data-stu-id="ce3b7-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="ce3b7-107">Zwrócona wartość będzie jedną z wartości zdefiniowanych w wyliczeniu [CorSymVarFlag —](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ce3b7-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ce3b7-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ce3b7-108">Return Value</span></span>  
 <span data-ttu-id="ce3b7-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="ce3b7-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce3b7-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce3b7-110">Requirements</span></span>  
 <span data-ttu-id="ce3b7-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ce3b7-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce3b7-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ce3b7-112">See also</span></span>

- [<span data-ttu-id="ce3b7-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="ce3b7-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)

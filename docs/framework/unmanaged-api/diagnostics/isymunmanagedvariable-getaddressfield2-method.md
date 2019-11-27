---
title: ISymUnmanagedVariable::GetAddressField2 — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField2
helpviewer_keywords:
- GetAddressField2 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField2 method [.NET Framework debugging]
ms.assetid: 1f25b294-72b6-4882-a49b-6c9d364b6008
topic_type:
- apiref
ms.openlocfilehash: 794615994cd11ee00c2a381b9ba883cebb8233a0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446127"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="dffbe-102">ISymUnmanagedVariable::GetAddressField2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="dffbe-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="dffbe-103">Pobiera drugie pole adresu dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="dffbe-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="dffbe-104">Jego znaczenie zależy od rodzaju adresu.</span><span class="sxs-lookup"><span data-stu-id="dffbe-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dffbe-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dffbe-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dffbe-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dffbe-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="dffbe-107">określoną Wskaźnik do `ULONG32`, który odbiera drugie pole adresu.</span><span class="sxs-lookup"><span data-stu-id="dffbe-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dffbe-108">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="dffbe-108">Return Value</span></span>  
 <span data-ttu-id="dffbe-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="dffbe-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dffbe-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dffbe-110">Requirements</span></span>  
 <span data-ttu-id="dffbe-111">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="dffbe-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dffbe-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dffbe-112">See also</span></span>

- [<span data-ttu-id="dffbe-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="dffbe-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="dffbe-114">GetAddressField1, metoda</span><span class="sxs-lookup"><span data-stu-id="dffbe-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="dffbe-115">GetAddressField3, metoda</span><span class="sxs-lookup"><span data-stu-id="dffbe-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="dffbe-116">GetAddressKind, metoda</span><span class="sxs-lookup"><span data-stu-id="dffbe-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)

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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a283915f8326a19c7d2c9b45851b9879fe0ec17
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634990"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="b10ac-102">ISymUnmanagedVariable::GetAddressField2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="b10ac-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="b10ac-103">Pobiera drugie pole Adres dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b10ac-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="b10ac-104">Znaczenia, zależy od rodzaju adresu.</span><span class="sxs-lookup"><span data-stu-id="b10ac-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b10ac-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b10ac-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b10ac-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b10ac-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="b10ac-107">[out] Wskaźnik do `ULONG32` odbierająca drugie pole adres.</span><span class="sxs-lookup"><span data-stu-id="b10ac-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b10ac-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b10ac-108">Return Value</span></span>  
 <span data-ttu-id="b10ac-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="b10ac-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b10ac-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b10ac-110">Requirements</span></span>  
 <span data-ttu-id="b10ac-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b10ac-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b10ac-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b10ac-112">See also</span></span>
- [<span data-ttu-id="b10ac-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="b10ac-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="b10ac-114">GetAddressField1, metoda</span><span class="sxs-lookup"><span data-stu-id="b10ac-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="b10ac-115">GetAddressField3, metoda</span><span class="sxs-lookup"><span data-stu-id="b10ac-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="b10ac-116">GetAddressKind, metoda</span><span class="sxs-lookup"><span data-stu-id="b10ac-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)

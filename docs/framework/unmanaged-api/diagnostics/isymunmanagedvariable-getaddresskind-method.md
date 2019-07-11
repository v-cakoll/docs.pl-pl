---
title: ISymUnmanagedVariable::GetAddressKind — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressKind
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6b5fd3c5e5a7a706929af849ec3a66dd6c41b3bd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778287"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="50c5d-102">ISymUnmanagedVariable::GetAddressKind — Metoda</span><span class="sxs-lookup"><span data-stu-id="50c5d-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="50c5d-103">Pobiera rodzaj adres tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="50c5d-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50c5d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50c5d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50c5d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="50c5d-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="50c5d-106">[out] Wskaźnik do `ULONG32` , która otrzymuje wartość.</span><span class="sxs-lookup"><span data-stu-id="50c5d-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="50c5d-107">Możliwe wartości są zdefiniowane w [corsymaddrkind —](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="50c5d-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50c5d-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="50c5d-108">Return Value</span></span>  
 <span data-ttu-id="50c5d-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="50c5d-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50c5d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50c5d-110">Requirements</span></span>  
 <span data-ttu-id="50c5d-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="50c5d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c5d-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50c5d-112">See also</span></span>

- [<span data-ttu-id="50c5d-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="50c5d-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)

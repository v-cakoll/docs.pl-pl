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
ms.openlocfilehash: eae5b21af3bcdca911ec13067a61bb957d4ae6ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092945"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="e0208-102">ISymUnmanagedVariable::GetAddressKind — Metoda</span><span class="sxs-lookup"><span data-stu-id="e0208-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="e0208-103">Pobiera rodzaj adres tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e0208-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0208-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0208-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0208-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0208-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="e0208-106">[out] Wskaźnik do `ULONG32` , która otrzymuje wartość.</span><span class="sxs-lookup"><span data-stu-id="e0208-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="e0208-107">Możliwe wartości są zdefiniowane w [corsymaddrkind —](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="e0208-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0208-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e0208-108">Return Value</span></span>  
 <span data-ttu-id="e0208-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="e0208-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0208-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0208-110">Requirements</span></span>  
 <span data-ttu-id="e0208-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e0208-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0208-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0208-112">See also</span></span>

- [<span data-ttu-id="e0208-113">ISymUnmanagedVariable — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e0208-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)

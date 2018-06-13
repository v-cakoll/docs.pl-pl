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
ms.openlocfilehash: 18e83582a73ba3b2eb2538bcdf60984c46131768
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426958"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="498e1-102">ISymUnmanagedVariable::GetAddressKind — Metoda</span><span class="sxs-lookup"><span data-stu-id="498e1-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="498e1-103">Pobiera rodzaj adresu tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="498e1-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="498e1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="498e1-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="498e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="498e1-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="498e1-106">[out] Wskaźnik do `ULONG32` odbierająca wartość.</span><span class="sxs-lookup"><span data-stu-id="498e1-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="498e1-107">Możliwe wartości są definiowane w [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="498e1-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="498e1-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="498e1-108">Return Value</span></span>  
 <span data-ttu-id="498e1-109">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="498e1-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="498e1-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="498e1-110">Requirements</span></span>  
 <span data-ttu-id="498e1-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="498e1-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="498e1-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="498e1-112">See Also</span></span>  
 [<span data-ttu-id="498e1-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="498e1-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)

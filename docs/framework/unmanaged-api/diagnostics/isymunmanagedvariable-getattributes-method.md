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
ms.openlocfilehash: f7e71315b5ff99a550ae4a59f3b0d444093dac01
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778277"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="abcfe-102">ISymUnmanagedVariable::GetAttributes — Metoda</span><span class="sxs-lookup"><span data-stu-id="abcfe-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="abcfe-103">Pobiera flagi atrybutów dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="abcfe-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abcfe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="abcfe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abcfe-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="abcfe-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="abcfe-106">[out] Wskaźnik do `ULONG32` odbierająca atrybutów.</span><span class="sxs-lookup"><span data-stu-id="abcfe-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="abcfe-107">Zwrócona wartość będzie jedna z wartości zdefiniowanych w [corsymvarflag —](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="abcfe-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abcfe-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="abcfe-108">Return Value</span></span>  
 <span data-ttu-id="abcfe-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="abcfe-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abcfe-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="abcfe-110">Requirements</span></span>  
 <span data-ttu-id="abcfe-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="abcfe-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abcfe-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="abcfe-112">See also</span></span>

- [<span data-ttu-id="abcfe-113">ISymUnmanagedVariable, interfejs</span><span class="sxs-lookup"><span data-stu-id="abcfe-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)

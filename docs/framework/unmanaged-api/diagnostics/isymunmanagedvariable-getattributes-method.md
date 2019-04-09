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
ms.openlocfilehash: d7ba794060330de3934f8d4ca6434b09672d12bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090592"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="d4bbf-102">ISymUnmanagedVariable::GetAttributes — Metoda</span><span class="sxs-lookup"><span data-stu-id="d4bbf-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="d4bbf-103">Pobiera flagi atrybutów dla tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d4bbf-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4bbf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4bbf-104">Syntax</span></span>  
  
```  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4bbf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4bbf-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="d4bbf-106">[out] Wskaźnik do `ULONG32` odbierająca atrybutów.</span><span class="sxs-lookup"><span data-stu-id="d4bbf-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="d4bbf-107">Zwrócona wartość będzie jedna z wartości zdefiniowanych w [corsymvarflag —](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d4bbf-107">The returned value will be one of the values defined in the [CorSymVarFlag](../../../../docs/framework/unmanaged-api/diagnostics/corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4bbf-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d4bbf-108">Return Value</span></span>  
 <span data-ttu-id="d4bbf-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="d4bbf-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4bbf-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d4bbf-110">Requirements</span></span>  
 <span data-ttu-id="d4bbf-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d4bbf-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4bbf-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4bbf-112">See also</span></span>

- [<span data-ttu-id="d4bbf-113">ISymUnmanagedVariable — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d4bbf-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)

---
title: ISymUnmanagedScope::GetEndOffset — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e28a351b6d47d14f171b9e760b2fa2c6755e3f8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986199"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="25d2f-102">ISymUnmanagedScope::GetEndOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="25d2f-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="25d2f-103">Pobiera wartość przesunięcia końcowego dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="25d2f-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25d2f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25d2f-104">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25d2f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25d2f-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="25d2f-106">[out] Wskaźnik do `ULONG32` odbierająca przesunięcia końcowego.</span><span class="sxs-lookup"><span data-stu-id="25d2f-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25d2f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="25d2f-107">Return Value</span></span>  
 <span data-ttu-id="25d2f-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="25d2f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25d2f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25d2f-109">Requirements</span></span>  
 <span data-ttu-id="25d2f-110">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="25d2f-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25d2f-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25d2f-111">See also</span></span>

- [<span data-ttu-id="25d2f-112">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="25d2f-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="25d2f-113">GetStartOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="25d2f-113">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)

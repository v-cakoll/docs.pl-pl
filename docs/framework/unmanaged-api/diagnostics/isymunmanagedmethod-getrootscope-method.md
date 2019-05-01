---
title: ISymUnmanagedMethod::GetRootScope — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRootScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7c77be0dde950693d3943e41c392dcdcd9bc995e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939610"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="0f4c3-102">ISymUnmanagedMethod::GetRootScope — Metoda</span><span class="sxs-lookup"><span data-stu-id="0f4c3-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="0f4c3-103">Pobiera zakres leksykalne głównego w ramach tej metody.</span><span class="sxs-lookup"><span data-stu-id="0f4c3-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="0f4c3-104">Ten zakres obejmuje całą metodę.</span><span class="sxs-lookup"><span data-stu-id="0f4c3-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f4c3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f4c3-105">Syntax</span></span>  
  
```  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f4c3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0f4c3-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="0f4c3-107">[out] Wskaźnik, który jest ustawiony do zwracanego [isymunmanagedscope —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0f4c3-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f4c3-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0f4c3-108">Return Value</span></span>  
 <span data-ttu-id="0f4c3-109">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="0f4c3-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f4c3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0f4c3-110">Requirements</span></span>  
 <span data-ttu-id="0f4c3-111">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0f4c3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f4c3-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f4c3-112">See also</span></span>

- [<span data-ttu-id="0f4c3-113">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="0f4c3-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

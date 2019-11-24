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
ms.openlocfilehash: 25a8188e3ab62c095355b72b3e63e767a6768114
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446351"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="5e627-102">ISymUnmanagedScope::GetEndOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="5e627-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="5e627-103">Gets the end offset for this scope.</span><span class="sxs-lookup"><span data-stu-id="5e627-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e627-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e627-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e627-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e627-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="5e627-106">[out] A pointer to a `ULONG32` that receives the end offset.</span><span class="sxs-lookup"><span data-stu-id="5e627-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e627-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5e627-107">Return Value</span></span>  
 <span data-ttu-id="5e627-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="5e627-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e627-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e627-109">Requirements</span></span>  
 <span data-ttu-id="5e627-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5e627-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e627-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e627-111">See also</span></span>

- [<span data-ttu-id="5e627-112">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e627-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="5e627-113">GetStartOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="5e627-113">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)

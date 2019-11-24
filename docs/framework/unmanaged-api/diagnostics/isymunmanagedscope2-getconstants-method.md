---
title: ISymUnmanagedScope2::GetConstants — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
ms.openlocfilehash: f7cd45a90a750c357706f720453ff23697875b58
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446238"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="00f7b-102">ISymUnmanagedScope2::GetConstants — Metoda</span><span class="sxs-lookup"><span data-stu-id="00f7b-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="00f7b-103">Gets the local constants defined within this scope.</span><span class="sxs-lookup"><span data-stu-id="00f7b-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00f7b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00f7b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*   
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00f7b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00f7b-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="00f7b-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span><span class="sxs-lookup"><span data-stu-id="00f7b-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="00f7b-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span><span class="sxs-lookup"><span data-stu-id="00f7b-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="00f7b-108">[out] The buffer that stores the constants.</span><span class="sxs-lookup"><span data-stu-id="00f7b-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00f7b-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="00f7b-109">Return Value</span></span>  
 <span data-ttu-id="00f7b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="00f7b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00f7b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00f7b-111">Requirements</span></span>  
 <span data-ttu-id="00f7b-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="00f7b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00f7b-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00f7b-113">See also</span></span>

- [<span data-ttu-id="00f7b-114">ISymUnmanagedScope2, interfejs</span><span class="sxs-lookup"><span data-stu-id="00f7b-114">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)

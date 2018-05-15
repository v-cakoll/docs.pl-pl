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
ms.openlocfilehash: d13006bc5c09ed065ae1671ee75cf8dce066669d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="5876e-102">ISymUnmanagedScope::GetEndOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="5876e-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="5876e-103">Pobiera przesunięcie zakończenia dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="5876e-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5876e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5876e-104">Syntax</span></span>  
  
```  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5876e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5876e-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="5876e-106">[out] Wskaźnik do `ULONG32` odbierająca przesunięcie zakończenia.</span><span class="sxs-lookup"><span data-stu-id="5876e-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5876e-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5876e-107">Return Value</span></span>  
 <span data-ttu-id="5876e-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="5876e-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5876e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5876e-109">Requirements</span></span>  
 <span data-ttu-id="5876e-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5876e-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5876e-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5876e-111">See Also</span></span>  
 [<span data-ttu-id="5876e-112">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="5876e-112">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 [<span data-ttu-id="5876e-113">GetStartOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="5876e-113">GetStartOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)

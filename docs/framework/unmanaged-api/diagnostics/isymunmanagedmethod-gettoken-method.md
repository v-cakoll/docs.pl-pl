---
title: ISymUnmanagedMethod::GetToken — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89ae648e38b6349bfad0a37724a9bdc1ae05e365
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="e8d13-102">ISymUnmanagedMethod::GetToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="e8d13-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="e8d13-103">Zwraca token metadanych dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="e8d13-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8d13-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8d13-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8d13-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8d13-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="e8d13-106">[out] Wskaźnik do `mdMethodDef` rozmiaru, który odbiera znakami muszą zawierać metadane buforu.</span><span class="sxs-lookup"><span data-stu-id="e8d13-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8d13-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e8d13-107">Return Value</span></span>  
 <span data-ttu-id="e8d13-108">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e8d13-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8d13-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8d13-109">Requirements</span></span>  
 <span data-ttu-id="e8d13-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e8d13-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d13-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8d13-111">See Also</span></span>  
 [<span data-ttu-id="e8d13-112">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="e8d13-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

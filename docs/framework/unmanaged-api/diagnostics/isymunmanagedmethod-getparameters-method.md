---
title: "ISymUnmanagedMethod::GetParameters — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetParameters
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetParameters
helpviewer_keywords:
- ISymUnmanagedMethod::GetParameters method [.NET Framework debugging]
- GetParameters method [.NET Framework debugging]
ms.assetid: 3a8074f1-facc-4a3f-bb9b-d6574fc2fc74
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1a2e3471b63f819bfe1879b87e42ff9258036356
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="b698c-102">ISymUnmanagedMethod::GetParameters — Metoda</span><span class="sxs-lookup"><span data-stu-id="b698c-102">ISymUnmanagedMethod::GetParameters Method</span></span>
<span data-ttu-id="b698c-103">Pobiera parametry dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="b698c-103">Gets the parameters for this method.</span></span> <span data-ttu-id="b698c-104">Parametry są zwracane w kolejności, w którym są definiowane w podpisie metody.</span><span class="sxs-lookup"><span data-stu-id="b698c-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b698c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b698c-105">Syntax</span></span>  
  
```  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b698c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b698c-106">Parameters</span></span>  
 `cParams`  
 <span data-ttu-id="b698c-107">[in] Rozmiar `params` tablicy.</span><span class="sxs-lookup"><span data-stu-id="b698c-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="b698c-108">[in] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, który jest wymagany do zawierają parametry.</span><span class="sxs-lookup"><span data-stu-id="b698c-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="b698c-109">[out] Wskaźnik do buforu, który odbiera parametrów.</span><span class="sxs-lookup"><span data-stu-id="b698c-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b698c-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b698c-110">Return Value</span></span>  
 <span data-ttu-id="b698c-111">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="b698c-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b698c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b698c-112">Requirements</span></span>  
 <span data-ttu-id="b698c-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b698c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b698c-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b698c-114">See Also</span></span>  
 [<span data-ttu-id="b698c-115">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="b698c-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

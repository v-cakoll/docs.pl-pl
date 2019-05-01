---
title: ISymUnmanagedMethod::GetParameters — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetParameters
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetParameters
helpviewer_keywords:
- ISymUnmanagedMethod::GetParameters method [.NET Framework debugging]
- GetParameters method [.NET Framework debugging]
ms.assetid: 3a8074f1-facc-4a3f-bb9b-d6574fc2fc74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a757e3b28a94c96e28a5bab736a6820a83617a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939636"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="6374d-102">ISymUnmanagedMethod::GetParameters — Metoda</span><span class="sxs-lookup"><span data-stu-id="6374d-102">ISymUnmanagedMethod::GetParameters Method</span></span>
<span data-ttu-id="6374d-103">Pobiera parametry dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="6374d-103">Gets the parameters for this method.</span></span> <span data-ttu-id="6374d-104">Parametry są zwracane w kolejności, w której są zdefiniowane w podpisie metody.</span><span class="sxs-lookup"><span data-stu-id="6374d-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6374d-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6374d-105">Syntax</span></span>  
  
```  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6374d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6374d-106">Parameters</span></span>  
 `cParams`  
 <span data-ttu-id="6374d-107">[in] Rozmiar `params` tablicy.</span><span class="sxs-lookup"><span data-stu-id="6374d-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="6374d-108">[in] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, który jest wymagany do zawierać parametry.</span><span class="sxs-lookup"><span data-stu-id="6374d-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="6374d-109">[out] Wskaźnik do buforu, który otrzymuje parametrów.</span><span class="sxs-lookup"><span data-stu-id="6374d-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6374d-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6374d-110">Return Value</span></span>  
 <span data-ttu-id="6374d-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="6374d-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6374d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6374d-112">Requirements</span></span>  
 <span data-ttu-id="6374d-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6374d-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6374d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6374d-114">See also</span></span>

- [<span data-ttu-id="6374d-115">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="6374d-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

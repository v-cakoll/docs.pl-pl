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
ms.openlocfilehash: 9e8139a822c877e70731e18ae5a75b83e6b7578e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448956"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="33548-102">ISymUnmanagedMethod::GetParameters — Metoda</span><span class="sxs-lookup"><span data-stu-id="33548-102">ISymUnmanagedMethod::GetParameters Method</span></span>
<span data-ttu-id="33548-103">Pobiera parametry dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="33548-103">Gets the parameters for this method.</span></span> <span data-ttu-id="33548-104">Parametry są zwracane w kolejności, w jakiej są zdefiniowane w podpisie metody.</span><span class="sxs-lookup"><span data-stu-id="33548-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33548-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="33548-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33548-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="33548-106">Parameters</span></span>  
 `cParams`  
 <span data-ttu-id="33548-107">podczas Rozmiar tablicy `params`.</span><span class="sxs-lookup"><span data-stu-id="33548-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="33548-108">podczas Wskaźnik do `ULONG32`, który odbiera rozmiar buforu, który jest wymagany do zawierania parametrów.</span><span class="sxs-lookup"><span data-stu-id="33548-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="33548-109">określoną Wskaźnik do buforu, który odbiera parametry.</span><span class="sxs-lookup"><span data-stu-id="33548-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33548-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="33548-110">Return Value</span></span>  
 <span data-ttu-id="33548-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="33548-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33548-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33548-112">Requirements</span></span>  
 <span data-ttu-id="33548-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="33548-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33548-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33548-114">See also</span></span>

- [<span data-ttu-id="33548-115">ISymUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="33548-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

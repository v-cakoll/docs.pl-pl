---
title: ISymUnmanagedNamespace::GetVariables — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetVariables
helpviewer_keywords:
- ISymUnmanagedNamespace::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: ea7c1617-f3ce-4220-8288-f2b50eaf0f0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 813f57377c1885b09190ada3c73f4391a3f2d931
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895048"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="3cc5d-102">ISymUnmanagedNamespace::GetVariables — Metoda</span><span class="sxs-lookup"><span data-stu-id="3cc5d-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="3cc5d-103">Zwraca wszystkie zmienne zdefiniowane w zakresie globalnym w tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3cc5d-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cc5d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3cc5d-104">Syntax</span></span>  
  
```cpp
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cc5d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3cc5d-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="3cc5d-106">podczas `ULONG32` Wskazuje rozmiar`pVars` tablicy.</span><span class="sxs-lookup"><span data-stu-id="3cc5d-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="3cc5d-107">określoną Wskaźnik do `ULONG32` obiektu, który odbiera rozmiar buforu wymaganego do przechowywania przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3cc5d-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="3cc5d-108">określoną Wskaźnik do buforu, który zawiera przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="3cc5d-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3cc5d-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3cc5d-109">Return Value</span></span>  
 <span data-ttu-id="3cc5d-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie, E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="3cc5d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cc5d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3cc5d-111">Requirements</span></span>  
 <span data-ttu-id="3cc5d-112">**Nagłówki** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3cc5d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc5d-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3cc5d-113">See also</span></span>

- [<span data-ttu-id="3cc5d-114">ISymUnmanagedNamespace, interfejs</span><span class="sxs-lookup"><span data-stu-id="3cc5d-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)

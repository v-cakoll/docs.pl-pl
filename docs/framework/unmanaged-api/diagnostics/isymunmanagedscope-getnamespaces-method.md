---
title: ISymUnmanagedScope::GetNamespaces — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3dc3c842bbb4b86b82d03848751673400bed193b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213041"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="6d314-102">ISymUnmanagedScope::GetNamespaces — Metoda</span><span class="sxs-lookup"><span data-stu-id="6d314-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="6d314-103">Pobiera przestrzenie nazw, które są używane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="6d314-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d314-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d314-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d314-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d314-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="6d314-106">[in] Rozmiar `namespaces` tablicy.</span><span class="sxs-lookup"><span data-stu-id="6d314-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="6d314-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="6d314-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="6d314-108">[out] Tablica, która odbiera przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6d314-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d314-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6d314-109">Return Value</span></span>  
 <span data-ttu-id="6d314-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="6d314-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d314-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d314-111">Requirements</span></span>  
 <span data-ttu-id="6d314-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6d314-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d314-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d314-113">See also</span></span>

- [<span data-ttu-id="6d314-114">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d314-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)

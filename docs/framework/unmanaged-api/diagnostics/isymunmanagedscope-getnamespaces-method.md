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
ms.openlocfilehash: c786cd43a25aa0c69c19e57452a3b190c7bfb167
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426844"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="9e681-102">ISymUnmanagedScope::GetNamespaces — Metoda</span><span class="sxs-lookup"><span data-stu-id="9e681-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="9e681-103">Pobiera przestrzenie nazw, które są używane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="9e681-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e681-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e681-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e681-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e681-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="9e681-106">[in] Rozmiar `namespaces` tablicy.</span><span class="sxs-lookup"><span data-stu-id="9e681-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="9e681-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="9e681-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="9e681-108">[out] Tablica, która odbiera przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="9e681-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e681-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9e681-109">Return Value</span></span>  
 <span data-ttu-id="9e681-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="9e681-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e681-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e681-111">Requirements</span></span>  
 <span data-ttu-id="9e681-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9e681-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e681-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e681-113">See Also</span></span>  
 [<span data-ttu-id="9e681-114">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="9e681-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)

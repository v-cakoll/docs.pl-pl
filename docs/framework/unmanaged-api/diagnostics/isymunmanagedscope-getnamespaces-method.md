---
title: "ISymUnmanagedScope::GetNamespaces — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetNamespaces
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25f6fc01d418693f62092d338cf93b1762bcfc8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="d1aef-102">ISymUnmanagedScope::GetNamespaces — Metoda</span><span class="sxs-lookup"><span data-stu-id="d1aef-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="d1aef-103">Pobiera przestrzenie nazw, które są używane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="d1aef-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1aef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1aef-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1aef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1aef-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="d1aef-106">[in] Rozmiar `namespaces` tablicy.</span><span class="sxs-lookup"><span data-stu-id="d1aef-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="d1aef-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="d1aef-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="d1aef-108">[out] Tablica, która odbiera przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="d1aef-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d1aef-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d1aef-109">Return Value</span></span>  
 <span data-ttu-id="d1aef-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="d1aef-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1aef-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1aef-111">Requirements</span></span>  
 <span data-ttu-id="d1aef-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d1aef-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1aef-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1aef-113">See Also</span></span>  
 [<span data-ttu-id="d1aef-114">ISymUnmanagedScope, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1aef-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)

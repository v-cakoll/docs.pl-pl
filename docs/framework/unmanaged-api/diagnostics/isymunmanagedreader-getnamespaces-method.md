---
title: ISymUnmanagedReader::GetNamespaces — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 570532433483e9d0a08f4d685087c0736e135390
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993307"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="870d1-102">ISymUnmanagedReader::GetNamespaces — Metoda</span><span class="sxs-lookup"><span data-stu-id="870d1-102">ISymUnmanagedReader::GetNamespaces Method</span></span>
<span data-ttu-id="870d1-103">Pobiera przestrzenie nazw zdefiniowane w zakresie globalnym, w tym magazynie symboli.</span><span class="sxs-lookup"><span data-stu-id="870d1-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="870d1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="870d1-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="870d1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="870d1-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="870d1-106">[in] Rozmiar tablicy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="870d1-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="870d1-107">[out] Wskaźnik do zmiennej, która odbiera długość listy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="870d1-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="870d1-108">[out] Wskaźnik do zmiennej, która odbiera listę przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="870d1-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="870d1-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="870d1-109">Return Value</span></span>  
 <span data-ttu-id="870d1-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="870d1-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="870d1-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="870d1-111">Requirements</span></span>  
 <span data-ttu-id="870d1-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="870d1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="870d1-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="870d1-113">See also</span></span>

- [<span data-ttu-id="870d1-114">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="870d1-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

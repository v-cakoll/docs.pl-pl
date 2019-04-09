---
title: ISymUnmanagedNamespace::GetName — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9017eeaf8e80c3dc0b546c1f3c2fb54634b3e949
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186436"
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="95a27-102">ISymUnmanagedNamespace::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="95a27-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="95a27-103">Pobiera nazwę tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="95a27-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95a27-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="95a27-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95a27-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95a27-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="95a27-106">[in] A `ULONG32` oznacza rozmiar `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="95a27-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="95a27-107">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera w postaci, buforu, muszą zawierać nazwę przestrzeni nazw, w tym zakończenia o wartości null.</span><span class="sxs-lookup"><span data-stu-id="95a27-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="95a27-108">[out] Wskaźnik do buforu, który zawiera nazwę przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="95a27-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95a27-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="95a27-109">Return Value</span></span>  
 <span data-ttu-id="95a27-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="95a27-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95a27-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="95a27-111">Requirements</span></span>  
 <span data-ttu-id="95a27-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="95a27-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a27-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95a27-113">See also</span></span>

- [<span data-ttu-id="95a27-114">ISymUnmanagedNamespace — Interfejs</span><span class="sxs-lookup"><span data-stu-id="95a27-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)

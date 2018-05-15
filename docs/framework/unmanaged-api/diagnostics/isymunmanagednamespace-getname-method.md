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
ms.openlocfilehash: aeb3c4e9a1d87b2d93a310b88c340aec0955a845
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="2282c-102">ISymUnmanagedNamespace::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="2282c-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="2282c-103">Pobiera nazwę tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2282c-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2282c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2282c-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2282c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2282c-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="2282c-106">[in] A `ULONG32` wskazuje, że rozmiar `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="2282c-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="2282c-107">[out] Wskaźnik do `ULONG32` rozmiaru, który odbiera w znaki buforu, muszą zawierać nazwę przestrzeni nazw, takie jak zakończenie wartości null.</span><span class="sxs-lookup"><span data-stu-id="2282c-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="2282c-108">[out] Wskaźnik do buforu, który zawiera nazwę przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2282c-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2282c-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="2282c-109">Return Value</span></span>  
 <span data-ttu-id="2282c-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="2282c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2282c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2282c-111">Requirements</span></span>  
 <span data-ttu-id="2282c-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2282c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2282c-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2282c-113">See Also</span></span>  
 [<span data-ttu-id="2282c-114">ISymUnmanagedNamespace, interfejs</span><span class="sxs-lookup"><span data-stu-id="2282c-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)

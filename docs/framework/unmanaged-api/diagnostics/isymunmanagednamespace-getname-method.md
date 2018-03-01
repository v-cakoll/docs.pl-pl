---
title: "ISymUnmanagedNamespace::GetName — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 37b29e71a9a1185a7080f71b1621a07dd7ae41a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="26945-102">ISymUnmanagedNamespace::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="26945-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="26945-103">Pobiera nazwę tej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="26945-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26945-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26945-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26945-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26945-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="26945-106">[in] A `ULONG32` wskazuje, że rozmiar `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="26945-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="26945-107">[out] Wskaźnik do `ULONG32` rozmiaru, który odbiera w znaki buforu, muszą zawierać nazwę przestrzeni nazw, takie jak zakończenie wartości null.</span><span class="sxs-lookup"><span data-stu-id="26945-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="26945-108">[out] Wskaźnik do buforu, który zawiera nazwę przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="26945-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="26945-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="26945-109">Return Value</span></span>  
 <span data-ttu-id="26945-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="26945-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26945-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26945-111">Requirements</span></span>  
 <span data-ttu-id="26945-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="26945-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26945-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26945-113">See Also</span></span>  
 [<span data-ttu-id="26945-114">ISymUnmanagedNamespace, interfejs</span><span class="sxs-lookup"><span data-stu-id="26945-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)

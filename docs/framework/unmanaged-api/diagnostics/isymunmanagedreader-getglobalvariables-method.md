---
title: "ISymUnmanagedReader::GetGlobalVariables — Metoda"
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
- ISymUnmanagedReader.GetGlobalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetGlobalVariables
helpviewer_keywords:
- GetGlobalVariables method [.NET Framework debugging]
- ISymUnmanagedReader::GetGlobalVariables method [.NET Framework debugging]
ms.assetid: a2dd5098-3e58-4be5-b7a2-e4160b3b505a
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b17abe352dc37b366294e72de53bcc4e1ad8dc9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="0da4e-102">ISymUnmanagedReader::GetGlobalVariables — Metoda</span><span class="sxs-lookup"><span data-stu-id="0da4e-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="0da4e-103">Zwraca wszystkie zmienne globalne.</span><span class="sxs-lookup"><span data-stu-id="0da4e-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0da4e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0da4e-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0da4e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0da4e-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="0da4e-106">[in] Długość buforu wskazywana przez `pcVars`.</span><span class="sxs-lookup"><span data-stu-id="0da4e-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="0da4e-107">[out] Wskaźnik do `ULONG32` odbierająca rozmiar buforu, muszą zawierać zmiennych.</span><span class="sxs-lookup"><span data-stu-id="0da4e-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="0da4e-108">[out] Bufor, który zawiera zmienne.</span><span class="sxs-lookup"><span data-stu-id="0da4e-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0da4e-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0da4e-109">Return Value</span></span>  
 <span data-ttu-id="0da4e-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="0da4e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0da4e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0da4e-111">Requirements</span></span>  
 <span data-ttu-id="0da4e-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0da4e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0da4e-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0da4e-113">See Also</span></span>  
 [<span data-ttu-id="0da4e-114">ISymUnmanagedReader, interfejs</span><span class="sxs-lookup"><span data-stu-id="0da4e-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

---
title: "ISymENCUnmanagedMethod::GetFileNameFromOffset — Metoda"
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
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f4b760f2782cf75cf0ab0879eb77e185a93b8b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="b42f9-102">ISymENCUnmanagedMethod::GetFileNameFromOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="b42f9-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="b42f9-103">Pobiera nazwę pliku dla wiersz skojarzony z przesunięciem.</span><span class="sxs-lookup"><span data-stu-id="b42f9-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b42f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b42f9-104">Syntax</span></span>  
  
```  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b42f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b42f9-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="b42f9-106">[in] A `ULONG32` zawiera przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="b42f9-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="b42f9-107">[in] A `ULONG32` wskazuje, że rozmiar `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="b42f9-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b42f9-108">[out] Wskaźnik do `ULONG32` rozmiaru, który odbiera w znaki buforu, muszą zawierać nazw plików.</span><span class="sxs-lookup"><span data-stu-id="b42f9-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="b42f9-109">[out] Buforu, który zawiera nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="b42f9-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b42f9-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b42f9-110">Return Value</span></span>  
 <span data-ttu-id="b42f9-111">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="b42f9-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b42f9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b42f9-112">Requirements</span></span>  
 <span data-ttu-id="b42f9-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b42f9-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b42f9-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b42f9-114">See Also</span></span>  
 [<span data-ttu-id="b42f9-115">ISymENCUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="b42f9-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

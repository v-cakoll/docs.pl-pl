---
title: "ISymENCUnmanagedMethod::GetFileNameFromOffset — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9dcdbf7813c7ce3d451a27c0abf08c661a8f17b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="fe39e-102">ISymENCUnmanagedMethod::GetFileNameFromOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="fe39e-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="fe39e-103">Pobiera nazwę pliku dla wiersz skojarzony z przesunięciem.</span><span class="sxs-lookup"><span data-stu-id="fe39e-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe39e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe39e-104">Syntax</span></span>  
  
```  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe39e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe39e-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="fe39e-106">[in] A `ULONG32` zawiera przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="fe39e-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="fe39e-107">[in] A `ULONG32` wskazuje, że rozmiar `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="fe39e-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="fe39e-108">[out] Wskaźnik do `ULONG32` rozmiaru, który odbiera w znaki buforu, muszą zawierać nazw plików.</span><span class="sxs-lookup"><span data-stu-id="fe39e-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="fe39e-109">[out] Buforu, który zawiera nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="fe39e-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe39e-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fe39e-110">Return Value</span></span>  
 <span data-ttu-id="fe39e-111">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="fe39e-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe39e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe39e-112">Requirements</span></span>  
 <span data-ttu-id="fe39e-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fe39e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe39e-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe39e-114">See Also</span></span>  
 [<span data-ttu-id="fe39e-115">ISymENCUnmanagedMethod — interfejs</span><span class="sxs-lookup"><span data-stu-id="fe39e-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

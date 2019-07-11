---
title: ISymENCUnmanagedMethod::GetFileNameFromOffset — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 80bfdc9d58a86bb4cf945f0c8106bcfc00f3743e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760315"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="d20f3-102">ISymENCUnmanagedMethod::GetFileNameFromOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="d20f3-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>
<span data-ttu-id="d20f3-103">Pobiera nazwę pliku dla linii skojarzonych z przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="d20f3-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d20f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d20f3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d20f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d20f3-105">Parameters</span></span>  
 `dwOffset`  
 <span data-ttu-id="d20f3-106">[in] Element `ULONG32` zawiera przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="d20f3-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="d20f3-107">[in] A `ULONG32` oznacza rozmiar `szName` buforu.</span><span class="sxs-lookup"><span data-stu-id="d20f3-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d20f3-108">[out] Wskaźnik do `ULONG32` rozmiar, który odbiera w postaci, buforu, muszą zawierać nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="d20f3-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="d20f3-109">[out] Bufor, który zawiera nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="d20f3-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d20f3-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="d20f3-110">Return Value</span></span>  
 <span data-ttu-id="d20f3-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="d20f3-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d20f3-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d20f3-112">Requirements</span></span>  
 <span data-ttu-id="d20f3-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d20f3-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d20f3-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d20f3-114">See also</span></span>

- [<span data-ttu-id="d20f3-115">ISymENCUnmanagedMethod, interfejs</span><span class="sxs-lookup"><span data-stu-id="d20f3-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

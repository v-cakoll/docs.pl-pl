---
title: ISymUnmanagedScope2::GetConstants — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
ms.openlocfilehash: 45268929b6e9ad6ac6423aa0fa2b7b5022bc9179
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176620"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="436df-102">ISymUnmanagedScope2::GetConstants — Metoda</span><span class="sxs-lookup"><span data-stu-id="436df-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="436df-103">Pobiera stałe lokalne zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="436df-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="436df-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="436df-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="436df-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="436df-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="436df-106">[w] Długość buforu, na `pcConstants` który wskazuje parametr.</span><span class="sxs-lookup"><span data-stu-id="436df-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="436df-107">[na zewnątrz] Wskaźnik do, `ULONG32` który odbiera rozmiar, w znakach, buforu wymagane do zawierają stałe.</span><span class="sxs-lookup"><span data-stu-id="436df-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="436df-108">[na zewnątrz] Bufor, który przechowuje stałe.</span><span class="sxs-lookup"><span data-stu-id="436df-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="436df-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="436df-109">Return Value</span></span>  
 <span data-ttu-id="436df-110">S_OK, jeśli metoda powiedzie się; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="436df-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="436df-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="436df-111">Requirements</span></span>  
 <span data-ttu-id="436df-112">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="436df-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="436df-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="436df-113">See also</span></span>

- [<span data-ttu-id="436df-114">ISymUnmanagedScope2, interfejs</span><span class="sxs-lookup"><span data-stu-id="436df-114">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)

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
ms.openlocfilehash: f558d209d13fae93bd3a6f5e0e653afb91371a6a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615335"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="3fc05-102">ISymUnmanagedScope2::GetConstants — Metoda</span><span class="sxs-lookup"><span data-stu-id="3fc05-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="3fc05-103">Pobiera stałe lokalne zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="3fc05-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fc05-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3fc05-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fc05-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3fc05-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="3fc05-106">podczas Długość buforu, `pcConstants` do którego wskazuje parametr.</span><span class="sxs-lookup"><span data-stu-id="3fc05-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="3fc05-107">określoną Wskaźnik do obiektu, `ULONG32` który odbiera rozmiar (w znakach) bufora, który musi zawierać stałe.</span><span class="sxs-lookup"><span data-stu-id="3fc05-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="3fc05-108">określoną Bufor przechowujący stałe.</span><span class="sxs-lookup"><span data-stu-id="3fc05-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fc05-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3fc05-109">Return Value</span></span>  
 <span data-ttu-id="3fc05-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="3fc05-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fc05-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3fc05-111">Requirements</span></span>  
 <span data-ttu-id="3fc05-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3fc05-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fc05-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3fc05-113">See also</span></span>

- [<span data-ttu-id="3fc05-114">ISymUnmanagedScope2, interfejs</span><span class="sxs-lookup"><span data-stu-id="3fc05-114">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)

---
title: ISymUnmanagedScope2::GetConstantCount — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstantCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type:
- apiref
ms.openlocfilehash: 88fc6b7d6076bca42050ca87533062557e6a7b50
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610954"
---
# <a name="isymunmanagedscope2getconstantcount-method"></a><span data-ttu-id="49d62-102">ISymUnmanagedScope2::GetConstantCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="49d62-102">ISymUnmanagedScope2::GetConstantCount Method</span></span>
<span data-ttu-id="49d62-103">Pobiera liczbę stałych zdefiniowanych w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="49d62-103">Gets a count of the constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49d62-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49d62-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49d62-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="49d62-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="49d62-106">określoną Wskaźnik do obiektu, `ULONG32` który odbiera rozmiar (w znakach) bufora, który musi zawierać stałe.</span><span class="sxs-lookup"><span data-stu-id="49d62-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49d62-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="49d62-107">Return Value</span></span>  
 <span data-ttu-id="49d62-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="49d62-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49d62-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="49d62-109">Requirements</span></span>  
 <span data-ttu-id="49d62-110">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="49d62-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49d62-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49d62-111">See also</span></span>

- [<span data-ttu-id="49d62-112">ISymUnmanagedScope2, interfejs</span><span class="sxs-lookup"><span data-stu-id="49d62-112">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)

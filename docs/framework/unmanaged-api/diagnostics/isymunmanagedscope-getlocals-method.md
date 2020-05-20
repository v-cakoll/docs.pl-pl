---
title: ISymUnmanagedScope::GetLocals — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocals
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocals
helpviewer_keywords:
- GetLocals method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocals method [.NET Framework debugging]
ms.assetid: 17c45f15-8c44-44da-b070-f902077b36e4
topic_type:
- apiref
ms.openlocfilehash: 0acd31d85504688427cace0222a657885035c537
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615387"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="bd91a-102">ISymUnmanagedScope::GetLocals — Metoda</span><span class="sxs-lookup"><span data-stu-id="bd91a-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="bd91a-103">Pobiera zmienne lokalne zdefiniowane w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="bd91a-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd91a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bd91a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd91a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bd91a-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="bd91a-106">podczas `ULONG32`Wskazuje rozmiar `locals` tablicy.</span><span class="sxs-lookup"><span data-stu-id="bd91a-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="bd91a-107">określoną Wskaźnik do obiektu `ULONG32` , który odbiera rozmiar buforu wymaganego do przechowywania zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="bd91a-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="bd91a-108">określoną Tablica, która odbiera zmienne lokalne.</span><span class="sxs-lookup"><span data-stu-id="bd91a-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd91a-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bd91a-109">Return Value</span></span>  
 <span data-ttu-id="bd91a-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="bd91a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd91a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd91a-111">Requirements</span></span>  
 <span data-ttu-id="bd91a-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="bd91a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd91a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd91a-113">See also</span></span>

- [<span data-ttu-id="bd91a-114">ISymUnmanagedScope — Interfejs</span><span class="sxs-lookup"><span data-stu-id="bd91a-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)

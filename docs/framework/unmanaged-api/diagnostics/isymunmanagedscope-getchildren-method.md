---
title: ISymUnmanagedScope::GetChildren — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetChildren
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type:
- apiref
ms.openlocfilehash: c6d21f40c260890c9c88dcdfccd7e31161024ba3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614867"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="94ccd-102">ISymUnmanagedScope::GetChildren — Metoda</span><span class="sxs-lookup"><span data-stu-id="94ccd-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="94ccd-103">Pobiera elementy podrzędne tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="94ccd-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94ccd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="94ccd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94ccd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="94ccd-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="94ccd-106">podczas `ULONG32`Wskazuje rozmiar `children` tablicy.</span><span class="sxs-lookup"><span data-stu-id="94ccd-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="94ccd-107">określoną Wskaźnik do obiektu `ULONG32` , który odbiera rozmiar buforu wymaganego do zawierania elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="94ccd-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="94ccd-108">określoną Zwracana tablica elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="94ccd-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94ccd-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="94ccd-109">Return Value</span></span>  
 <span data-ttu-id="94ccd-110">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="94ccd-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94ccd-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="94ccd-111">Requirements</span></span>  
 <span data-ttu-id="94ccd-112">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="94ccd-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94ccd-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94ccd-113">See also</span></span>

- [<span data-ttu-id="94ccd-114">ISymUnmanagedScope — Interfejs</span><span class="sxs-lookup"><span data-stu-id="94ccd-114">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="94ccd-115">GetParent, metoda</span><span class="sxs-lookup"><span data-stu-id="94ccd-115">GetParent Method</span></span>](isymunmanagedscope-getparent-method.md)

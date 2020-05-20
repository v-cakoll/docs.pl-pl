---
title: ISymUnmanagedScope::GetLocalCount — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocalCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type:
- apiref
ms.openlocfilehash: 9ffba23e3821c48c9b0708e4b6b617db4ddc5959
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83611266"
---
# <a name="isymunmanagedscopegetlocalcount-method"></a><span data-ttu-id="e0c71-102">ISymUnmanagedScope::GetLocalCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="e0c71-102">ISymUnmanagedScope::GetLocalCount Method</span></span>
<span data-ttu-id="e0c71-103">Pobiera liczbę zmiennych lokalnych zdefiniowanych w tym zakresie.</span><span class="sxs-lookup"><span data-stu-id="e0c71-103">Gets a count of the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0c71-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0c71-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0c71-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0c71-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="e0c71-106">określoną Wskaźnik do obiektu `ULONG32` , który otrzymuje liczbę zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="e0c71-106">[out] A pointer to a `ULONG32` that receives the count of local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0c71-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e0c71-107">Return Value</span></span>  
 <span data-ttu-id="e0c71-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="e0c71-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0c71-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0c71-109">Requirements</span></span>  
 <span data-ttu-id="e0c71-110">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e0c71-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0c71-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0c71-111">See also</span></span>

- [<span data-ttu-id="e0c71-112">ISymUnmanagedScope — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e0c71-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)

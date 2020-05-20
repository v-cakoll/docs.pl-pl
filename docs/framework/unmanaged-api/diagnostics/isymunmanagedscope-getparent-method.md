---
title: ISymUnmanagedScope::GetParent — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetParent
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetParent
helpviewer_keywords:
- GetParent method [.NET Framework debugging]
- ISymUnmanagedScope::GetParent method [.NET Framework debugging]
ms.assetid: c7963c87-6ec5-49b3-a5cd-e0fe0c43f9b4
topic_type:
- apiref
ms.openlocfilehash: 95ae081d61200e4fd020609a4d23783f265d2cc6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615361"
---
# <a name="isymunmanagedscopegetparent-method"></a><span data-ttu-id="efc8f-102">ISymUnmanagedScope::GetParent — Metoda</span><span class="sxs-lookup"><span data-stu-id="efc8f-102">ISymUnmanagedScope::GetParent Method</span></span>
<span data-ttu-id="efc8f-103">Pobiera zakres nadrzędny tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="efc8f-103">Gets the parent scope of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efc8f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="efc8f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParent(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efc8f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="efc8f-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="efc8f-106">określoną Wskaźnik do zwracanego interfejsu [ISymUnmanagedScope](isymunmanagedscope-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="efc8f-106">[out] A pointer to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="efc8f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="efc8f-107">Return Value</span></span>  
 <span data-ttu-id="efc8f-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="efc8f-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efc8f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="efc8f-109">Requirements</span></span>  
 <span data-ttu-id="efc8f-110">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="efc8f-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efc8f-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efc8f-111">See also</span></span>

- [<span data-ttu-id="efc8f-112">ISymUnmanagedScope — Interfejs</span><span class="sxs-lookup"><span data-stu-id="efc8f-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="efc8f-113">GetChildren, metoda</span><span class="sxs-lookup"><span data-stu-id="efc8f-113">GetChildren Method</span></span>](isymunmanagedscope-getchildren-method.md)

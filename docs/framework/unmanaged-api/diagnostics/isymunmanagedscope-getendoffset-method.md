---
title: ISymUnmanagedScope::GetEndOffset — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetEndOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetEndOffset
helpviewer_keywords:
- ISymUnmanagedScope::GetEndOffset method [.NET Framework debugging]
- GetEndOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 1d0b15c9-8059-435f-9fce-346a08b9bd36
topic_type:
- apiref
ms.openlocfilehash: 4d6bd239a15bd196f840007af120cb062499f4c9
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614854"
---
# <a name="isymunmanagedscopegetendoffset-method"></a><span data-ttu-id="0ba8d-102">ISymUnmanagedScope::GetEndOffset — Metoda</span><span class="sxs-lookup"><span data-stu-id="0ba8d-102">ISymUnmanagedScope::GetEndOffset Method</span></span>
<span data-ttu-id="0ba8d-103">Pobiera przesunięcie końca dla tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="0ba8d-103">Gets the end offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ba8d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0ba8d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEndOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ba8d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ba8d-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="0ba8d-106">określoną Wskaźnik do elementu `ULONG32` , który odbiera przesunięcie końcowe.</span><span class="sxs-lookup"><span data-stu-id="0ba8d-106">[out] A pointer to a `ULONG32` that receives the end offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ba8d-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0ba8d-107">Return Value</span></span>  
 <span data-ttu-id="0ba8d-108">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="0ba8d-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ba8d-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0ba8d-109">Requirements</span></span>  
 <span data-ttu-id="0ba8d-110">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0ba8d-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ba8d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ba8d-111">See also</span></span>

- [<span data-ttu-id="0ba8d-112">ISymUnmanagedScope — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0ba8d-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="0ba8d-113">GetStartOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="0ba8d-113">GetStartOffset Method</span></span>](isymunmanagedscope-getstartoffset-method.md)

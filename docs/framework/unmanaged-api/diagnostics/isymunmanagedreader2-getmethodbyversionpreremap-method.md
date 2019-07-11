---
title: ISymUnmanagedReader2::GetMethodByVersionPreRemap — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetMethodByVersionPreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetMethodByVersionPreRemap
helpviewer_keywords:
- GetMethodByVersionPreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetMethodByVersionPreRemap method [.NET Framework debugging]
ms.assetid: 0d144ed4-bdb0-4cac-960c-cb90f4dca173
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 06b8ebf26794baa1d957cc47d1179283611b62d5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736683"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="03a16-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap — Metoda</span><span class="sxs-lookup"><span data-stu-id="03a16-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="03a16-103">Pobiera metodę czytnika symboli, biorąc pod uwagę token metody oraz numer wersji edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="03a16-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="03a16-104">Numery wersji są liczone od 1 i jest zwiększana za każdym razem, gdy metoda zmienia się w wyniku operacji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="03a16-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03a16-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="03a16-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03a16-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="03a16-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="03a16-107">[in] Metoda token metadanych.</span><span class="sxs-lookup"><span data-stu-id="03a16-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="03a16-108">[in] Wersja metody.</span><span class="sxs-lookup"><span data-stu-id="03a16-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="03a16-109">[out] Wskaźnik do zwracanego [isymunmanagedmethod —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="03a16-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03a16-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="03a16-110">Return Value</span></span>  
 <span data-ttu-id="03a16-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="03a16-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03a16-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03a16-112">Requirements</span></span>  
 <span data-ttu-id="03a16-113">**Nagłówek:** CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="03a16-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="03a16-114">CorSym.h</span><span class="sxs-lookup"><span data-stu-id="03a16-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a16-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03a16-115">See also</span></span>

- [<span data-ttu-id="03a16-116">ISymUnmanagedReader2, interfejs</span><span class="sxs-lookup"><span data-stu-id="03a16-116">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)

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
ms.openlocfilehash: bcd200b7fa431f193dd202c3c2a690aa22ec8e32
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135190"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="16570-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap — Metoda</span><span class="sxs-lookup"><span data-stu-id="16570-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="16570-103">Pobiera metodę czytnika symboli, biorąc pod uwagę token metody oraz numer wersji edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="16570-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="16570-104">Numery wersji są liczone od 1 i jest zwiększana za każdym razem, gdy metoda zmienia się w wyniku operacji Edytuj i Kontynuuj.</span><span class="sxs-lookup"><span data-stu-id="16570-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16570-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="16570-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16570-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="16570-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="16570-107">[in] Metoda token metadanych.</span><span class="sxs-lookup"><span data-stu-id="16570-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="16570-108">[in] Wersja metody.</span><span class="sxs-lookup"><span data-stu-id="16570-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="16570-109">[out] Wskaźnik do zwracanego [isymunmanagedmethod —](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="16570-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16570-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="16570-110">Return Value</span></span>  
 <span data-ttu-id="16570-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="16570-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16570-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16570-112">Requirements</span></span>  
 <span data-ttu-id="16570-113">**Nagłówek:** CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="16570-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="16570-114">CorSym.h</span><span class="sxs-lookup"><span data-stu-id="16570-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16570-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="16570-115">See also</span></span>

- [<span data-ttu-id="16570-116">ISymUnmanagedReader2, interfejs</span><span class="sxs-lookup"><span data-stu-id="16570-116">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)

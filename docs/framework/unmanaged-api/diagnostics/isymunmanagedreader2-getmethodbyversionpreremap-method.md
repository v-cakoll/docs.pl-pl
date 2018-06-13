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
ms.openlocfilehash: efa34d262157faed2e05cd6e7517c259cd279146
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428579"
---
# <a name="isymunmanagedreader2getmethodbyversionpreremap-method"></a><span data-ttu-id="c45b3-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap — Metoda</span><span class="sxs-lookup"><span data-stu-id="c45b3-102">ISymUnmanagedReader2::GetMethodByVersionPreRemap Method</span></span>
<span data-ttu-id="c45b3-103">Pobiera metodę czytnika symboli podany token metody i numer wersji edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="c45b3-103">Gets a symbol reader method, given a method token and an edit-and-continue version number.</span></span> <span data-ttu-id="c45b3-104">Numery wersji są liczone od 1 i są zwiększany po każdej zmianie metody wyniku operacji edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="c45b3-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-continue operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c45b3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c45b3-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersionPreRemap(  
    [in]  mdMethodDef token,  
    [in]  int version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c45b3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c45b3-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="c45b3-107">[in] Metoda token metadanych.</span><span class="sxs-lookup"><span data-stu-id="c45b3-107">[in] The method metadata token.</span></span>  
  
 `version`  
 <span data-ttu-id="c45b3-108">[in] Wersja metody.</span><span class="sxs-lookup"><span data-stu-id="c45b3-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="c45b3-109">[out] Wskaźnik do zwróconego [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c45b3-109">[out] A pointer to the returned [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c45b3-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c45b3-110">Return Value</span></span>  
 <span data-ttu-id="c45b3-111">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="c45b3-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c45b3-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c45b3-112">Requirements</span></span>  
 <span data-ttu-id="c45b3-113">**Nagłówek:** CorSym.idl.</span><span class="sxs-lookup"><span data-stu-id="c45b3-113">**Header:** CorSym.idl.</span></span> <span data-ttu-id="c45b3-114">CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c45b3-114">CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c45b3-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c45b3-115">See Also</span></span>  
 [<span data-ttu-id="c45b3-116">ISymUnmanagedReader2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c45b3-116">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)

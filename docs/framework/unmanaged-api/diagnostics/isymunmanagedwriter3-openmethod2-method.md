---
title: ISymUnmanagedWriter3::OpenMethod2 — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 643666df9f93d1aa5e09579359ae0db87908f10b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428336"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a><span data-ttu-id="25e49-102">ISymUnmanagedWriter3::OpenMethod2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="25e49-102">ISymUnmanagedWriter3::OpenMethod2 Method</span></span>
<span data-ttu-id="25e49-103">Otwiera metody i zapewnia jego przesunięcie rzeczywistych sekcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="25e49-103">Opens a method and provides its real section offset in the image.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25e49-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25e49-104">Syntax</span></span>  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25e49-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25e49-105">Parameters</span></span>  
 `method`  
 <span data-ttu-id="25e49-106">[in] Token metadanych metody, która ma zostać otwarty.</span><span class="sxs-lookup"><span data-stu-id="25e49-106">[in] The metadata token for the method to be opened.</span></span>  
  
 `isect`  
 <span data-ttu-id="25e49-107">[in] Przesunięcie sekcji w obrazie.</span><span class="sxs-lookup"><span data-stu-id="25e49-107">[in] The section offset in the image.</span></span>  
  
 `offset`  
 <span data-ttu-id="25e49-108">[in] Przesunięcie w obrazie.</span><span class="sxs-lookup"><span data-stu-id="25e49-108">[in] The offset in the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="25e49-109">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="25e49-109">Return Value</span></span>  
 <span data-ttu-id="25e49-110">Wartość S_OK, jeśli metoda zakończy się pomyślnie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="25e49-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25e49-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25e49-111">Requirements</span></span>  
 <span data-ttu-id="25e49-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="25e49-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25e49-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25e49-113">See Also</span></span>  
 [<span data-ttu-id="25e49-114">ISymUnmanagedWriter3, interfejs</span><span class="sxs-lookup"><span data-stu-id="25e49-114">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 [<span data-ttu-id="25e49-115">OpenMethod, metoda</span><span class="sxs-lookup"><span data-stu-id="25e49-115">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)

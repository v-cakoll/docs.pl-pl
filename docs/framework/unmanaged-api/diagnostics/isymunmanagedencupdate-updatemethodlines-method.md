---
title: ISymUnmanagedENCUpdate::UpdateMethodLines — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateMethodLines
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateMethodLines
helpviewer_keywords:
- UpdateMethodLines method [.NET Framework debugging]
- ISymUnmanagedENCUpdate::UpdateMethodLines method [.NET Framework debugging]
ms.assetid: 275ef87b-0b53-49f9-af6b-58506335dc06
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bd1f101e2e9cf9baeb28290c7607ccab3d8d7440
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939688"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="38579-102">ISymUnmanagedENCUpdate::UpdateMethodLines — Metoda</span><span class="sxs-lookup"><span data-stu-id="38579-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="38579-103">Zezwala na aktualizowanie informacji o wierszu dla metody, która nie zwrócenie, ale których wiersze zostały przeniesione niezależnie.</span><span class="sxs-lookup"><span data-stu-id="38579-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="38579-104">Delta dla każdej instrukcji jest dozwolona.</span><span class="sxs-lookup"><span data-stu-id="38579-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38579-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="38579-105">Syntax</span></span>  
  
```  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38579-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="38579-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="38579-107">[in] Metadane token metody.</span><span class="sxs-lookup"><span data-stu-id="38579-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="38579-108">[in] Tablica `INT32` wartości wskazujących różnic dla każdego punktu sekwencji w metodzie.</span><span class="sxs-lookup"><span data-stu-id="38579-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="38579-109">[in] A `ULONG` zawierający rozmiar `pDeltas` parametru.</span><span class="sxs-lookup"><span data-stu-id="38579-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38579-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="38579-110">Return Value</span></span>  
 <span data-ttu-id="38579-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.</span><span class="sxs-lookup"><span data-stu-id="38579-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38579-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38579-112">Requirements</span></span>  
 <span data-ttu-id="38579-113">**Nagłówek:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="38579-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38579-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38579-114">See also</span></span>

- [<span data-ttu-id="38579-115">ISymUnmanagedENCUpdate, interfejs</span><span class="sxs-lookup"><span data-stu-id="38579-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

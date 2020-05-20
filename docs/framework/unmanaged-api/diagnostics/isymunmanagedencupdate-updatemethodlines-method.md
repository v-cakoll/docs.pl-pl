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
ms.openlocfilehash: 9a490299c24f44b59da682f714f4b696fde3cba5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614516"
---
# <a name="isymunmanagedencupdateupdatemethodlines-method"></a><span data-ttu-id="1d4b6-102">ISymUnmanagedENCUpdate::UpdateMethodLines — Metoda</span><span class="sxs-lookup"><span data-stu-id="1d4b6-102">ISymUnmanagedENCUpdate::UpdateMethodLines Method</span></span>
<span data-ttu-id="1d4b6-103">Umożliwia aktualizowanie informacji o wierszu dla metody, która nie została ponownie skompilowana, ale których linie nie zostały przesunięte niezależnie.</span><span class="sxs-lookup"><span data-stu-id="1d4b6-103">Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently.</span></span> <span data-ttu-id="1d4b6-104">Różnicowa dla każdej instrukcji jest dozwolony.</span><span class="sxs-lookup"><span data-stu-id="1d4b6-104">A delta for each statement is allowed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d4b6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d4b6-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateMethodLines(  
    [in]  mdMethodDef  mdMethodToken,  
    [in, size_is(cDeltas)] INT32*  pDeltas,  
    [in]  ULONG        cDeltas);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d4b6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d4b6-106">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="1d4b6-107">podczas Metadane tokenu metody.</span><span class="sxs-lookup"><span data-stu-id="1d4b6-107">[in] The metadata of the method token.</span></span>  
  
 `pDeltas`  
 <span data-ttu-id="1d4b6-108">podczas Tablica `INT32` wartości, która wskazuje różnice dla każdego punktu sekwencji w metodzie.</span><span class="sxs-lookup"><span data-stu-id="1d4b6-108">[in] An array of `INT32` values that indicates deltas for each sequence point in the method.</span></span>  
  
 `cDeltas`  
 <span data-ttu-id="1d4b6-109">podczas `ULONG`Zawierający rozmiar `pDeltas` parametru.</span><span class="sxs-lookup"><span data-stu-id="1d4b6-109">[in] A `ULONG` containing the size of the `pDeltas` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d4b6-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1d4b6-110">Return Value</span></span>  
 <span data-ttu-id="1d4b6-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="1d4b6-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d4b6-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1d4b6-112">Requirements</span></span>  
 <span data-ttu-id="1d4b6-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1d4b6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d4b6-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d4b6-114">See also</span></span>

- [<span data-ttu-id="1d4b6-115">ISymUnmanagedENCUpdate, interfejs</span><span class="sxs-lookup"><span data-stu-id="1d4b6-115">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)

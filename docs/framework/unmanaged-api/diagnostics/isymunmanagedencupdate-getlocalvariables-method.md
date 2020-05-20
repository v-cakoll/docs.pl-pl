---
title: ISymUnmanagedENCUpdate::GetLocalVariables — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
ms.openlocfilehash: 5e5bf097a4b1e366fff807595b22c4696a91cf43
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614555"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="a4dd7-102">ISymUnmanagedENCUpdate::GetLocalVariables — Metoda</span><span class="sxs-lookup"><span data-stu-id="a4dd7-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>
<span data-ttu-id="a4dd7-103">Pobiera zmienne lokalne.</span><span class="sxs-lookup"><span data-stu-id="a4dd7-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4dd7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4dd7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4dd7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4dd7-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="a4dd7-106">podczas Token metadanych metody.</span><span class="sxs-lookup"><span data-stu-id="a4dd7-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="a4dd7-107">podczas `ULONG`Wskazuje rozmiar `rgLocals` parametru.</span><span class="sxs-lookup"><span data-stu-id="a4dd7-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="a4dd7-108">określoną Zwrócona tablica wystąpień [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a4dd7-108">[out] The returned array of [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="a4dd7-109">określoną Wskaźnik do obiektu `ULONG` , który odbiera rozmiar `rgLocals` buforu wymaganego do przechowywania wartości lokalnych.</span><span class="sxs-lookup"><span data-stu-id="a4dd7-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4dd7-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a4dd7-110">Return Value</span></span>  
 <span data-ttu-id="a4dd7-111">S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.</span><span class="sxs-lookup"><span data-stu-id="a4dd7-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4dd7-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a4dd7-112">Requirements</span></span>  
 <span data-ttu-id="a4dd7-113">**Nagłówek:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a4dd7-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4dd7-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4dd7-114">See also</span></span>

- [<span data-ttu-id="a4dd7-115">ISymUnmanagedENCUpdate, interfejs</span><span class="sxs-lookup"><span data-stu-id="a4dd7-115">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)

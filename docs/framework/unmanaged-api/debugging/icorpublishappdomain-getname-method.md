---
title: ICorPublishAppDomain::GetName — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4afbc41e680d8a20166095aeb1afbc0de9bbacbc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631770"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="fee17-102">ICorPublishAppDomain::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="fee17-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="fee17-103">Pobiera nazwę domeny aplikacji, który jest reprezentowany przez ten [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="fee17-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fee17-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fee17-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fee17-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fee17-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="fee17-106">[in] Rozmiar `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="fee17-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="fee17-107">[out] Wskaźnik do liczby znaków dwubajtowych znakiem zerowym, zwracane w tym `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="fee17-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="fee17-108">[out] Tablica do przechowywania nazwy.</span><span class="sxs-lookup"><span data-stu-id="fee17-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fee17-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fee17-109">Remarks</span></span>  
 <span data-ttu-id="fee17-110">Jeśli `szName` jest różna od null, `GetName` metoda kopiuje do `cchName` znaków (łącznie z terminatorem null) do `szName`.</span><span class="sxs-lookup"><span data-stu-id="fee17-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="fee17-111">Jeśli zwracana jest inna niż null w `pcchName`, rzeczywista liczba znaków w nazwie (łącznie z terminatorem null) są przechowywane w `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="fee17-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="fee17-112">`GetName` Metoda zwróci wartość HRESULT S_OK, niezależnie od tego, ile znaków zostały skopiowane.</span><span class="sxs-lookup"><span data-stu-id="fee17-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fee17-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fee17-113">Requirements</span></span>  
 <span data-ttu-id="fee17-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fee17-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fee17-115">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="fee17-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="fee17-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fee17-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fee17-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fee17-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee17-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fee17-118">See also</span></span>
- [<span data-ttu-id="fee17-119">ICorPublishAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="fee17-119">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)

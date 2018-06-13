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
ms.openlocfilehash: 796f8ea42cc5cbe13729f7b92e15bc214d62734d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423861"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="be663-102">ICorPublishAppDomain::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="be663-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="be663-103">Pobiera nazwę domeny aplikacji, która jest reprezentowana przez to [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="be663-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be663-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be663-104">Syntax</span></span>  
  
```  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be663-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be663-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="be663-106">[in] Rozmiar `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="be663-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="be663-107">[out] Wskaźnik do liczby znaki dwubajtowe, w tym znakiem null zwracane w `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="be663-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="be663-108">[out] Tablica do przechowywania nazwy.</span><span class="sxs-lookup"><span data-stu-id="be663-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be663-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be663-109">Remarks</span></span>  
 <span data-ttu-id="be663-110">Jeśli `szName` jest różna od null, `GetName` metoda kopiuje do `cchName` znaków (włącznie z terminatorem null) do `szName`.</span><span class="sxs-lookup"><span data-stu-id="be663-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="be663-111">Jeśli inne niż null, jest zwracany w `pcchName`, rzeczywista liczba znaków w polu Nazwa (włącznie z terminatorem null) są przechowywane w `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="be663-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="be663-112">`GetName` Metoda zwróci wartość HRESULT S_OK niezależnie od tego, ile znaków zostały skopiowane.</span><span class="sxs-lookup"><span data-stu-id="be663-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be663-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be663-113">Requirements</span></span>  
 <span data-ttu-id="be663-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be663-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be663-115">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="be663-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="be663-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be663-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be663-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be663-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be663-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be663-118">See Also</span></span>  
 [<span data-ttu-id="be663-119">ICorPublishAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="be663-119">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)

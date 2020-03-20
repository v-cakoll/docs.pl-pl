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
ms.openlocfilehash: 762c637696fdf79ccab6702918b5bf962ea55903
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178406"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="055d4-102">ICorPublishAppDomain::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="055d4-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="055d4-103">Pobiera nazwę domeny aplikacji, która jest reprezentowana przez ten [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="055d4-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="055d4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="055d4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="055d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="055d4-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="055d4-106">[w] Rozmiar tablicy. `szName`</span><span class="sxs-lookup"><span data-stu-id="055d4-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="055d4-107">[na zewnątrz] Wskaźnik do liczby znaków szerokich, w tym znaku `szName` null, zwrócony w tablicy.</span><span class="sxs-lookup"><span data-stu-id="055d4-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="055d4-108">[na zewnątrz] Tablica, w której ma być przechowywana nazwa.</span><span class="sxs-lookup"><span data-stu-id="055d4-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="055d4-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="055d4-109">Remarks</span></span>  
 <span data-ttu-id="055d4-110">Jeśli `szName` metoda nie jest `GetName` null, metoda `cchName` kopiuje do znaków `szName`(w tym zerowy terminator) do .</span><span class="sxs-lookup"><span data-stu-id="055d4-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="055d4-111">Jeśli w `pcchName`tablicy jest zwracana wartość null, rzeczywista liczba znaków w nazwie `szName` (w tym terminator zerowy) jest przechowywana w tablicy.</span><span class="sxs-lookup"><span data-stu-id="055d4-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="055d4-112">Metoda `GetName` zwraca S_OK HRESULT niezależnie od liczby znaków zostały skopiowane.</span><span class="sxs-lookup"><span data-stu-id="055d4-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="055d4-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="055d4-113">Requirements</span></span>  
 <span data-ttu-id="055d4-114">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="055d4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="055d4-115">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="055d4-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="055d4-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="055d4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="055d4-117">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="055d4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="055d4-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="055d4-118">See also</span></span>

- [<span data-ttu-id="055d4-119">ICorPublishAppDomain, interfejs</span><span class="sxs-lookup"><span data-stu-id="055d4-119">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)

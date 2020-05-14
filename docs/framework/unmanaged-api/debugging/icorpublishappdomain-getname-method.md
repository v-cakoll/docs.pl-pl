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
ms.openlocfilehash: e95f96847c6e069758362fb6febc28dc31911bc9
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396298"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="2644d-102">ICorPublishAppDomain::GetName — Metoda</span><span class="sxs-lookup"><span data-stu-id="2644d-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="2644d-103">Pobiera nazwę domeny aplikacji reprezentowanej przez ten [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="2644d-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2644d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2644d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2644d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2644d-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="2644d-106">podczas Rozmiar `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="2644d-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="2644d-107">określoną Wskaźnik do liczby znaków dwubajtowych, w tym znak null, zwracany w `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="2644d-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="2644d-108">określoną Tablica, w której ma zostać przechowana nazwa.</span><span class="sxs-lookup"><span data-stu-id="2644d-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2644d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2644d-109">Remarks</span></span>  
 <span data-ttu-id="2644d-110">Jeśli `szName` jest inna niż null, `GetName` Metoda kopiuje do. do `cchName` znaków (w tym terminator wartości null) `szName` .</span><span class="sxs-lookup"><span data-stu-id="2644d-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="2644d-111">Jeśli zwracana jest wartość inna niż null `pcchName` , rzeczywista liczba znaków w nazwie (łącznie z terminatorem wartości null) jest przechowywana w `szName` tablicy.</span><span class="sxs-lookup"><span data-stu-id="2644d-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="2644d-112">`GetName`Metoda zwraca S_OK HRESULT, niezależnie od liczby skopiowanych znaków.</span><span class="sxs-lookup"><span data-stu-id="2644d-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2644d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2644d-113">Requirements</span></span>  
 <span data-ttu-id="2644d-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2644d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2644d-115">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="2644d-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2644d-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2644d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2644d-117">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2644d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2644d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2644d-118">See also</span></span>

- [<span data-ttu-id="2644d-119">ICorPublishAppDomain — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2644d-119">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)

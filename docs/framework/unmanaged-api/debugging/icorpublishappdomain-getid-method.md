---
title: ICorPublishAppDomain::GetID — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type:
- apiref
ms.openlocfilehash: 36c5c674f3cdf867107b9ee85a5befadc9246d78
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396303"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="c5dfa-102">ICorPublishAppDomain::GetID — Metoda</span><span class="sxs-lookup"><span data-stu-id="c5dfa-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="c5dfa-103">Pobiera unikatowy identyfikator dla tego [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c5dfa-103">Gets the unique identifier for this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5dfa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c5dfa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5dfa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5dfa-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="c5dfa-106">określoną Wskaźnik do identyfikatora domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c5dfa-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5dfa-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c5dfa-107">Remarks</span></span>  
 <span data-ttu-id="c5dfa-108">Identyfikator jest unikatowy tylko w zakresie procesu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="c5dfa-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5dfa-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c5dfa-109">Requirements</span></span>  
 <span data-ttu-id="c5dfa-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5dfa-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5dfa-111">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="c5dfa-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c5dfa-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c5dfa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5dfa-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5dfa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5dfa-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5dfa-114">See also</span></span>

- [<span data-ttu-id="c5dfa-115">ICorPublishAppDomain — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c5dfa-115">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)

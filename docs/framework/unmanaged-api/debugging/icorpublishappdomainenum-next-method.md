---
title: ICorPublishAppDomainEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomainEnum::Next
helpviewer_keywords:
- Next method, ICorPublishAppDomainEnum interface [.NET Framework debugging]
- ICorPublishAppDomainEnum::Next method [.NET Framework debugging]
ms.assetid: ad37cd10-0339-4d08-9b0e-4b3428bb4dc3
topic_type:
- apiref
ms.openlocfilehash: c8866e98be0dd064138acdf5e0f6fb9c339fb3d2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790647"
---
# <a name="icorpublishappdomainenumnext-method"></a><span data-ttu-id="b4b05-102">ICorPublishAppDomainEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="b4b05-102">ICorPublishAppDomainEnum::Next Method</span></span>
<span data-ttu-id="b4b05-103">Pobiera określoną liczbę domen aplikacji, które aktualnie istnieją w procesie, rozpoczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="b4b05-103">Gets the specified number of application domains that currently exist in the process, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4b05-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4b05-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]   
        ICorPublishAppDomain **objects,  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4b05-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4b05-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="b4b05-106">podczas Liczba elementów, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="b4b05-106">[in] The number of elements to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="b4b05-107">określoną Wskaźnik do tablicy pobranych obiektów [ICorPublishAppDomain](icorpublishappdomain-interface.md) , z których każdy reprezentuje domenę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b4b05-107">[out] A pointer to the array of retrieved [ICorPublishAppDomain](icorpublishappdomain-interface.md) objects, each of which represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="b4b05-108">określoną Wskaźnik na liczbę domen aplikacji, które faktycznie zostały zwrócone.</span><span class="sxs-lookup"><span data-stu-id="b4b05-108">[out] Pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="b4b05-109">Ta wartość może być równa null, jeśli `celt`.</span><span class="sxs-lookup"><span data-stu-id="b4b05-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4b05-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4b05-110">Requirements</span></span>  
 <span data-ttu-id="b4b05-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4b05-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4b05-112">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="b4b05-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b4b05-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b4b05-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4b05-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4b05-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b05-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4b05-115">See also</span></span>

- [<span data-ttu-id="b4b05-116">ICorPublishAppDomainEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b4b05-116">ICorPublishAppDomainEnum Interface</span></span>](icorpublishappdomainenum-interface.md)

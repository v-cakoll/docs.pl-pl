---
title: ICorPublishEnum::GetCount — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type:
- apiref
ms.openlocfilehash: 0b3754fbcca50b52039dc358aed7070b8a152ead
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790639"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="0b584-102">ICorPublishEnum::GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="0b584-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="0b584-103">Pobiera liczbę elementów w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="0b584-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b584-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b584-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b584-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b584-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="0b584-106">określoną Wskaźnik do liczby elementów w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="0b584-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b584-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b584-107">Requirements</span></span>  
 <span data-ttu-id="0b584-108">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b584-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b584-109">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="0b584-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="0b584-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0b584-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b584-111">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b584-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b584-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b584-112">See also</span></span>

- [<span data-ttu-id="0b584-113">ICorPublishEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="0b584-113">ICorPublishEnum Interface</span></span>](icorpublishenum-interface.md)

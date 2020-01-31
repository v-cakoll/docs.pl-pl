---
title: ICorPublishProcess::IsManaged — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
ms.openlocfilehash: 68931ba16ea1f8f61176c6d6ed8300e762b61690
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790525"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="8f2ba-102">ICorPublishProcess::IsManaged — Metoda</span><span class="sxs-lookup"><span data-stu-id="8f2ba-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="8f2ba-103">Pobiera wartość wskazującą, czy proces, do którego odwołuje się ten [ICorPublishProcess](icorpublishprocess-interface.md) , ma znany kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="8f2ba-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f2ba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8f2ba-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f2ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8f2ba-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="8f2ba-106">określoną Wskaźnik do wartości logicznej wskazującej, czy proces ma kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="8f2ba-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="8f2ba-107">Wartość jest `true`, jeśli proces ma kod zarządzany; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="8f2ba-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f2ba-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8f2ba-108">Remarks</span></span>  
 <span data-ttu-id="8f2ba-109">Ponieważ bieżąca wersja `ICorPublishProcess` zezwala na dostęp tylko do procesów, które mają kod zarządzany, `IsManaged` zawsze zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="8f2ba-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f2ba-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f2ba-110">Requirements</span></span>  
 <span data-ttu-id="8f2ba-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f2ba-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f2ba-112">**Nagłówek:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="8f2ba-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="8f2ba-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8f2ba-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f2ba-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f2ba-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f2ba-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f2ba-115">See also</span></span>

- [<span data-ttu-id="8f2ba-116">ICorPublishProcess, interfejs</span><span class="sxs-lookup"><span data-stu-id="8f2ba-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)

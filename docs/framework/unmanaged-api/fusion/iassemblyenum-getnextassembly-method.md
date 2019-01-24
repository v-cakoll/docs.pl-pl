---
title: IAssemblyEnum::GetNextAssembly — Metoda
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 563784dd2fe3881cbf3278992ca2c75a94df1d3f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727563"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="2df13-102">IAssemblyEnum::GetNextAssembly — Metoda</span><span class="sxs-lookup"><span data-stu-id="2df13-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="2df13-103">Pobiera wskaźnik do następnego [iassemblyname —](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) zawarte w tym [iassemblyenum —](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="2df13-103">Gets a pointer to the next [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contained in this [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2df13-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2df13-104">Syntax</span></span>  
  
```  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2df13-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2df13-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="2df13-106">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="2df13-106">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="2df13-107">`pvReserved` musi być odwołanie o wartości null.</span><span class="sxs-lookup"><span data-stu-id="2df13-107">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="2df13-108">[out] Zwrócony `IAssemblyName` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="2df13-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2df13-109">[in] Zarezerwowane dla przyszłej rozszerzalności.</span><span class="sxs-lookup"><span data-stu-id="2df13-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="2df13-110">`dwFlags` musi być równa 0 (zero).</span><span class="sxs-lookup"><span data-stu-id="2df13-110">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2df13-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2df13-111">Requirements</span></span>  
 <span data-ttu-id="2df13-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2df13-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2df13-113">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="2df13-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="2df13-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2df13-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2df13-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2df13-115">See also</span></span>
- [<span data-ttu-id="2df13-116">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="2df13-116">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="2df13-117">IAssemblyEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="2df13-117">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)

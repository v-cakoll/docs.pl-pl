---
title: "ICLRDataTarget::GetMachineType — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetMachineType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetMachineType
helpviewer_keywords:
- ICLRDataTarget::GetMachineType method [.NET Framework debugging]
- GetMachineType method [.NET Framework debugging]
ms.assetid: 5f1f9c61-3e3b-48b2-b111-a4395f7623a7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 56fabfd2bb929e40c60903ad7b5e86e2b18d7d93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="a39fa-102">ICLRDataTarget::GetMachineType — Metoda</span><span class="sxs-lookup"><span data-stu-id="a39fa-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="a39fa-103">Pobiera identyfikator dla rodzaju zestaw instrukcji, który używa procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="a39fa-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a39fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a39fa-104">Syntax</span></span>  
  
```  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a39fa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a39fa-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="a39fa-106">[out] Wskaźnik do wartości, który wskazuje, że instrukcja ustawić proces docelowy korzysta.</span><span class="sxs-lookup"><span data-stu-id="a39fa-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="a39fa-107">Zwrócona `machineType` jest jednym z stałe IMAGE_FILE_MACHINE, które są zdefiniowane w pliku WinNT.h pliku nagłówka.</span><span class="sxs-lookup"><span data-stu-id="a39fa-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a39fa-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a39fa-108">Requirements</span></span>  
 <span data-ttu-id="a39fa-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a39fa-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a39fa-110">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="a39fa-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a39fa-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a39fa-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a39fa-112">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a39fa-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a39fa-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a39fa-113">See Also</span></span>  
 [<span data-ttu-id="a39fa-114">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="a39fa-114">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)

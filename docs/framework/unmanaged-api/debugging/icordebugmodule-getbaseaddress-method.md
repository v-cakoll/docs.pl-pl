---
title: ICorDebugModule::GetBaseAddress — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetBaseAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetBaseAddress
helpviewer_keywords:
- GetBaseAddress method [.NET Framework debugging]
- ICorDebugModule::GetBaseAddress method [.NET Framework debugging]
ms.assetid: 26a82815-1982-4eb7-92d1-5c3d318d5be4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ad6c8bd59f62bc7b0a96e1ef5e545fe15610c91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516983"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="bf125-102">ICorDebugModule::GetBaseAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="bf125-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="bf125-103">Pobiera adres podstawowy moduł.</span><span class="sxs-lookup"><span data-stu-id="bf125-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf125-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf125-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bf125-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bf125-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="bf125-106">[out] A `CORDB_ADDRESS` określający adres podstawowy moduł.</span><span class="sxs-lookup"><span data-stu-id="bf125-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf125-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf125-107">Remarks</span></span>  
 <span data-ttu-id="bf125-108">Jeśli moduł jest natywny obraz (to znaczy, jeśli moduł został wyprodukowany przez generator obrazu natywnego, NGen.exe), jej adres podstawowy będzie mieć wartość zero.</span><span class="sxs-lookup"><span data-stu-id="bf125-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf125-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf125-109">Requirements</span></span>  
 <span data-ttu-id="bf125-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf125-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf125-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf125-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf125-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf125-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf125-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf125-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf125-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf125-114">See also</span></span>



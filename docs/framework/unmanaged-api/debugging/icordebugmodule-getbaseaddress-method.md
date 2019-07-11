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
ms.openlocfilehash: 9ed6344f9a37d246a551699c94046b8c2b473fd8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762692"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="cde80-102">ICorDebugModule::GetBaseAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="cde80-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="cde80-103">Pobiera adres podstawowy moduł.</span><span class="sxs-lookup"><span data-stu-id="cde80-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cde80-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cde80-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cde80-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cde80-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="cde80-106">[out] A `CORDB_ADDRESS` określający adres podstawowy moduł.</span><span class="sxs-lookup"><span data-stu-id="cde80-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cde80-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cde80-107">Remarks</span></span>  
 <span data-ttu-id="cde80-108">Jeśli moduł jest natywny obraz (to znaczy, jeśli moduł został wyprodukowany przez generator obrazu natywnego, NGen.exe), jej adres podstawowy będzie mieć wartość zero.</span><span class="sxs-lookup"><span data-stu-id="cde80-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cde80-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cde80-109">Requirements</span></span>  
 <span data-ttu-id="cde80-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cde80-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cde80-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cde80-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cde80-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cde80-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cde80-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cde80-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cde80-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cde80-114">See also</span></span>

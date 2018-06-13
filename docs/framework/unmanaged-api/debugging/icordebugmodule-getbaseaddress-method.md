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
ms.openlocfilehash: 10e7da7711cd63579589fda416d0d3a4f777eefe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412548"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="c60f9-102">ICorDebugModule::GetBaseAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="c60f9-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="c60f9-103">Pobiera adres podstawowy modułu.</span><span class="sxs-lookup"><span data-stu-id="c60f9-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c60f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c60f9-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c60f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c60f9-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="c60f9-106">[out] A `CORDB_ADDRESS` , który określa adres bazowy modułu.</span><span class="sxs-lookup"><span data-stu-id="c60f9-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c60f9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c60f9-107">Remarks</span></span>  
 <span data-ttu-id="c60f9-108">Jeśli moduł jest natywny obrazu (to znaczy, jeśli moduł został utworzony przez generator obrazu natywnego, NGen.exe), jej adres podstawowy będą miały wartość zero.</span><span class="sxs-lookup"><span data-stu-id="c60f9-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c60f9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c60f9-109">Requirements</span></span>  
 <span data-ttu-id="c60f9-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c60f9-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c60f9-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c60f9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c60f9-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c60f9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c60f9-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c60f9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c60f9-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c60f9-114">See Also</span></span>  
    
 

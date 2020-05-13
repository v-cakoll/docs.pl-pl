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
ms.openlocfilehash: 9270afa1d8c8ddd74cfe6dd05e39c1480f5767e6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206933"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="2903a-102">ICorDebugModule::GetBaseAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="2903a-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="2903a-103">Pobiera adres podstawowy modułu.</span><span class="sxs-lookup"><span data-stu-id="2903a-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2903a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2903a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2903a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2903a-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="2903a-106">określoną A `CORDB_ADDRESS` określający adres podstawowy modułu.</span><span class="sxs-lookup"><span data-stu-id="2903a-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2903a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2903a-107">Remarks</span></span>  
 <span data-ttu-id="2903a-108">Jeśli moduł jest obrazem natywnym (czyli jeśli moduł został wyprodukowany przez generator obrazu natywnego, NGen. exe), jego adres podstawowy będzie równy zero.</span><span class="sxs-lookup"><span data-stu-id="2903a-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2903a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2903a-109">Requirements</span></span>  
 <span data-ttu-id="2903a-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2903a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2903a-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2903a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2903a-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2903a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2903a-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2903a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2903a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2903a-114">See also</span></span>

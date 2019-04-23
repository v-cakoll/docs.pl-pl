---
title: ICorDebugProcess5::GetTypeForTypeID — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeForTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aeb4ad1dffe4553b243b5168037aea8b68f8244b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222064"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="84c33-102">ICorDebugProcess5::GetTypeForTypeID — Metoda</span><span class="sxs-lookup"><span data-stu-id="84c33-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="84c33-103">Konwertuje wartość będącą liczbą ICorDebugType identyfikator typu.</span><span class="sxs-lookup"><span data-stu-id="84c33-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84c33-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84c33-104">Syntax</span></span>  
  
```  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84c33-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84c33-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="84c33-106">[in] Identyfikator typu.</span><span class="sxs-lookup"><span data-stu-id="84c33-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="84c33-107">[out] Wskaźnik na adres obiektu ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="84c33-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84c33-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84c33-108">Remarks</span></span>  
 <span data-ttu-id="84c33-109">W niektórych przypadkach, metody, które zwracają identyfikatora typu może zwracać wartość null `COR_TYPEID` wartość.</span><span class="sxs-lookup"><span data-stu-id="84c33-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="84c33-110">Jeśli ta wartość jest przekazywana jako `id` argument `GetTypeForTypeID` metody będą się niepowodzeniem i zwróci `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="84c33-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84c33-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84c33-111">Requirements</span></span>  
 <span data-ttu-id="84c33-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84c33-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84c33-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84c33-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84c33-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84c33-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84c33-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84c33-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84c33-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84c33-116">See also</span></span>

- [<span data-ttu-id="84c33-117">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="84c33-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="84c33-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="84c33-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

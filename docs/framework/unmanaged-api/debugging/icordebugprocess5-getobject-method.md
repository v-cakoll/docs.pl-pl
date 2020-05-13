---
title: ICorDebugProcess5::GetObject — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type:
- apiref
ms.openlocfilehash: de570507c4312f09def0908b9d56e5371c63527e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207295"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="418af-102">ICorDebugProcess5::GetObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="418af-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="418af-103">Konwertuje adres obiektu na obiekt "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="418af-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="418af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="418af-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="418af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="418af-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="418af-106">podczas Adres obiektu.</span><span class="sxs-lookup"><span data-stu-id="418af-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="418af-107">określoną Wskaźnik do adresu obiektu "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="418af-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="418af-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="418af-108">Remarks</span></span>  
 <span data-ttu-id="418af-109">Jeśli nie `addr` wskazuje prawidłowego obiektu zarządzanego, `GetObject` Metoda zwraca `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="418af-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="418af-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="418af-110">Requirements</span></span>  
 <span data-ttu-id="418af-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="418af-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="418af-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="418af-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="418af-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="418af-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="418af-114">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="418af-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="418af-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="418af-115">See also</span></span>

- [<span data-ttu-id="418af-116">ICorDebugProcess5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="418af-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="418af-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="418af-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

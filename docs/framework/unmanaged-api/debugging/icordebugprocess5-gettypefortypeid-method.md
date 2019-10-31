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
ms.openlocfilehash: 39f5c1813b08f4d72c610820b1434e29eb4aec8e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121273"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="56202-102">ICorDebugProcess5::GetTypeForTypeID — Metoda</span><span class="sxs-lookup"><span data-stu-id="56202-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="56202-103">Konwertuje identyfikator typu na wartość ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="56202-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56202-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="56202-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56202-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56202-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="56202-106">podczas Identyfikator typu.</span><span class="sxs-lookup"><span data-stu-id="56202-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="56202-107">określoną Wskaźnik do adresu obiektu ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="56202-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56202-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="56202-108">Remarks</span></span>  
 <span data-ttu-id="56202-109">W niektórych przypadkach metody, które zwracają identyfikator typu, mogą zwracać wartość null `COR_TYPEID`.</span><span class="sxs-lookup"><span data-stu-id="56202-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="56202-110">Jeśli ta wartość jest przenoszona jako argument `id`, Metoda `GetTypeForTypeID` zakończy się niepowodzeniem i zwróci `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="56202-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56202-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="56202-111">Requirements</span></span>  
 <span data-ttu-id="56202-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56202-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56202-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="56202-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56202-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="56202-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56202-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56202-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56202-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="56202-116">See also</span></span>

- [<span data-ttu-id="56202-117">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="56202-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="56202-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="56202-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

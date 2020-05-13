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
ms.openlocfilehash: ea7f7a9d4589e4f08b1b1e20b4d073bb5f822714
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212766"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="a6f5b-102">ICorDebugProcess5::GetTypeForTypeID — Metoda</span><span class="sxs-lookup"><span data-stu-id="a6f5b-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="a6f5b-103">Konwertuje identyfikator typu na wartość ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="a6f5b-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6f5b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6f5b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6f5b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6f5b-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="a6f5b-106">podczas Identyfikator typu.</span><span class="sxs-lookup"><span data-stu-id="a6f5b-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="a6f5b-107">określoną Wskaźnik do adresu obiektu ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="a6f5b-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6f5b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6f5b-108">Remarks</span></span>  
 <span data-ttu-id="a6f5b-109">W niektórych przypadkach metody, które zwracają identyfikator typu, mogą zwracać wartość null `COR_TYPEID` .</span><span class="sxs-lookup"><span data-stu-id="a6f5b-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="a6f5b-110">Jeśli ta wartość jest przenoszona jako `id` argument, `GetTypeForTypeID` Metoda zakończy się niepowodzeniem i zwróci `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="a6f5b-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6f5b-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a6f5b-111">Requirements</span></span>  
 <span data-ttu-id="a6f5b-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6f5b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6f5b-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a6f5b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6f5b-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a6f5b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6f5b-115">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6f5b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6f5b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6f5b-116">See also</span></span>

- [<span data-ttu-id="a6f5b-117">ICorDebugProcess5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a6f5b-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="a6f5b-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="a6f5b-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

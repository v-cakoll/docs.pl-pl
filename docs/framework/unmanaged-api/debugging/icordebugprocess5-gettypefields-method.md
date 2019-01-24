---
title: ICorDebugProcess5::GetTypeFields — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f688993bfd8e6bef66451b075a49f31efe641cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497108"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="5a928-102">ICorDebugProcess5::GetTypeFields — Metoda</span><span class="sxs-lookup"><span data-stu-id="5a928-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="5a928-103">Zawiera informacje dotyczące pola, które należą do typu.</span><span class="sxs-lookup"><span data-stu-id="5a928-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a928-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5a928-104">Syntax</span></span>  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a928-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a928-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="5a928-106">[in] Identyfikator typu, w których informacje są pobierane.</span><span class="sxs-lookup"><span data-stu-id="5a928-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="5a928-107">[in] Liczba [cor_field —](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) obiekty, których informacje pole ma być pobrana.</span><span class="sxs-lookup"><span data-stu-id="5a928-107">[in] The number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="5a928-108">[out] Tablica [cor_field —](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) obiektów, które dostarczają informacji na temat pól, które należą do tego typu.</span><span class="sxs-lookup"><span data-stu-id="5a928-108">[out] An array of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="5a928-109">[out] Wskaźnik do liczby [cor_field —](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) obiektów uwzględnionych w `fields`.</span><span class="sxs-lookup"><span data-stu-id="5a928-109">[out] A pointer to the number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a928-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5a928-110">Remarks</span></span>  
 <span data-ttu-id="5a928-111">`celt` Parametr, który określa liczbę pól, których informacje pola, metody używane do wypełniania `fields`, powinien odpowiadać wartości `COR_TYPE_LAYOUT::numFields` pola.</span><span class="sxs-lookup"><span data-stu-id="5a928-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a928-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5a928-112">Requirements</span></span>  
 <span data-ttu-id="5a928-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a928-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a928-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a928-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a928-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a928-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a928-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a928-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a928-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a928-117">See also</span></span>
- [<span data-ttu-id="5a928-118">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="5a928-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="5a928-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5a928-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

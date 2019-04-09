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
ms.openlocfilehash: 7c2725c62105e92996bb2d8e79e8ff504904e9c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107955"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="dac38-102">ICorDebugProcess5::GetTypeFields — Metoda</span><span class="sxs-lookup"><span data-stu-id="dac38-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="dac38-103">Zawiera informacje dotyczące pola, które należą do typu.</span><span class="sxs-lookup"><span data-stu-id="dac38-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dac38-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dac38-104">Syntax</span></span>  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dac38-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dac38-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="dac38-106">[in] Identyfikator typu, w których informacje są pobierane.</span><span class="sxs-lookup"><span data-stu-id="dac38-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="dac38-107">[in] Liczba [cor_field —](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) obiekty, których informacje pole ma być pobrana.</span><span class="sxs-lookup"><span data-stu-id="dac38-107">[in] The number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="dac38-108">[out] Tablica [cor_field —](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) obiektów, które dostarczają informacji na temat pól, które należą do tego typu.</span><span class="sxs-lookup"><span data-stu-id="dac38-108">[out] An array of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="dac38-109">[out] Wskaźnik do liczby [cor_field —](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) obiektów uwzględnionych w `fields`.</span><span class="sxs-lookup"><span data-stu-id="dac38-109">[out] A pointer to the number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dac38-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dac38-110">Remarks</span></span>  
 <span data-ttu-id="dac38-111">`celt` Parametr, który określa liczbę pól, których informacje pola, metody używane do wypełniania `fields`, powinien odpowiadać wartości `COR_TYPE_LAYOUT::numFields` pola.</span><span class="sxs-lookup"><span data-stu-id="dac38-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dac38-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dac38-112">Requirements</span></span>  
 <span data-ttu-id="dac38-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dac38-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dac38-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dac38-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dac38-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dac38-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="dac38-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="dac38-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dac38-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dac38-117">See also</span></span>

- [<span data-ttu-id="dac38-118">ICorDebugProcess5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dac38-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="dac38-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="dac38-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

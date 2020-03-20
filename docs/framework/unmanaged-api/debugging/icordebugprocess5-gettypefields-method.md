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
ms.openlocfilehash: 29006eba3d3a523fd24a461207ab12222a639782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178589"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="1597c-102">ICorDebugProcess5::GetTypeFields — Metoda</span><span class="sxs-lookup"><span data-stu-id="1597c-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="1597c-103">Zawiera informacje o polach należących do typu.</span><span class="sxs-lookup"><span data-stu-id="1597c-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1597c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1597c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1597c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1597c-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="1597c-106">[w] Identyfikator typu, którego informacje o polu są pobierane.</span><span class="sxs-lookup"><span data-stu-id="1597c-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="1597c-107">[w] Liczba [obiektów COR_FIELD,](cor-field-structure.md) których informacje o polu mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="1597c-107">[in] The number of [COR_FIELD](cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="1597c-108">[na zewnątrz] Tablica [COR_FIELD](cor-field-structure.md) obiektów, które zawierają informacje o polach należących do typu.</span><span class="sxs-lookup"><span data-stu-id="1597c-108">[out] An array of [COR_FIELD](cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="1597c-109">[na zewnątrz] Wskaźnik do liczby [obiektów COR_FIELD](cor-field-structure.md) uwzględnionych w `fields`pliku .</span><span class="sxs-lookup"><span data-stu-id="1597c-109">[out] A pointer to the number of [COR_FIELD](cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1597c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1597c-110">Remarks</span></span>  
 <span data-ttu-id="1597c-111">Parametr, `celt` który określa liczbę pól, których informacje o polu użyto metody do zapełnienia, `fields`powinien odpowiadać wartości `COR_TYPE_LAYOUT::numFields` pola.</span><span class="sxs-lookup"><span data-stu-id="1597c-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1597c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1597c-112">Requirements</span></span>  
 <span data-ttu-id="1597c-113">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1597c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1597c-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1597c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1597c-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1597c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1597c-116">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1597c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1597c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1597c-117">See also</span></span>

- [<span data-ttu-id="1597c-118">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="1597c-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="1597c-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1597c-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

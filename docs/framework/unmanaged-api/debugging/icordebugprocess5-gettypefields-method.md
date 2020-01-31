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
ms.openlocfilehash: 644b5ed751caaf1809250244b37badc8037b0f57
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792352"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="b6275-102">ICorDebugProcess5::GetTypeFields — Metoda</span><span class="sxs-lookup"><span data-stu-id="b6275-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="b6275-103">Zawiera informacje o polach, które należą do typu.</span><span class="sxs-lookup"><span data-stu-id="b6275-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6275-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6275-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6275-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6275-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="b6275-106">podczas Identyfikator typu, którego informacje o polu są pobierane.</span><span class="sxs-lookup"><span data-stu-id="b6275-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="b6275-107">podczas Liczba obiektów [COR_FIELD](cor-field-structure.md) , których informacje o polach mają być pobierane.</span><span class="sxs-lookup"><span data-stu-id="b6275-107">[in] The number of [COR_FIELD](cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="b6275-108">określoną Tablica obiektów [COR_FIELD](cor-field-structure.md) , które zawierają informacje o polach, które należą do typu.</span><span class="sxs-lookup"><span data-stu-id="b6275-108">[out] An array of [COR_FIELD](cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="b6275-109">określoną Wskaźnik do liczby [COR_FIELD](cor-field-structure.md) obiektów zawartych w `fields`.</span><span class="sxs-lookup"><span data-stu-id="b6275-109">[out] A pointer to the number of [COR_FIELD](cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6275-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6275-110">Remarks</span></span>  
 <span data-ttu-id="b6275-111">`celt` parametr, który określa liczbę pól, których informacje pola są używane przez metodę do wypełniania `fields`, powinien odpowiadać wartości pola `COR_TYPE_LAYOUT::numFields`.</span><span class="sxs-lookup"><span data-stu-id="b6275-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6275-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6275-112">Requirements</span></span>  
 <span data-ttu-id="b6275-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6275-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6275-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b6275-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6275-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b6275-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6275-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6275-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6275-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6275-117">See also</span></span>

- [<span data-ttu-id="b6275-118">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="b6275-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="b6275-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b6275-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

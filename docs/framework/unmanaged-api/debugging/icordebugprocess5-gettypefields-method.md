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
ms.openlocfilehash: a2c7f7b722abac6acf71d3b64276862441695a5f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212792"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="26b2b-102">ICorDebugProcess5::GetTypeFields — Metoda</span><span class="sxs-lookup"><span data-stu-id="26b2b-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="26b2b-103">Zawiera informacje o polach, które należą do typu.</span><span class="sxs-lookup"><span data-stu-id="26b2b-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26b2b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26b2b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26b2b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26b2b-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="26b2b-106">podczas Identyfikator typu, którego informacje o polu są pobierane.</span><span class="sxs-lookup"><span data-stu-id="26b2b-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="26b2b-107">podczas Liczba obiektów [COR_FIELD](cor-field-structure.md) , których informacje o polach mają być pobierane.</span><span class="sxs-lookup"><span data-stu-id="26b2b-107">[in] The number of [COR_FIELD](cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="26b2b-108">określoną Tablica obiektów [COR_FIELD](cor-field-structure.md) , które zawierają informacje o polach, które należą do typu.</span><span class="sxs-lookup"><span data-stu-id="26b2b-108">[out] An array of [COR_FIELD](cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="26b2b-109">określoną Wskaźnik do liczby [COR_FIELD](cor-field-structure.md) obiektów uwzględnionych w `fields` .</span><span class="sxs-lookup"><span data-stu-id="26b2b-109">[out] A pointer to the number of [COR_FIELD](cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26b2b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26b2b-110">Remarks</span></span>  
 <span data-ttu-id="26b2b-111">`celt`Parametr, który określa liczbę pól, których informacje pola są używane przez metodę do wypełnienia `fields` , powinien odpowiadać wartości `COR_TYPE_LAYOUT::numFields` pola.</span><span class="sxs-lookup"><span data-stu-id="26b2b-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26b2b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26b2b-112">Requirements</span></span>  
 <span data-ttu-id="26b2b-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26b2b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26b2b-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="26b2b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26b2b-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="26b2b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26b2b-116">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26b2b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26b2b-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26b2b-117">See also</span></span>

- [<span data-ttu-id="26b2b-118">ICorDebugProcess5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="26b2b-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="26b2b-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="26b2b-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

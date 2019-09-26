---
title: COR_TYPE_LAYOUT — Struktura
ms.date: 03/30/2017
api_name:
- COR_TYPE_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPE_LAYOUT
helpviewer_keywords:
- COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bd274b1eb14532629580e777288317186544912
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274165"
---
# <a name="cor_type_layout-structure"></a><span data-ttu-id="0b6be-102">COR_TYPE_LAYOUT — Struktura</span><span class="sxs-lookup"><span data-stu-id="0b6be-102">COR_TYPE_LAYOUT Structure</span></span>
<span data-ttu-id="0b6be-103">Zawiera informacje na temat układu obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="0b6be-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b6be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b6be-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="0b6be-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0b6be-105">Members</span></span>  
  
|<span data-ttu-id="0b6be-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="0b6be-106">Member</span></span>|<span data-ttu-id="0b6be-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0b6be-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="0b6be-108">Identyfikator typu nadrzędnego dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="0b6be-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="0b6be-109">Będzie to identyfikator typu NULL (token1 = 0, token2 = 0), jeśli identyfikator typu odpowiada <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0b6be-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="0b6be-110">Rozmiar podstawowy obiektu tego typu.</span><span class="sxs-lookup"><span data-stu-id="0b6be-110">The base size of an object of this type.</span></span> <span data-ttu-id="0b6be-111">Jest to całkowity rozmiar obiektów niezmiennych.</span><span class="sxs-lookup"><span data-stu-id="0b6be-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="0b6be-112">Liczba pól uwzględnionych w obiektach tego typu.</span><span class="sxs-lookup"><span data-stu-id="0b6be-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="0b6be-113">Jeśli ten typ jest opakowany, początkowe przesunięcie pól obiektu.</span><span class="sxs-lookup"><span data-stu-id="0b6be-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="0b6be-114">To pole jest prawidłowe tylko dla typów wartości, takich jak elementy pierwotne i struktury.</span><span class="sxs-lookup"><span data-stu-id="0b6be-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="0b6be-115">CorElementType —, do którego należy ten typ.</span><span class="sxs-lookup"><span data-stu-id="0b6be-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b6be-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b6be-116">Remarks</span></span>  
 <span data-ttu-id="0b6be-117">Jeśli `numFields` jest większa od zera, można wywołać metodę [ICorDebugProcess5:: GetTypeFields —](icordebugprocess5-gettypefields-method.md) , aby uzyskać informacje o polach w tym typie.</span><span class="sxs-lookup"><span data-stu-id="0b6be-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="0b6be-118">Jeśli `type` jest `ELEMENT_TYPE_STRING` ,`ELEMENT_TYPE_ARRAY`, lub`ELEMENT_TYPE_SZARRAY`, rozmiar obiektów tego typu jest zmienny i można przekazać strukturę [COR_TYPEID](cor-typeid-structure.md) do metody [ICorDebugProcess5:: GetArrayLayout —](icordebugprocess5-getarraylayout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0b6be-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b6be-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b6be-119">Requirements</span></span>  
 <span data-ttu-id="0b6be-120">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b6be-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b6be-121">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b6be-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b6be-122">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b6be-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b6be-123">**.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b6be-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b6be-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b6be-124">See also</span></span>

- [<span data-ttu-id="0b6be-125">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="0b6be-125">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="0b6be-126">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="0b6be-126">Debugging</span></span>](index.md)

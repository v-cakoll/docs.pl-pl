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
ms.openlocfilehash: 7efb2c3e8033b8bd8fa736a29b2ab9b3bedebeaa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109645"
---
# <a name="cortypelayout-structure"></a><span data-ttu-id="199f3-102">COR_TYPE_LAYOUT — Struktura</span><span class="sxs-lookup"><span data-stu-id="199f3-102">COR_TYPE_LAYOUT Structure</span></span>
<span data-ttu-id="199f3-103">Informacje dotyczące układu obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="199f3-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="199f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="199f3-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="199f3-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="199f3-105">Members</span></span>  
  
|<span data-ttu-id="199f3-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="199f3-106">Member</span></span>|<span data-ttu-id="199f3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="199f3-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="199f3-108">Identyfikator typu nadrzędnego do tego typu.</span><span class="sxs-lookup"><span data-stu-id="199f3-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="199f3-109">Jest to identyfikator typu o wartości NULL (token1 = 0, token2 = 0), gdy odpowiada identyfikator typu <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="199f3-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="199f3-110">Wielkość podstawowa obiektu tego typu.</span><span class="sxs-lookup"><span data-stu-id="199f3-110">The base size of an object of this type.</span></span> <span data-ttu-id="199f3-111">Jest to łączny rozmiar obiektów wielkości niezmienny.</span><span class="sxs-lookup"><span data-stu-id="199f3-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="199f3-112">Numer pola zawarte w obiektach tego typu.</span><span class="sxs-lookup"><span data-stu-id="199f3-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="199f3-113">Jeśli ten typ jest opakowany, początku przesunięcia pól obiektu.</span><span class="sxs-lookup"><span data-stu-id="199f3-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="199f3-114">To pole jest prawidłowe tylko w przypadku typów wartości, takich jak podstawowych i struktur.</span><span class="sxs-lookup"><span data-stu-id="199f3-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="199f3-115">Corelementtype — do której należy tego typu.</span><span class="sxs-lookup"><span data-stu-id="199f3-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="199f3-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="199f3-116">Remarks</span></span>  
 <span data-ttu-id="199f3-117">Jeśli `numFields` jest większa od zera, można wywołać [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) metodę, aby uzyskać informacje na temat pól, w tym typie.</span><span class="sxs-lookup"><span data-stu-id="199f3-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="199f3-118">Jeśli `type` jest `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, lub `ELEMENT_TYPE_SZARRAY`, rozmiar obiektów tego typu jest zmienną i można przekazać [cor_typeid —](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) struktury do [ICorDebugProcess5::GetArrayLayout ](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="199f3-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="199f3-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="199f3-119">Requirements</span></span>  
 <span data-ttu-id="199f3-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="199f3-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="199f3-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="199f3-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="199f3-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="199f3-122">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="199f3-123">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="199f3-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="199f3-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="199f3-124">See also</span></span>

- [<span data-ttu-id="199f3-125">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="199f3-125">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="199f3-126">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="199f3-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

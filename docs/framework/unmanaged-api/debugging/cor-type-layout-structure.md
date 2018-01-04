---
title: "COR_TYPE_LAYOUT — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_TYPE_LAYOUT
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_TYPE_LAYOUT
helpviewer_keywords: COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 250d78dd9983b75fa7e1b3cfd99215160fbc2b1d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cortypelayout-structure"></a><span data-ttu-id="41832-102">COR_TYPE_LAYOUT — Struktura</span><span class="sxs-lookup"><span data-stu-id="41832-102">COR_TYPE_LAYOUT Structure</span></span>
<span data-ttu-id="41832-103">Zawiera informacje o układzie obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="41832-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41832-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="41832-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="41832-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="41832-105">Members</span></span>  
  
|<span data-ttu-id="41832-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="41832-106">Member</span></span>|<span data-ttu-id="41832-107">Opis</span><span class="sxs-lookup"><span data-stu-id="41832-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="41832-108">Identyfikator typu nadrzędnego do tego typu.</span><span class="sxs-lookup"><span data-stu-id="41832-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="41832-109">Będzie to identyfikator typu NULL (token1 = 0, token2 = 0), gdy odpowiada identyfikator typu <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="41832-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="41832-110">Wielkość podstawowa obiektu tego typu.</span><span class="sxs-lookup"><span data-stu-id="41832-110">The base size of an object of this type.</span></span> <span data-ttu-id="41832-111">Jest to łączny rozmiar obiektów o rozmiarze-variable.</span><span class="sxs-lookup"><span data-stu-id="41832-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="41832-112">Liczba pól zawarte w obiektach tego typu.</span><span class="sxs-lookup"><span data-stu-id="41832-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="41832-113">Jeśli ten typ jest opakowany, początku przesunięcia pól obiektu.</span><span class="sxs-lookup"><span data-stu-id="41832-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="41832-114">W tym polu jest prawidłowa tylko dla typów wartości, takich jak podstawowych i struktury.</span><span class="sxs-lookup"><span data-stu-id="41832-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="41832-115">CorElementType, do którego należy tego typu.</span><span class="sxs-lookup"><span data-stu-id="41832-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41832-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41832-116">Remarks</span></span>  
 <span data-ttu-id="41832-117">Jeśli `numFields` jest większa od zera, można wywołać [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) metody, aby uzyskać informacje o pola w tym typie.</span><span class="sxs-lookup"><span data-stu-id="41832-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="41832-118">Jeśli `type` jest `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, lub `ELEMENT_TYPE_SZARRAY`, rozmiar obiektów tego typu jest zmienną i można przekazać [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) struktury do [ICorDebugProcess5::GetArrayLayout ](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="41832-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41832-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41832-119">Requirements</span></span>  
 <span data-ttu-id="41832-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41832-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41832-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="41832-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41832-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41832-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41832-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41832-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41832-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41832-124">See Also</span></span>  
 [<span data-ttu-id="41832-125">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="41832-125">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="41832-126">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="41832-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

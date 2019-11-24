---
title: COR_NATIVE_LINK — Struktura
ms.date: 03/30/2017
api_name:
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
ms.openlocfilehash: d03c22c455f0e44ce32d4593d9eee50ceef94a22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443946"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="0a45c-102">COR_NATIVE_LINK — Struktura</span><span class="sxs-lookup"><span data-stu-id="0a45c-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="0a45c-103">Contains information that is used to link native code.</span><span class="sxs-lookup"><span data-stu-id="0a45c-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a45c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a45c-104">Syntax</span></span>  
  
```cpp  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="0a45c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0a45c-105">Members</span></span>  
  
|<span data-ttu-id="0a45c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="0a45c-106">Member</span></span>|<span data-ttu-id="0a45c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0a45c-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="0a45c-108">The type to be linked in native code.</span><span class="sxs-lookup"><span data-stu-id="0a45c-108">The type to be linked in native code.</span></span> <span data-ttu-id="0a45c-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span><span class="sxs-lookup"><span data-stu-id="0a45c-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="0a45c-110">Flags used by the linker when linking native code.</span><span class="sxs-lookup"><span data-stu-id="0a45c-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="0a45c-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span><span class="sxs-lookup"><span data-stu-id="0a45c-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="0a45c-112">The MemberRef metadata token that represents the entry point.</span><span class="sxs-lookup"><span data-stu-id="0a45c-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="0a45c-113">The format is `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="0a45c-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0a45c-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a45c-114">Requirements</span></span>  
 <span data-ttu-id="0a45c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a45c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a45c-116">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0a45c-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0a45c-117">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0a45c-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0a45c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a45c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a45c-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a45c-119">See also</span></span>

- [<span data-ttu-id="0a45c-120">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="0a45c-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="0a45c-121">CorNativeLinkType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0a45c-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [<span data-ttu-id="0a45c-122">CorNativeLinkFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0a45c-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)

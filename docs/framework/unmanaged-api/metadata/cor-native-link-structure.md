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
ms.openlocfilehash: 812b70a594b5aa933f52d36f32d96d712267ecf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177961"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="45df5-102">COR_NATIVE_LINK — Struktura</span><span class="sxs-lookup"><span data-stu-id="45df5-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="45df5-103">Zawiera informacje używane do łączenia kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="45df5-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45df5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="45df5-104">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="45df5-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="45df5-105">Members</span></span>  
  
|<span data-ttu-id="45df5-106">Członek</span><span class="sxs-lookup"><span data-stu-id="45df5-106">Member</span></span>|<span data-ttu-id="45df5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="45df5-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="45df5-108">Typ, który ma być połączony w kodzie macierzystym.</span><span class="sxs-lookup"><span data-stu-id="45df5-108">The type to be linked in native code.</span></span> <span data-ttu-id="45df5-109">Ta wartość jest jedną z [corNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="45df5-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="45df5-110">Flagi używane przez konsolidator podczas łączenia kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="45df5-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="45df5-111">Ta wartość jest jedną z [corNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="45df5-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="45df5-112">Token metadanych MemberRef, który reprezentuje punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="45df5-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="45df5-113">Format to `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="45df5-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="45df5-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="45df5-114">Requirements</span></span>  
 <span data-ttu-id="45df5-115">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45df5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45df5-116">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="45df5-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="45df5-117">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="45df5-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="45df5-118">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45df5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45df5-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45df5-119">See also</span></span>

- [<span data-ttu-id="45df5-120">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="45df5-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="45df5-121">CorNativeLinkType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="45df5-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [<span data-ttu-id="45df5-122">CorNativeLinkFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="45df5-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)

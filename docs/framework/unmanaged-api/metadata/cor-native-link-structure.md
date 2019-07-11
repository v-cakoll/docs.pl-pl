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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ae518e5a736a78a261dc3821d53d93afee95a271
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779997"
---
# <a name="cornativelink-structure"></a><span data-ttu-id="24dea-102">COR_NATIVE_LINK — Struktura</span><span class="sxs-lookup"><span data-stu-id="24dea-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="24dea-103">Zawiera informacje, które jest używane do łączenia kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="24dea-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24dea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24dea-104">Syntax</span></span>  
  
```cpp  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="24dea-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="24dea-105">Members</span></span>  
  
|<span data-ttu-id="24dea-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="24dea-106">Member</span></span>|<span data-ttu-id="24dea-107">Opis</span><span class="sxs-lookup"><span data-stu-id="24dea-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="24dea-108">Typ, które mają być łączone w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="24dea-108">The type to be linked in native code.</span></span> <span data-ttu-id="24dea-109">Ta wartość jest jednym z [cornativelinktype —](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="24dea-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="24dea-110">Flagi używane przez konsolidator, podczas łączenia kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="24dea-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="24dea-111">Ta wartość jest jednym z [cornativelinkflags —](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="24dea-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="24dea-112">Token metadanych MemberRef, który reprezentuje punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="24dea-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="24dea-113">Format jest `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="24dea-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="24dea-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24dea-114">Requirements</span></span>  
 <span data-ttu-id="24dea-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24dea-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24dea-116">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="24dea-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="24dea-117">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="24dea-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="24dea-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24dea-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24dea-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24dea-119">See also</span></span>

- [<span data-ttu-id="24dea-120">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="24dea-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [<span data-ttu-id="24dea-121">CorNativeLinkType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="24dea-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [<span data-ttu-id="24dea-122">CorNativeLinkFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="24dea-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)

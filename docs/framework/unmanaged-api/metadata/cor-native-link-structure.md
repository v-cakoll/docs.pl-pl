---
title: "COR_NATIVE_LINK — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_NATIVE_LINK
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_NATIVE_LINK
helpviewer_keywords: COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e27b66fce8a78ef0feb7ed10e77cc51fc1fe83c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cornativelink-structure"></a><span data-ttu-id="eebce-102">COR_NATIVE_LINK — Struktura</span><span class="sxs-lookup"><span data-stu-id="eebce-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="eebce-103">Zawiera informacje, które jest używane do łączenia kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="eebce-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eebce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eebce-104">Syntax</span></span>  
  
```  
typedef struct   
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="eebce-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="eebce-105">Members</span></span>  
  
|<span data-ttu-id="eebce-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="eebce-106">Member</span></span>|<span data-ttu-id="eebce-107">Opis</span><span class="sxs-lookup"><span data-stu-id="eebce-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="eebce-108">Typ, które mają być łączone w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="eebce-108">The type to be linked in native code.</span></span> <span data-ttu-id="eebce-109">Ta wartość jest jednym z [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="eebce-109">This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="eebce-110">Flagi używane przez konsolidator podczas łączenia kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="eebce-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="eebce-111">Ta wartość jest jednym z [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="eebce-111">This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="eebce-112">Token metadanych elementu MemberRef, który reprezentuje punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="eebce-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="eebce-113">Format jest `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="eebce-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="eebce-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eebce-114">Requirements</span></span>  
 <span data-ttu-id="eebce-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eebce-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eebce-116">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="eebce-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eebce-117">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eebce-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eebce-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eebce-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eebce-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eebce-119">See Also</span></span>  
 [<span data-ttu-id="eebce-120">Metadane struktury</span><span class="sxs-lookup"><span data-stu-id="eebce-120">Metadata Structures</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [<span data-ttu-id="eebce-121">CorNativeLinkType — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="eebce-121">CorNativeLinkType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)  
 [<span data-ttu-id="eebce-122">CorNativeLinkFlags — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="eebce-122">CorNativeLinkFlags Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)

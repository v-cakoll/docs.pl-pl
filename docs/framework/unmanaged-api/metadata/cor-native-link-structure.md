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
ms.openlocfilehash: a11b7d5939c4c20504b1ff3dfb4613f85bca0db4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007978"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="04f78-102">COR_NATIVE_LINK — Struktura</span><span class="sxs-lookup"><span data-stu-id="04f78-102">COR_NATIVE_LINK Structure</span></span>
<span data-ttu-id="04f78-103">Zawiera informacje, które są używane do łączenia kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="04f78-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04f78-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="04f78-104">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="04f78-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="04f78-105">Members</span></span>  
  
|<span data-ttu-id="04f78-106">Członek</span><span class="sxs-lookup"><span data-stu-id="04f78-106">Member</span></span>|<span data-ttu-id="04f78-107">Opis</span><span class="sxs-lookup"><span data-stu-id="04f78-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="04f78-108">Typ, który ma być połączony w kodzie natywnym.</span><span class="sxs-lookup"><span data-stu-id="04f78-108">The type to be linked in native code.</span></span> <span data-ttu-id="04f78-109">Ta wartość jest jedną z wartości [CorNativeLinkType —](cornativelinktype-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="04f78-109">This value is one of the [CorNativeLinkType](cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="04f78-110">Flagi używane przez konsolidator podczas łączenia kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="04f78-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="04f78-111">Ta wartość jest jedną z wartości [CorNativeLinkFlags —](cornativelinkflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="04f78-111">This value is one of the [CorNativeLinkFlags](cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="04f78-112">Token metadanych elementu MemberRef reprezentujący punkt wejścia.</span><span class="sxs-lookup"><span data-stu-id="04f78-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="04f78-113">Format to `lib:entrypoint`.</span><span class="sxs-lookup"><span data-stu-id="04f78-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="04f78-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="04f78-114">Requirements</span></span>  
 <span data-ttu-id="04f78-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04f78-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04f78-116">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="04f78-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04f78-117">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="04f78-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="04f78-118">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04f78-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04f78-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="04f78-119">See also</span></span>

- [<span data-ttu-id="04f78-120">Struktury metadanych</span><span class="sxs-lookup"><span data-stu-id="04f78-120">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="04f78-121">CorNativeLinkType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="04f78-121">CorNativeLinkType Enumeration</span></span>](cornativelinktype-enumeration.md)
- [<span data-ttu-id="04f78-122">CorNativeLinkFlags, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="04f78-122">CorNativeLinkFlags Enumeration</span></span>](cornativelinkflags-enumeration.md)

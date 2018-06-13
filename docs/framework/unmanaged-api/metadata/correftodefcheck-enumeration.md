---
title: CorRefToDefCheck — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5caf432b5de7cb0c8ff0e6f53b3e79a64ecf802e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443316"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="6a64d-102">CorRefToDefCheck — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6a64d-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="6a64d-103">Określa flagi kontrolujące elementy do którego istnieje odwołanie, które są konwertowane na ich definicje w celu optymalizacji kodu.</span><span class="sxs-lookup"><span data-stu-id="6a64d-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a64d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a64d-104">Syntax</span></span>  
  
```  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="6a64d-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6a64d-105">Members</span></span>  
  
|<span data-ttu-id="6a64d-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6a64d-106">Member</span></span>|<span data-ttu-id="6a64d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6a64d-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="6a64d-108">Określa, że odwołania do typu i odwołania do elementu członkowskiego powinny być konwertowane do definicji.</span><span class="sxs-lookup"><span data-stu-id="6a64d-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="6a64d-109">Jest to wartość domyślna (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span><span class="sxs-lookup"><span data-stu-id="6a64d-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="6a64d-110">Określa, że wszystkie elementy z którym związane są odwołania powinny być konwertowane do definicji.</span><span class="sxs-lookup"><span data-stu-id="6a64d-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="6a64d-111">Określa, że nie przywoływanych elementów powinny być konwertowane do definicji.</span><span class="sxs-lookup"><span data-stu-id="6a64d-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="6a64d-112">Określa, że tylko odwołania do typu powinny być konwertowane na typ definicje.</span><span class="sxs-lookup"><span data-stu-id="6a64d-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="6a64d-113">Określa, że tylko odwołania do elementu członkowskiego powinny być konwertowane do definicji.</span><span class="sxs-lookup"><span data-stu-id="6a64d-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="6a64d-114">Oznacza to, że odwołania do elementu członkowskiego powinny być konwertowane na definicjami metod lub definicje pól.</span><span class="sxs-lookup"><span data-stu-id="6a64d-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6a64d-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6a64d-115">Requirements</span></span>  
 <span data-ttu-id="6a64d-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a64d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a64d-117">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="6a64d-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="6a64d-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a64d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a64d-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a64d-119">See Also</span></span>  
 [<span data-ttu-id="6a64d-120">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="6a64d-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

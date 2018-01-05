---
title: "CorRefToDefCheck — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRefToDefCheck
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRefToDefCheck
helpviewer_keywords: CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 366110eca3c4621866213b2c9fc4bcf99103d0a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="8feb1-102">CorRefToDefCheck — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8feb1-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="8feb1-103">Określa flagi kontrolujące elementy do którego istnieje odwołanie, które są konwertowane na ich definicje w celu optymalizacji kodu.</span><span class="sxs-lookup"><span data-stu-id="8feb1-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8feb1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8feb1-104">Syntax</span></span>  
  
```  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="8feb1-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8feb1-105">Members</span></span>  
  
|<span data-ttu-id="8feb1-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8feb1-106">Member</span></span>|<span data-ttu-id="8feb1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8feb1-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="8feb1-108">Określa, że odwołania do typu i odwołania do elementu członkowskiego powinny być konwertowane do definicji.</span><span class="sxs-lookup"><span data-stu-id="8feb1-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="8feb1-109">Jest to wartość domyślna (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span><span class="sxs-lookup"><span data-stu-id="8feb1-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="8feb1-110">Określa, że wszystkie elementy z którym związane są odwołania powinny być konwertowane do definicji.</span><span class="sxs-lookup"><span data-stu-id="8feb1-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="8feb1-111">Określa, że nie przywoływanych elementów powinny być konwertowane do definicji.</span><span class="sxs-lookup"><span data-stu-id="8feb1-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="8feb1-112">Określa, że tylko odwołania do typu powinny być konwertowane na typ definicje.</span><span class="sxs-lookup"><span data-stu-id="8feb1-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="8feb1-113">Określa, że tylko odwołania do elementu członkowskiego powinny być konwertowane do definicji.</span><span class="sxs-lookup"><span data-stu-id="8feb1-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="8feb1-114">Oznacza to, że odwołania do elementu członkowskiego powinny być konwertowane na definicjami metod lub definicje pól.</span><span class="sxs-lookup"><span data-stu-id="8feb1-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8feb1-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8feb1-115">Requirements</span></span>  
 <span data-ttu-id="8feb1-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8feb1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8feb1-117">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="8feb1-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8feb1-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8feb1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8feb1-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8feb1-119">See Also</span></span>  
 [<span data-ttu-id="8feb1-120">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="8feb1-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

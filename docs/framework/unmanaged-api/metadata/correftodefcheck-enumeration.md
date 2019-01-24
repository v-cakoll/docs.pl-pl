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
ms.openlocfilehash: a54b20ecf34ecf1824420fcbb3d45fba64017b76
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657197"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="ea7a0-102">CorRefToDefCheck — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ea7a0-102">CorRefToDefCheck Enumeration</span></span>
<span data-ttu-id="ea7a0-103">Określa flagi do kontroli, do którego istnieje odwołanie elementy, które są konwertowane na ich definicji w celu optymalizacji kodu.</span><span class="sxs-lookup"><span data-stu-id="ea7a0-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea7a0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea7a0-104">Syntax</span></span>  
  
```  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="ea7a0-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ea7a0-105">Members</span></span>  
  
|<span data-ttu-id="ea7a0-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ea7a0-106">Member</span></span>|<span data-ttu-id="ea7a0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ea7a0-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="ea7a0-108">Określa, czy typ odwołania i odwołania do elementu członkowskiego powinny być konwertowane do definicji.</span><span class="sxs-lookup"><span data-stu-id="ea7a0-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="ea7a0-109">Jest to wartość domyślna (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span><span class="sxs-lookup"><span data-stu-id="ea7a0-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="ea7a0-110">Określa, że wszystkie elementy odwołania powinny być konwertowane do definicji.</span><span class="sxs-lookup"><span data-stu-id="ea7a0-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="ea7a0-111">Określa, że żadne elementy odwołania powinny być konwertowane na definicje.</span><span class="sxs-lookup"><span data-stu-id="ea7a0-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="ea7a0-112">Określa, że tylko typ odwołania powinny być konwertowane na definicje typów.</span><span class="sxs-lookup"><span data-stu-id="ea7a0-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="ea7a0-113">Określa, że tylko odwołania do elementu członkowskiego powinny być konwertowane do definicji.</span><span class="sxs-lookup"><span data-stu-id="ea7a0-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="ea7a0-114">Oznacza to, że odwołania do elementu członkowskiego powinny być konwertowane na definicje metod lub definicje pól.</span><span class="sxs-lookup"><span data-stu-id="ea7a0-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ea7a0-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ea7a0-115">Requirements</span></span>  
 <span data-ttu-id="ea7a0-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea7a0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea7a0-117">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="ea7a0-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ea7a0-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea7a0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea7a0-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea7a0-119">See also</span></span>
- [<span data-ttu-id="ea7a0-120">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="ea7a0-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

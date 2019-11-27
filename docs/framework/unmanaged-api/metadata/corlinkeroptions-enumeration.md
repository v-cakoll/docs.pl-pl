---
title: CorLinkerOptions — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorLinkerOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLinkerOptions
helpviewer_keywords:
- CorLinkerOptions enumeration [.NET Framework metadata]
ms.assetid: a656aad6-cc7e-4994-8251-004a6a45e18f
topic_type:
- apiref
ms.openlocfilehash: 086e17185df9caa823b44b51cf027f95d635c48d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450274"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="96b7c-102">CorLinkerOptions — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="96b7c-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="96b7c-103">Określa flagi do wybierania opcji konsolidatora metadanych.</span><span class="sxs-lookup"><span data-stu-id="96b7c-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96b7c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="96b7c-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="96b7c-105">Members</span><span class="sxs-lookup"><span data-stu-id="96b7c-105">Members</span></span>  
  
|<span data-ttu-id="96b7c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="96b7c-106">Member</span></span>|<span data-ttu-id="96b7c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="96b7c-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="96b7c-108">Prywatne typy i funkcje globalne nie są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="96b7c-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="96b7c-109">Prywatne typy i funkcje globalne są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="96b7c-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="96b7c-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="96b7c-110">Requirements</span></span>  
 <span data-ttu-id="96b7c-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96b7c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96b7c-112">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="96b7c-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="96b7c-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96b7c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b7c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="96b7c-114">See also</span></span>

- [<span data-ttu-id="96b7c-115">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="96b7c-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

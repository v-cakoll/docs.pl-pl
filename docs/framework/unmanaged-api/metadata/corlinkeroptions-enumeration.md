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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 906b5ef2795d8fad996185f66f145a8cd3618c41
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781810"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="ecea2-102">CorLinkerOptions — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ecea2-102">CorLinkerOptions Enumeration</span></span>
<span data-ttu-id="ecea2-103">Określa flagi, aby wybrać opcje do konsolidatora metadanych.</span><span class="sxs-lookup"><span data-stu-id="ecea2-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecea2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecea2-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="ecea2-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ecea2-105">Members</span></span>  
  
|<span data-ttu-id="ecea2-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ecea2-106">Member</span></span>|<span data-ttu-id="ecea2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ecea2-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="ecea2-108">Prywatne typy i funkcje globalne nie są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="ecea2-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="ecea2-109">Prywatne typy i funkcje globalne są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="ecea2-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ecea2-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ecea2-110">Requirements</span></span>  
 <span data-ttu-id="ecea2-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecea2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecea2-112">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="ecea2-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ecea2-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecea2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecea2-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecea2-114">See also</span></span>

- [<span data-ttu-id="ecea2-115">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="ecea2-115">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

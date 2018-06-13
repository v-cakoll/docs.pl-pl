---
title: COR_PRF_CODE_INFO — Struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_CODE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODE_INFO
helpviewer_keywords:
- COR_PRF_CODE_INFO structure [.NET Framework profiling]
ms.assetid: cf30e27c-1f7e-43a2-ba1e-01e4137301db
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 852e6cbd666441b92afb583b15b72d50d26eff8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449787"
---
# <a name="corprfcodeinfo-structure"></a><span data-ttu-id="e3e85-102">COR_PRF_CODE_INFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="e3e85-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="e3e85-103">Reprezentuje jeden ciągły blok kodu natywnego przechowywane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e3e85-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3e85-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3e85-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="e3e85-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e3e85-105">Members</span></span>  
  
|<span data-ttu-id="e3e85-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="e3e85-106">Member</span></span>|<span data-ttu-id="e3e85-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e3e85-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="e3e85-108">Adres początkowy ciągłego bloku kodu.</span><span class="sxs-lookup"><span data-stu-id="e3e85-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="e3e85-109">Rozmiar bloku.</span><span class="sxs-lookup"><span data-stu-id="e3e85-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e3e85-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3e85-110">Requirements</span></span>  
 <span data-ttu-id="e3e85-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3e85-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3e85-112">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="e3e85-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="e3e85-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3e85-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3e85-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3e85-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3e85-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3e85-115">See Also</span></span>  
 [<span data-ttu-id="e3e85-116">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="e3e85-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)

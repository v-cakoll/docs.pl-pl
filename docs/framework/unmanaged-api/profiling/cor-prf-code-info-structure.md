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
ms.openlocfilehash: e83dbb234cf1cacc0e18d4e42bccb427eb54f14c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617255"
---
# <a name="corprfcodeinfo-structure"></a><span data-ttu-id="c31ab-102">COR_PRF_CODE_INFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="c31ab-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="c31ab-103">Reprezentuje jednym ciągłym bloku kodu natywnego, przechowywane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="c31ab-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c31ab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c31ab-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="c31ab-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c31ab-105">Members</span></span>  
  
|<span data-ttu-id="c31ab-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c31ab-106">Member</span></span>|<span data-ttu-id="c31ab-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c31ab-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="c31ab-108">Adres początkowy ciągłego bloku kodu.</span><span class="sxs-lookup"><span data-stu-id="c31ab-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="c31ab-109">Rozmiar bloku.</span><span class="sxs-lookup"><span data-stu-id="c31ab-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c31ab-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c31ab-110">Requirements</span></span>  
 <span data-ttu-id="c31ab-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c31ab-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c31ab-112">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="c31ab-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="c31ab-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c31ab-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c31ab-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c31ab-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c31ab-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c31ab-115">See also</span></span>
- [<span data-ttu-id="c31ab-116">Profiling — struktury</span><span class="sxs-lookup"><span data-stu-id="c31ab-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)

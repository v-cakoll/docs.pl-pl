---
title: "COR_PRF_CODE_INFO — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_CODE_INFO
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_CODE_INFO
helpviewer_keywords: COR_PRF_CODE_INFO structure [.NET Framework profiling]
ms.assetid: cf30e27c-1f7e-43a2-ba1e-01e4137301db
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 007bb5990ec750dccc678a208d755136ea67a05c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corprfcodeinfo-structure"></a><span data-ttu-id="442a0-102">COR_PRF_CODE_INFO — Struktura</span><span class="sxs-lookup"><span data-stu-id="442a0-102">COR_PRF_CODE_INFO Structure</span></span>
<span data-ttu-id="442a0-103">Reprezentuje jeden ciągły blok kodu natywnego przechowywane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="442a0-103">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="442a0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="442a0-104">Syntax</span></span>  
  
```  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="442a0-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="442a0-105">Members</span></span>  
  
|<span data-ttu-id="442a0-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="442a0-106">Member</span></span>|<span data-ttu-id="442a0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="442a0-107">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="442a0-108">Adres początkowy ciągłego bloku kodu.</span><span class="sxs-lookup"><span data-stu-id="442a0-108">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="442a0-109">Rozmiar bloku.</span><span class="sxs-lookup"><span data-stu-id="442a0-109">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="442a0-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="442a0-110">Requirements</span></span>  
 <span data-ttu-id="442a0-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="442a0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="442a0-112">**Nagłówek:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="442a0-112">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="442a0-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="442a0-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="442a0-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="442a0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="442a0-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="442a0-115">See Also</span></span>  
 [<span data-ttu-id="442a0-116">Struktury profilowania</span><span class="sxs-lookup"><span data-stu-id="442a0-116">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)

---
title: "CLR_DEBUGGING_VERSION — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLR_DEBUGGING_VERSION
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLR_DEBUGGING_VERSION
helpviewer_keywords: CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 98124b7b9efb2c92ebee6b6e99f73edc6cf173a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="clrdebuggingversion-structure"></a><span data-ttu-id="74e99-102">CLR_DEBUGGING_VERSION — Struktura</span><span class="sxs-lookup"><span data-stu-id="74e99-102">CLR_DEBUGGING_VERSION Structure</span></span>
<span data-ttu-id="74e99-103">Określa wersję produktu środowisko uruchomieniowe języka wspólnego (CLR) na potrzeby debugowania.</span><span class="sxs-lookup"><span data-stu-id="74e99-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74e99-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="74e99-104">Syntax</span></span>  
  
```  
Typedef struct _CLR_DEBUGGING_VERSION  
{  
WORD wStructVersion;  
WORD wMajor;   
WORD wMinor;  
WORD wBuild;  
WORD wRevision;  
}  CLR_DEBUGGING_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="74e99-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="74e99-105">Members</span></span>  
  
|<span data-ttu-id="74e99-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="74e99-106">Member</span></span>|<span data-ttu-id="74e99-107">Opis</span><span class="sxs-lookup"><span data-stu-id="74e99-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="74e99-108">Numer wersji struktury</span><span class="sxs-lookup"><span data-stu-id="74e99-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="74e99-109">Główny numer wersji.</span><span class="sxs-lookup"><span data-stu-id="74e99-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="74e99-110">Pomocniczy numer wersji.</span><span class="sxs-lookup"><span data-stu-id="74e99-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="74e99-111">Numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="74e99-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="74e99-112">Numer poprawki.</span><span class="sxs-lookup"><span data-stu-id="74e99-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74e99-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="74e99-113">Remarks</span></span>  
 <span data-ttu-id="74e99-114">`CLR_DEBUGGING_VERSION` Struktura jest taka sama jak cor_version — struktura, jednak, `CLR_DEBUGGING_VERSION` struktura zawiera pola wersji struktury dodatkowe (`wStructVersion`).</span><span class="sxs-lookup"><span data-stu-id="74e99-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="74e99-115">Obecnie to pole musi mieć ustawioną wartość zero.</span><span class="sxs-lookup"><span data-stu-id="74e99-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74e99-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="74e99-116">Requirements</span></span>  
 <span data-ttu-id="74e99-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74e99-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74e99-118">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="74e99-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="74e99-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74e99-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74e99-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74e99-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74e99-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74e99-121">See Also</span></span>  
 [<span data-ttu-id="74e99-122">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="74e99-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="74e99-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="74e99-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

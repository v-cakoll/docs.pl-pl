---
title: "COR_VERSION — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_VERSION
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_VERSION
helpviewer_keywords: COR_VERSION structure [.NET Framework debugging]
ms.assetid: 5efaee1c-a001-4c73-9525-4160f4c71567
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bd4a878b51685befb39eb486097be2e2f2c1d409
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="corversion-structure"></a><span data-ttu-id="8e3cc-102">COR_VERSION — Struktura</span><span class="sxs-lookup"><span data-stu-id="8e3cc-102">COR_VERSION Structure</span></span>
<span data-ttu-id="8e3cc-103">Przechowuje numer wersji czteroczęściową standardowe środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="8e3cc-103">Stores the standard four-part version number of the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e3cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8e3cc-104">Syntax</span></span>  
  
```  
typedef struct _COR_VERSION {  
    DWORD dwMajor;  
    DWORD dwMinor;  
    DWORD dwBuild;  
    DWORD dwSubBuild;  
} COR_VERSION;  
```  
  
## <a name="members"></a><span data-ttu-id="8e3cc-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8e3cc-105">Members</span></span>  
  
|<span data-ttu-id="8e3cc-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8e3cc-106">Member</span></span>|<span data-ttu-id="8e3cc-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8e3cc-107">Description</span></span>|  
|------------|-----------------|  
|`dwMajor`|<span data-ttu-id="8e3cc-108">Główny numer wersji.</span><span class="sxs-lookup"><span data-stu-id="8e3cc-108">The major version number.</span></span>|  
|`dwMinor`|<span data-ttu-id="8e3cc-109">Pomocniczy numer wersji.</span><span class="sxs-lookup"><span data-stu-id="8e3cc-109">The minor version number.</span></span>|  
|`dwBuild`|<span data-ttu-id="8e3cc-110">Numer kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8e3cc-110">The build number.</span></span>|  
|`dwSubBuild`|<span data-ttu-id="8e3cc-111">Numer kompilacji podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="8e3cc-111">The sub-build number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8e3cc-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8e3cc-112">Remarks</span></span>  
 <span data-ttu-id="8e3cc-113">Jeśli numer wersji jest 1.0.3705.288, główny numer wersji jest 1, 0 jest podrzędny numer wersji 3705 jest numer kompilacji i 288 jest numer kompilacji podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="8e3cc-113">If the version number is 1.0.3705.288, 1 is the major version number, 0 is the minor version number, 3705 is the build number, and 288 is the sub-build number.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e3cc-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8e3cc-114">Requirements</span></span>  
 <span data-ttu-id="8e3cc-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8e3cc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e3cc-116">**Nagłówek:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="8e3cc-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="8e3cc-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8e3cc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8e3cc-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e3cc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e3cc-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e3cc-119">See Also</span></span>  
 [<span data-ttu-id="8e3cc-120">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="8e3cc-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="8e3cc-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="8e3cc-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

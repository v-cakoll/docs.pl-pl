---
title: "ASM_NAME — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASM_NAME
api_location: fusion.dll
api_type: COM
f1_keywords: ASM_NAME
helpviewer_keywords: ASM_NAME enumeration [.NET Framework fusion]
ms.assetid: c8b65b19-d777-428f-bc0c-0d84c78a37bc
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 153daddc0a5529d2c1cddc4669c3dbb098ce7bc2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="asmname-enumeration"></a><span data-ttu-id="e8b55-102">ASM_NAME — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="e8b55-102">ASM_NAME Enumeration</span></span>
<span data-ttu-id="e8b55-103">Wskazuje wersję, kompilacji, kultury, sygnatury i tak dalej, zestawu, którego właściwości zostanie pobrać lub ustawić [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e8b55-103">Indicates the version, build, culture, signature, and so on, of the assembly whose properties will be retrieved or set by [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8b55-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8b55-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    ASM_NAME_PUBLIC_KEY = 0,  
    ASM_NAME_PUBLIC_KEY_TOKEN,  
    ASM_NAME_HASH_VALUE,  
    ASM_NAME_NAME,  
    ASM_NAME_MAJOR_VERSION,  
    ASM_NAME_MINOR_VERSION,  
    ASM_NAME_BUILD_NUMBER,  
    ASM_NAME_REVISION_NUMBER,  
    ASM_NAME_CULTURE,  
    ASM_NAME_PROCESSOR_ID_ARRAY,  
    ASM_NAME_OSINFO_ARRAY,  
    ASM_NAME_HASH_ALGID,  
    ASM_NAME_ALIAS,  
    ASM_NAME_CODEBASE_URL,  
    ASM_NAME_CODEBASE_LASTMOD,  
    ASM_NAME_NULL_PUBLIC_KEY,  
    ASM_NAME_NULL_PUBLIC_KEY_TOKEN,  
    ASM_NAME_CUSTOM,  
    ASM_NAME_NULL_CUSTOM,   
    ASM_NAME_MVID,  
    ASM_NAME_FILE_MAJOR_VERSION,  
    ASM_NAME_FILE_MINOR_VERSION,  
    ASM_NAME_FILE_BUILD_NUMBER,  
    ASM_NAME_FILE_REVISION_NUMBER,  
    ASM_NAME_RETARGET,  
    ASM_NAME_SIGNATURE_BLOB,  
    ASM_NAME_CONFIG_MASK,  
    ASM_NAME_ARCHITECTURE,  
    ASM_NAME_MAX_PARAMS  
  
} ASM_NAME;  
```  
  
## <a name="requirements"></a><span data-ttu-id="e8b55-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8b55-105">Requirements</span></span>  
 <span data-ttu-id="e8b55-106">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8b55-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8b55-107">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="e8b55-107">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="e8b55-108">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e8b55-108">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e8b55-109">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8b55-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8b55-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8b55-110">See Also</span></span>  
 [<span data-ttu-id="e8b55-111">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="e8b55-111">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="e8b55-112">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="e8b55-112">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)

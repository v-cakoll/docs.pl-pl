---
title: COUNINITIEE — Wyliczenie
ms.date: 03/30/2017
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dcd7dc7c51caa94308760c0086384c8eea184ee9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443600"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="6e6c2-102">COUNINITIEE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6e6c2-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="6e6c2-103">Określa stałe używane przez [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) podczas inicjowania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="6e6c2-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e6c2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e6c2-104">Syntax</span></span>  
  
```  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="6e6c2-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6e6c2-105">Members</span></span>  
  
|<span data-ttu-id="6e6c2-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6e6c2-106">Member</span></span>|<span data-ttu-id="6e6c2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6e6c2-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="6e6c2-108">Określa domyślny tryb uninitialization.</span><span class="sxs-lookup"><span data-stu-id="6e6c2-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="6e6c2-109">Wskazuje tryb uninitialization wyładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="6e6c2-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6e6c2-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6e6c2-110">Requirements</span></span>  
 <span data-ttu-id="6e6c2-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e6c2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e6c2-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6e6c2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6e6c2-113">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6e6c2-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6e6c2-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e6c2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e6c2-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e6c2-115">See Also</span></span>  
 [<span data-ttu-id="6e6c2-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="6e6c2-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

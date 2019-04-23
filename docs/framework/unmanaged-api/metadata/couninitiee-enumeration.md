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
ms.openlocfilehash: 0cf1bfa03fd14d6324af60781003a8072a267a7e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102950"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="9ba61-102">COUNINITIEE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9ba61-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="9ba61-103">Określa stałe używane przez [couninitializeee —](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) podczas inicjowania środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="9ba61-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ba61-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ba61-104">Syntax</span></span>  
  
```  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="9ba61-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9ba61-105">Members</span></span>  
  
|<span data-ttu-id="9ba61-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="9ba61-106">Member</span></span>|<span data-ttu-id="9ba61-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9ba61-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="9ba61-108">Określa domyślny tryb anulowania inicjowania.</span><span class="sxs-lookup"><span data-stu-id="9ba61-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="9ba61-109">Wskazuje anulowania inicjowania tryb zwalniania zestawów.</span><span class="sxs-lookup"><span data-stu-id="9ba61-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9ba61-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ba61-110">Requirements</span></span>  
 <span data-ttu-id="9ba61-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ba61-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ba61-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="9ba61-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9ba61-113">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9ba61-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9ba61-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ba61-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ba61-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ba61-115">See also</span></span>

- [<span data-ttu-id="9ba61-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="9ba61-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

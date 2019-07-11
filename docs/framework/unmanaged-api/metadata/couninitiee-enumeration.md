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
ms.openlocfilehash: 3d8189365a73e85c0b9f5efb2aa03074385a3fb8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750747"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="3fd87-102">COUNINITIEE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3fd87-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="3fd87-103">Określa stałe używane przez [couninitializeee —](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) podczas inicjowania środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="3fd87-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fd87-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3fd87-104">Syntax</span></span>  
  
```cpp  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="3fd87-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3fd87-105">Members</span></span>  
  
|<span data-ttu-id="3fd87-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="3fd87-106">Member</span></span>|<span data-ttu-id="3fd87-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3fd87-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="3fd87-108">Określa domyślny tryb anulowania inicjowania.</span><span class="sxs-lookup"><span data-stu-id="3fd87-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="3fd87-109">Wskazuje anulowania inicjowania tryb zwalniania zestawów.</span><span class="sxs-lookup"><span data-stu-id="3fd87-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3fd87-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3fd87-110">Requirements</span></span>  
 <span data-ttu-id="3fd87-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fd87-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fd87-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="3fd87-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3fd87-113">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3fd87-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3fd87-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fd87-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd87-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3fd87-115">See also</span></span>

- [<span data-ttu-id="3fd87-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="3fd87-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

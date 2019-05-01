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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045061"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="bf053-102">COUNINITIEE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="bf053-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="bf053-103">Określa stałe używane przez [couninitializeee —](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) podczas inicjowania środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="bf053-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf053-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bf053-104">Syntax</span></span>  
  
```  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="bf053-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="bf053-105">Members</span></span>  
  
|<span data-ttu-id="bf053-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="bf053-106">Member</span></span>|<span data-ttu-id="bf053-107">Opis</span><span class="sxs-lookup"><span data-stu-id="bf053-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="bf053-108">Określa domyślny tryb anulowania inicjowania.</span><span class="sxs-lookup"><span data-stu-id="bf053-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="bf053-109">Wskazuje anulowania inicjowania tryb zwalniania zestawów.</span><span class="sxs-lookup"><span data-stu-id="bf053-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bf053-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf053-110">Requirements</span></span>  
 <span data-ttu-id="bf053-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf053-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf053-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bf053-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bf053-113">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bf053-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bf053-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf053-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf053-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf053-115">See also</span></span>

- [<span data-ttu-id="bf053-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="bf053-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

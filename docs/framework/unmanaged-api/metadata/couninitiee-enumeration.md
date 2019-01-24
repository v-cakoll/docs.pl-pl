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
ms.openlocfilehash: 475ae98d2bf7ea5132c9ec4555070f8bb2999cde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744014"
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="f68bd-102">COUNINITIEE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f68bd-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="f68bd-103">Określa stałe używane przez [couninitializeee —](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) podczas inicjowania środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="f68bd-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f68bd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f68bd-104">Syntax</span></span>  
  
```  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="f68bd-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f68bd-105">Members</span></span>  
  
|<span data-ttu-id="f68bd-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f68bd-106">Member</span></span>|<span data-ttu-id="f68bd-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f68bd-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="f68bd-108">Określa domyślny tryb anulowania inicjowania.</span><span class="sxs-lookup"><span data-stu-id="f68bd-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="f68bd-109">Wskazuje anulowania inicjowania tryb zwalniania zestawów.</span><span class="sxs-lookup"><span data-stu-id="f68bd-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f68bd-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f68bd-110">Requirements</span></span>  
 <span data-ttu-id="f68bd-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f68bd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f68bd-112">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f68bd-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f68bd-113">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f68bd-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f68bd-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f68bd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f68bd-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f68bd-115">See also</span></span>
- [<span data-ttu-id="f68bd-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="f68bd-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

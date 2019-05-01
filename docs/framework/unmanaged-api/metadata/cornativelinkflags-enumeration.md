---
title: CorNativeLinkFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e6eb2a30dd6722309fd80c1611ad9200ab14ae5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045452"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="8ed06-102">CorNativeLinkFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8ed06-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="8ed06-103">Udostępnia wartości flagi używane przez konsolidator, podczas łączenia kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="8ed06-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ed06-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ed06-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="8ed06-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8ed06-105">Members</span></span>  
  
|<span data-ttu-id="8ed06-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8ed06-106">Member</span></span>|<span data-ttu-id="8ed06-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8ed06-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="8ed06-108">Wskazuje nie flagi.</span><span class="sxs-lookup"><span data-stu-id="8ed06-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="8ed06-109">Wskazuje `setLastError` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="8ed06-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="8ed06-110">Wskazuje `nomangle` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="8ed06-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="8ed06-111">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="8ed06-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8ed06-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8ed06-112">Requirements</span></span>  
 <span data-ttu-id="8ed06-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ed06-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ed06-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="8ed06-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ed06-115">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8ed06-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8ed06-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ed06-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ed06-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ed06-117">See also</span></span>

- [<span data-ttu-id="8ed06-118">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="8ed06-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

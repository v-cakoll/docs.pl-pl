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
ms.openlocfilehash: 6be71878ba354ebe53b4b8b9b40db3222ec828f3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781734"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="f965b-102">CorNativeLinkFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f965b-102">CorNativeLinkFlags Enumeration</span></span>
<span data-ttu-id="f965b-103">Udostępnia wartości flagi używane przez konsolidator, podczas łączenia kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="f965b-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f965b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f965b-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="f965b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f965b-105">Members</span></span>  
  
|<span data-ttu-id="f965b-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f965b-106">Member</span></span>|<span data-ttu-id="f965b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f965b-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="f965b-108">Wskazuje nie flagi.</span><span class="sxs-lookup"><span data-stu-id="f965b-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="f965b-109">Wskazuje `setLastError` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="f965b-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="f965b-110">Wskazuje `nomangle` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="f965b-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="f965b-111">Nie używany.</span><span class="sxs-lookup"><span data-stu-id="f965b-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f965b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f965b-112">Requirements</span></span>  
 <span data-ttu-id="f965b-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f965b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f965b-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="f965b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f965b-115">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f965b-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f965b-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f965b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f965b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f965b-117">See also</span></span>

- [<span data-ttu-id="f965b-118">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="f965b-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

---
title: CorSaveSize — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSaveSize
helpviewer_keywords:
- CorSaveSize enumeration [.NET Framework metadata]
ms.assetid: eb95ce39-5688-43c1-a34d-578794b32faa
topic_type:
- apiref
ms.openlocfilehash: 22a7f87a5803dc185052a5ce7ed427eff9f8fb18
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009187"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="1b1ed-102">CorSaveSize — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1b1ed-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="1b1ed-103">Zawiera wartości wskazujące poziom dokładności wymagany podczas wykonywania zapytania o rozmiar operacji zapisywania.</span><span class="sxs-lookup"><span data-stu-id="1b1ed-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b1ed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b1ed-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,
    cssQuick                   = 0x0001,
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="1b1ed-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1b1ed-105">Members</span></span>  
  
|<span data-ttu-id="1b1ed-106">Członek</span><span class="sxs-lookup"><span data-stu-id="1b1ed-106">Member</span></span>|<span data-ttu-id="1b1ed-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1b1ed-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="1b1ed-108">Określa, że wartość zwracana powinna być dokładna.</span><span class="sxs-lookup"><span data-stu-id="1b1ed-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="1b1ed-109">Określa, że należy oszacować wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="1b1ed-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="1b1ed-110">Określa, że typy, które mają być odrzucane, powinny być usuwane.</span><span class="sxs-lookup"><span data-stu-id="1b1ed-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1b1ed-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1b1ed-111">Requirements</span></span>  
 <span data-ttu-id="1b1ed-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b1ed-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b1ed-113">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="1b1ed-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="1b1ed-114">**Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1b1ed-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1b1ed-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b1ed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b1ed-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b1ed-116">See also</span></span>

- [<span data-ttu-id="1b1ed-117">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="1b1ed-117">Metadata Enumerations</span></span>](metadata-enumerations.md)

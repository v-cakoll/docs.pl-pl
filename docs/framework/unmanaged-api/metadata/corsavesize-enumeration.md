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
ms.openlocfilehash: 13a4364244f7d0076d77d14c3e3ef161e3872bcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176139"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="00e94-102">CorSaveSize — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="00e94-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="00e94-103">Zawiera wartości wskazujące poziom precyzji wymagany podczas wykonywania zapytań o rozmiar operacji zapisywania.</span><span class="sxs-lookup"><span data-stu-id="00e94-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00e94-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00e94-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,
    cssQuick                   = 0x0001,
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="00e94-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="00e94-105">Members</span></span>  
  
|<span data-ttu-id="00e94-106">Członek</span><span class="sxs-lookup"><span data-stu-id="00e94-106">Member</span></span>|<span data-ttu-id="00e94-107">Opis</span><span class="sxs-lookup"><span data-stu-id="00e94-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="00e94-108">Określa, że wartość zwracana powinna być dokładna.</span><span class="sxs-lookup"><span data-stu-id="00e94-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="00e94-109">Określa, że wartość zwracana powinna być szacowana.</span><span class="sxs-lookup"><span data-stu-id="00e94-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="00e94-110">Określa, że typy podlegające odrzuceniu powinny zostać usunięte.</span><span class="sxs-lookup"><span data-stu-id="00e94-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00e94-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00e94-111">Requirements</span></span>  
 <span data-ttu-id="00e94-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00e94-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00e94-113">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="00e94-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="00e94-114">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00e94-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="00e94-115">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00e94-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00e94-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00e94-116">See also</span></span>

- [<span data-ttu-id="00e94-117">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="00e94-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

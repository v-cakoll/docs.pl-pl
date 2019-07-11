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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c1e7bbac17d9a9ae191a5ad6d69b52a806383562
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781599"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="a01e8-102">CorSaveSize — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a01e8-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="a01e8-103">Zawiera wartości wskazujące poziom precyzji wymagany podczas wykonywania zapytania dla rozmiaru zapisywania operacji.</span><span class="sxs-lookup"><span data-stu-id="a01e8-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a01e8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a01e8-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="a01e8-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a01e8-105">Members</span></span>  
  
|<span data-ttu-id="a01e8-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a01e8-106">Member</span></span>|<span data-ttu-id="a01e8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a01e8-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="a01e8-108">Określa, że zwracana wartość powinna być dokładna.</span><span class="sxs-lookup"><span data-stu-id="a01e8-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="a01e8-109">Określa, że należy obliczyć wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="a01e8-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="a01e8-110">Określa, czy typy discardable powinny zostać usunięte.</span><span class="sxs-lookup"><span data-stu-id="a01e8-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a01e8-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a01e8-111">Requirements</span></span>  
 <span data-ttu-id="a01e8-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a01e8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a01e8-113">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a01e8-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a01e8-114">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a01e8-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a01e8-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a01e8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a01e8-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a01e8-116">See also</span></span>

- [<span data-ttu-id="a01e8-117">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="a01e8-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

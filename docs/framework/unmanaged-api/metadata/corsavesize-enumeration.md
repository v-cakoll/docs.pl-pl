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
ms.openlocfilehash: 66f9f95b0cf19acb677daf7f7401d21cc81864a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447610"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="8d276-102">CorSaveSize — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8d276-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="8d276-103">Zawiera wartość wskazującą poziom dokładności wymagane podczas wykonywania zapytania dotyczącego rozmiar zapisywania operacji.</span><span class="sxs-lookup"><span data-stu-id="8d276-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d276-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d276-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="8d276-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8d276-105">Members</span></span>  
  
|<span data-ttu-id="8d276-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8d276-106">Member</span></span>|<span data-ttu-id="8d276-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8d276-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="8d276-108">Określa, że wartość zwracana powinna być dokładnie.</span><span class="sxs-lookup"><span data-stu-id="8d276-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="8d276-109">Określa, czy należy obliczyć wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="8d276-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="8d276-110">Określa, czy typy discardable powinna zostać usunięta.</span><span class="sxs-lookup"><span data-stu-id="8d276-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8d276-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8d276-111">Requirements</span></span>  
 <span data-ttu-id="8d276-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d276-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d276-113">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="8d276-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="8d276-114">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8d276-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8d276-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d276-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d276-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d276-116">See Also</span></span>  
 [<span data-ttu-id="8d276-117">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="8d276-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

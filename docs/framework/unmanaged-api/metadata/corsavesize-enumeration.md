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
ms.openlocfilehash: bc36468a2016822e884ec3a36a23c75477a00a2d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045386"
---
# <a name="corsavesize-enumeration"></a><span data-ttu-id="b6631-102">CorSaveSize — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b6631-102">CorSaveSize Enumeration</span></span>
<span data-ttu-id="b6631-103">Zawiera wartości wskazujące poziom precyzji wymagany podczas wykonywania zapytania dla rozmiaru zapisywania operacji.</span><span class="sxs-lookup"><span data-stu-id="b6631-103">Contains values indicating the level of precision required when querying for the size of a save operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6631-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6631-104">Syntax</span></span>  
  
```  
typedef enum CorSaveSize {  
    cssAccurate                = 0x0000,   
    cssQuick                   = 0x0001,   
    cssDiscardTransientCAs     = 0x0002  
} CorSaveSize;  
```  
  
## <a name="members"></a><span data-ttu-id="b6631-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b6631-105">Members</span></span>  
  
|<span data-ttu-id="b6631-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b6631-106">Member</span></span>|<span data-ttu-id="b6631-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b6631-107">Description</span></span>|  
|------------|-----------------|  
|`cssAccurate`|<span data-ttu-id="b6631-108">Określa, że zwracana wartość powinna być dokładna.</span><span class="sxs-lookup"><span data-stu-id="b6631-108">Specifies that the return value should be exact.</span></span>|  
|`cssQuick`|<span data-ttu-id="b6631-109">Określa, że należy obliczyć wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="b6631-109">Specifies that the return value should be estimated.</span></span>|  
|`cssDiscardTransientCAs`|<span data-ttu-id="b6631-110">Określa, czy typy discardable powinny zostać usunięte.</span><span class="sxs-lookup"><span data-stu-id="b6631-110">Specifies that discardable types should be removed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b6631-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b6631-111">Requirements</span></span>  
 <span data-ttu-id="b6631-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6631-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6631-113">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b6631-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b6631-114">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b6631-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6631-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6631-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6631-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6631-116">See also</span></span>

- [<span data-ttu-id="b6631-117">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="b6631-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

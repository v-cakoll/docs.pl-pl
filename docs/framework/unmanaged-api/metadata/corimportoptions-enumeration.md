---
title: CorImportOptions — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2f71a277484adbbfe3628222c635528cdab03e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156133"
---
# <a name="corimportoptions-enumeration"></a><span data-ttu-id="b1cc9-102">CorImportOptions — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b1cc9-102">CorImportOptions Enumeration</span></span>
<span data-ttu-id="b1cc9-103">Zawiera wartości flagi, które kontrolują zachowanie podczas Importowanie zestawu poza bieżącym zakresem.</span><span class="sxs-lookup"><span data-stu-id="b1cc9-103">Contains flag values that control the behavior during importation of an assembly outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1cc9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1cc9-104">Syntax</span></span>  
  
```  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="b1cc9-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b1cc9-105">Members</span></span>  
  
|<span data-ttu-id="b1cc9-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b1cc9-106">Member</span></span>|<span data-ttu-id="b1cc9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b1cc9-107">Description</span></span>|  
|------------|-----------------|  
|`MDImportOptionDefault`|<span data-ttu-id="b1cc9-108">Wskazuje zachowanie domyślne, czyli aby pominąć usuniętych rekordów.</span><span class="sxs-lookup"><span data-stu-id="b1cc9-108">Indicates the default behavior, which is to skip deleted records.</span></span>|  
|`MDImportOptionAll`|<span data-ttu-id="b1cc9-109">Wskazuje, że można wyliczyć wszystkie metadane.</span><span class="sxs-lookup"><span data-stu-id="b1cc9-109">Indicates that all metadata should be enumerated.</span></span>|  
|`MDImportOptionAllTypeDefs`|<span data-ttu-id="b1cc9-110">Wskazuje, że można wyliczyć wszystkie definicje typów, w tym usuniętych.</span><span class="sxs-lookup"><span data-stu-id="b1cc9-110">Indicates that all TypeDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllMethodDefs`|<span data-ttu-id="b1cc9-111">Wskazuje, że można wyliczyć wszystkie MethodDefs, w tym usuniętych.</span><span class="sxs-lookup"><span data-stu-id="b1cc9-111">Indicates that all MethodDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllFieldDefs`|<span data-ttu-id="b1cc9-112">Wskazuje, że można wyliczyć wszystkie FieldDefs, w tym usuniętych.</span><span class="sxs-lookup"><span data-stu-id="b1cc9-112">Indicates that all FieldDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllProperties`|<span data-ttu-id="b1cc9-113">Wskazuje, że można wyliczyć wszystkie PropertyDefs, w tym usuniętych.</span><span class="sxs-lookup"><span data-stu-id="b1cc9-113">Indicates that all PropertyDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllEvents`|<span data-ttu-id="b1cc9-114">Wskazuje, że można wyliczyć wszystkie EventDefs, w tym usuniętych.</span><span class="sxs-lookup"><span data-stu-id="b1cc9-114">Indicates that all EventDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllCustomAttributes`|<span data-ttu-id="b1cc9-115">Wskazuje, że można wyliczyć wszystkich atrybutów niestandardowych, w tym usuniętych.</span><span class="sxs-lookup"><span data-stu-id="b1cc9-115">Indicates that all custom attributes, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllExportedTypes`|<span data-ttu-id="b1cc9-116">Wskazuje, że można wyliczyć wszystkich typów eksportowanych, w tym usuniętych z nich.</span><span class="sxs-lookup"><span data-stu-id="b1cc9-116">Indicates that all exported types, including deleted ones, should be enumerated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b1cc9-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1cc9-117">Requirements</span></span>  
 <span data-ttu-id="b1cc9-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1cc9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1cc9-119">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b1cc9-119">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="b1cc9-120">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b1cc9-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b1cc9-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1cc9-121">See also</span></span>

- [<span data-ttu-id="b1cc9-122">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="b1cc9-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

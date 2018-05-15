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
ms.openlocfilehash: 7078b2eb98c15b7229132076da8af4691032bb08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corimportoptions-enumeration"></a><span data-ttu-id="9896c-102">CorImportOptions — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9896c-102">CorImportOptions Enumeration</span></span>
<span data-ttu-id="9896c-103">Zawiera wartości flagi, które kontrolują zachowanie podczas Import zestawu spoza zakresu.</span><span class="sxs-lookup"><span data-stu-id="9896c-103">Contains flag values that control the behavior during importation of an assembly outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9896c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9896c-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="9896c-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9896c-105">Members</span></span>  
  
|<span data-ttu-id="9896c-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="9896c-106">Member</span></span>|<span data-ttu-id="9896c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9896c-107">Description</span></span>|  
|------------|-----------------|  
|`MDImportOptionDefault`|<span data-ttu-id="9896c-108">Wskazuje zachowanie domyślne, które mają pominąć usuniętych rekordów.</span><span class="sxs-lookup"><span data-stu-id="9896c-108">Indicates the default behavior, which is to skip deleted records.</span></span>|  
|`MDImportOptionAll`|<span data-ttu-id="9896c-109">Wskazuje, że można wyliczyć wszystkich metadanych.</span><span class="sxs-lookup"><span data-stu-id="9896c-109">Indicates that all metadata should be enumerated.</span></span>|  
|`MDImportOptionAllTypeDefs`|<span data-ttu-id="9896c-110">Wskazuje, czy wszystkie definicje typów, w tym usunięto te należy wyliczyć.</span><span class="sxs-lookup"><span data-stu-id="9896c-110">Indicates that all TypeDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllMethodDefs`|<span data-ttu-id="9896c-111">Wskazuje, że można wyliczyć wszystkich MethodDefs, w tym tych usuniętych.</span><span class="sxs-lookup"><span data-stu-id="9896c-111">Indicates that all MethodDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllFieldDefs`|<span data-ttu-id="9896c-112">Wskazuje, że można wyliczyć wszystkich FieldDefs, w tym tych usuniętych.</span><span class="sxs-lookup"><span data-stu-id="9896c-112">Indicates that all FieldDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllProperties`|<span data-ttu-id="9896c-113">Wskazuje, że można wyliczyć wszystkich PropertyDefs, w tym tych usuniętych.</span><span class="sxs-lookup"><span data-stu-id="9896c-113">Indicates that all PropertyDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllEvents`|<span data-ttu-id="9896c-114">Wskazuje, że można wyliczyć wszystkich EventDefs, w tym tych usuniętych.</span><span class="sxs-lookup"><span data-stu-id="9896c-114">Indicates that all EventDefs, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllCustomAttributes`|<span data-ttu-id="9896c-115">Wskazuje, że można wyliczyć wszystkich atrybutów niestandardowych, w tym usunięto te.</span><span class="sxs-lookup"><span data-stu-id="9896c-115">Indicates that all custom attributes, including deleted ones, should be enumerated.</span></span>|  
|`MDImportOptionAllExportedTypes`|<span data-ttu-id="9896c-116">Wskazuje, czy można wyliczyć wszystkich typów wyeksportowany, w tym tych usuniętych.</span><span class="sxs-lookup"><span data-stu-id="9896c-116">Indicates that all exported types, including deleted ones, should be enumerated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9896c-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9896c-117">Requirements</span></span>  
 <span data-ttu-id="9896c-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9896c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9896c-119">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="9896c-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9896c-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9896c-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9896c-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9896c-121">See Also</span></span>  
 [<span data-ttu-id="9896c-122">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="9896c-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

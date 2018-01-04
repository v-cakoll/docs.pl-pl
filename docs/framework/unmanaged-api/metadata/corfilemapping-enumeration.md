---
title: "CorFileMapping — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorFileMapping
api_location: mscoree.dll
api_type: COM
f1_keywords: CorFileMapping
helpviewer_keywords: CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5abde0d34baecf12628c9c6c99f04d6d81dd62fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corfilemapping-enumeration"></a><span data-ttu-id="00e8f-102">CorFileMapping — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="00e8f-102">CorFileMapping Enumeration</span></span>
<span data-ttu-id="00e8f-103">Zawiera wartości, które opisują typ mapowania pliku, która jest zwracana w wyniku wywołania [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="00e8f-103">Contains values that describe the type of file mapping that is returned from a call to the [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00e8f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00e8f-104">Syntax</span></span>  
  
```  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="00e8f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="00e8f-105">Members</span></span>  
  
|<span data-ttu-id="00e8f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="00e8f-106">Member</span></span>|<span data-ttu-id="00e8f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="00e8f-107">Description</span></span>|  
|------------|-----------------|  
|`fmFlat`|<span data-ttu-id="00e8f-108">Plik jest mapowany jako plik danych.</span><span class="sxs-lookup"><span data-stu-id="00e8f-108">The file is mapped as a data file.</span></span> <span data-ttu-id="00e8f-109">Oznacza to `SEC_IMAGE` flagi nie został przekazany do Microsoft Win32 `CreateFileMapping` funkcji.</span><span class="sxs-lookup"><span data-stu-id="00e8f-109">That is, the `SEC_IMAGE` flag was not passed to the Microsoft Win32 `CreateFileMapping` function.</span></span>|  
|`fmExecutableImage`|<span data-ttu-id="00e8f-110">Plik jest zamapowana do wykonania, za pomocą `LoadLibrary` funkcji lub `CreateFileMapping` działać z `SEC_IMAGE` flagi.</span><span class="sxs-lookup"><span data-stu-id="00e8f-110">The file is mapped for execution, by using either the `LoadLibrary` function or the `CreateFileMapping` function with the `SEC_IMAGE` flag.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00e8f-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00e8f-111">Requirements</span></span>  
 <span data-ttu-id="00e8f-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00e8f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00e8f-113">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="00e8f-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="00e8f-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00e8f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00e8f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00e8f-115">See Also</span></span>  
 [<span data-ttu-id="00e8f-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="00e8f-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="00e8f-117">GetFileMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="00e8f-117">GetFileMapping Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)

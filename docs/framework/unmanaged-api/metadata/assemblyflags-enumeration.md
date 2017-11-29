---
title: "AssemblyFlags — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: AssemblyFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: AssemblyFlags
helpviewer_keywords: AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 91760b6d16b663257bf3d89915da3bd88b3411bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="3181f-102">AssemblyFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3181f-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="3181f-103">Zawiera wartości, które opisano funkcje wykonawcze języka zestawu.</span><span class="sxs-lookup"><span data-stu-id="3181f-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3181f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3181f-104">Syntax</span></span>  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="3181f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3181f-105">Members</span></span>  
  
|<span data-ttu-id="3181f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="3181f-106">Member</span></span>|<span data-ttu-id="3181f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3181f-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="3181f-108">Określa, że definicje wyeksportowanego typu niejawnych plików wchodzących w skład zestawu.</span><span class="sxs-lookup"><span data-stu-id="3181f-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="3181f-109">W wersje programu .NET Framework 1.0 i 1.1 Ta wartość jest zawsze przyjęto, należy ustawić wartość.</span><span class="sxs-lookup"><span data-stu-id="3181f-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="3181f-110">Określa, że niejawnych plików wchodzących w skład zestawu definicji zasobu.</span><span class="sxs-lookup"><span data-stu-id="3181f-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="3181f-111">W .NET Framework 1.0 i 1.1 Ta wartość jest zawsze przyjęto, należy ustawić wartość.</span><span class="sxs-lookup"><span data-stu-id="3181f-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="3181f-112">Określa, że zestaw nie można wykonać z innymi wersjami, jeśli działają w tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3181f-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="3181f-113">Określa, że zestaw nie można wykonać z innymi wersjami, jeśli są na nich uruchomione w tym samym procesie.</span><span class="sxs-lookup"><span data-stu-id="3181f-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="3181f-114">Określa, że zestaw nie można wykonać z innymi wersjami, jeśli są na nich uruchomione na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="3181f-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3181f-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3181f-115">Remarks</span></span>  
 <span data-ttu-id="3181f-116">Wartości między 0x0010 i 0x0070 włącznie, służą do opisywania funkcje zgodności side-by-side przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3181f-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="3181f-117">Jeśli żadna z tych wartości, zestaw zakłada się, że side-by-side zgodny.</span><span class="sxs-lookup"><span data-stu-id="3181f-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3181f-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3181f-118">Requirements</span></span>  
 <span data-ttu-id="3181f-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3181f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3181f-120">**Nagłówek:** MsCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3181f-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="3181f-121">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3181f-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3181f-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3181f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3181f-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3181f-123">See Also</span></span>  
 [<span data-ttu-id="3181f-124">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="3181f-124">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="3181f-125">IMetaDataAssemblyEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="3181f-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

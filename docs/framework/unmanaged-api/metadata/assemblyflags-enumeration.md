---
title: AssemblyFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fc6d08e960b0ba82c76945a318ec723546f71b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444909"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="8fc51-102">AssemblyFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8fc51-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="8fc51-103">Zawiera wartości, które opisano funkcje wykonawcze języka zestawu.</span><span class="sxs-lookup"><span data-stu-id="8fc51-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fc51-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8fc51-104">Syntax</span></span>  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="8fc51-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8fc51-105">Members</span></span>  
  
|<span data-ttu-id="8fc51-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="8fc51-106">Member</span></span>|<span data-ttu-id="8fc51-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8fc51-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="8fc51-108">Określa, że definicje wyeksportowanego typu niejawnych plików wchodzących w skład zestawu.</span><span class="sxs-lookup"><span data-stu-id="8fc51-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="8fc51-109">W wersje programu .NET Framework 1.0 i 1.1 Ta wartość jest zawsze przyjęto, należy ustawić wartość.</span><span class="sxs-lookup"><span data-stu-id="8fc51-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="8fc51-110">Określa, że niejawnych plików wchodzących w skład zestawu definicji zasobu.</span><span class="sxs-lookup"><span data-stu-id="8fc51-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="8fc51-111">W .NET Framework 1.0 i 1.1 Ta wartość jest zawsze przyjęto, należy ustawić wartość.</span><span class="sxs-lookup"><span data-stu-id="8fc51-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="8fc51-112">Określa, że zestaw nie można wykonać z innymi wersjami, jeśli działają w tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8fc51-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="8fc51-113">Określa, że zestaw nie można wykonać z innymi wersjami, jeśli są na nich uruchomione w tym samym procesie.</span><span class="sxs-lookup"><span data-stu-id="8fc51-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="8fc51-114">Określa, że zestaw nie można wykonać z innymi wersjami, jeśli są na nich uruchomione na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="8fc51-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fc51-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8fc51-115">Remarks</span></span>  
 <span data-ttu-id="8fc51-116">Wartości między 0x0010 i 0x0070 włącznie, służą do opisywania funkcje zgodności side-by-side przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="8fc51-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="8fc51-117">Jeśli żadna z tych wartości, zestaw zakłada się, że side-by-side zgodny.</span><span class="sxs-lookup"><span data-stu-id="8fc51-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fc51-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8fc51-118">Requirements</span></span>  
 <span data-ttu-id="8fc51-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fc51-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fc51-120">**Nagłówek:** MsCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8fc51-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="8fc51-121">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8fc51-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8fc51-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fc51-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fc51-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8fc51-123">See Also</span></span>  
 [<span data-ttu-id="8fc51-124">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="8fc51-124">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [<span data-ttu-id="8fc51-125">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="8fc51-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

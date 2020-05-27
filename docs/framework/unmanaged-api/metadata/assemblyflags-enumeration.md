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
ms.openlocfilehash: 1cb84b94b37a2e9e8dd4d20d09cbca82db290c0f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009458"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="635e4-102">AssemblyFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="635e4-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="635e4-103">Zawiera wartości opisujące funkcje czasu wykonywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="635e4-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="635e4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="635e4-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="635e4-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="635e4-105">Members</span></span>  
  
|<span data-ttu-id="635e4-106">Członek</span><span class="sxs-lookup"><span data-stu-id="635e4-106">Member</span></span>|<span data-ttu-id="635e4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="635e4-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="635e4-108">Określa, że eksportowane definicje typów są niejawne w obrębie plików wchodzących w skład zestawu.</span><span class="sxs-lookup"><span data-stu-id="635e4-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="635e4-109">W .NET Framework wersje 1,0 i 1,1 Ta wartość jest zawsze ustawiana jako ustawiona.</span><span class="sxs-lookup"><span data-stu-id="635e4-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="635e4-110">Określa, że definicje zasobów są niejawne w obrębie plików wchodzących w skład zestawu.</span><span class="sxs-lookup"><span data-stu-id="635e4-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="635e4-111">W .NET Framework 1,0 i 1,1 Ta wartość jest zawsze przyjmowana jako ustawiona.</span><span class="sxs-lookup"><span data-stu-id="635e4-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="635e4-112">Określa, że zestaw nie może być wykonywany z innymi wersjami, jeśli są uruchomione w tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="635e4-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="635e4-113">Określa, że zestaw nie może być wykonywany z innymi wersjami, jeśli są uruchomione w tym samym procesie.</span><span class="sxs-lookup"><span data-stu-id="635e4-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="635e4-114">Określa, że zestaw nie może być wykonywany z innymi wersjami, jeśli są uruchomione na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="635e4-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="635e4-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="635e4-115">Remarks</span></span>  
 <span data-ttu-id="635e4-116">Wartości między 0x0010 i 0x0070, włącznie, służą do opisywania funkcji zgodności Side-by-Side w przywoływanym zestawie.</span><span class="sxs-lookup"><span data-stu-id="635e4-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="635e4-117">Jeśli żadna z tych wartości nie zostanie ustawiona, przyjmuje się, że zestaw jest zgodny ze sobą.</span><span class="sxs-lookup"><span data-stu-id="635e4-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="635e4-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="635e4-118">Requirements</span></span>  
 <span data-ttu-id="635e4-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="635e4-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="635e4-120">**Nagłówek:** MsCorEE. h</span><span class="sxs-lookup"><span data-stu-id="635e4-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="635e4-121">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="635e4-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="635e4-122">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="635e4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="635e4-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="635e4-123">See also</span></span>

- [<span data-ttu-id="635e4-124">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="635e4-124">Metadata Enumerations</span></span>](metadata-enumerations.md)
- [<span data-ttu-id="635e4-125">IMetaDataAssemblyEmit — Interfejs</span><span class="sxs-lookup"><span data-stu-id="635e4-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)

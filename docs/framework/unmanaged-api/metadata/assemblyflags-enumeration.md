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
ms.openlocfilehash: 7c86a4fd2788c8ea2df5d9e54c5c221afd179704
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091424"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="a7eaf-102">AssemblyFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a7eaf-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="a7eaf-103">Zawiera wartości, które opisują zestawu funkcji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a7eaf-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7eaf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7eaf-104">Syntax</span></span>  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="a7eaf-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a7eaf-105">Members</span></span>  
  
|<span data-ttu-id="a7eaf-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a7eaf-106">Member</span></span>|<span data-ttu-id="a7eaf-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eaf-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="a7eaf-108">Określa, czy niejawne w ramach plików, wchodzące w skład zestawu definicji eksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="a7eaf-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="a7eaf-109">W .NET Framework w wersji 1.0 i 1.1 Ta wartość jest zawsze zakłada się, że można ustawić.</span><span class="sxs-lookup"><span data-stu-id="a7eaf-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="a7eaf-110">Określa, że definicje są niejawne w ramach plików, wchodzące w skład zestawu.</span><span class="sxs-lookup"><span data-stu-id="a7eaf-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="a7eaf-111">W .NET Framework 1.0 i 1.1 Ta wartość jest zawsze zakłada się, że można ustawić.</span><span class="sxs-lookup"><span data-stu-id="a7eaf-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="a7eaf-112">Określa, że zestaw nie można wykonać z innymi wersjami, jeśli są uruchomione w tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a7eaf-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="a7eaf-113">Określa, że zestaw nie można wykonać z innymi wersjami, jeśli są uruchomione w tym samym procesie.</span><span class="sxs-lookup"><span data-stu-id="a7eaf-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="a7eaf-114">Określa, że zestaw nie można wykonać z innymi wersjami, jeśli są uruchomione na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a7eaf-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7eaf-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7eaf-115">Remarks</span></span>  
 <span data-ttu-id="a7eaf-116">Wartości między 0x0010 i 0x0070 włącznie, są używane do opisywania funkcje zgodności side-by-side przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="a7eaf-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="a7eaf-117">Jeśli żadna z tych wartości są ustawione, zestaw zakłada się, że zgodne side-by-side.</span><span class="sxs-lookup"><span data-stu-id="a7eaf-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7eaf-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a7eaf-118">Requirements</span></span>  
 <span data-ttu-id="a7eaf-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7eaf-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7eaf-120">**Nagłówek:** MsCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a7eaf-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="a7eaf-121">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7eaf-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a7eaf-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7eaf-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7eaf-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7eaf-123">See also</span></span>

- [<span data-ttu-id="a7eaf-124">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="a7eaf-124">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="a7eaf-125">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="a7eaf-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

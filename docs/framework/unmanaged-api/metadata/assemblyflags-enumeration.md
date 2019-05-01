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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905999"
---
# <a name="assemblyflags-enumeration"></a><span data-ttu-id="88c17-102">AssemblyFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="88c17-102">AssemblyFlags Enumeration</span></span>
<span data-ttu-id="88c17-103">Zawiera wartości, które opisują zestawu funkcji środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="88c17-103">Contains values that describe run-time features of an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88c17-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="88c17-104">Syntax</span></span>  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="88c17-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="88c17-105">Members</span></span>  
  
|<span data-ttu-id="88c17-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="88c17-106">Member</span></span>|<span data-ttu-id="88c17-107">Opis</span><span class="sxs-lookup"><span data-stu-id="88c17-107">Description</span></span>|  
|------------|-----------------|  
|`afImplicitExportedTypes`|<span data-ttu-id="88c17-108">Określa, czy niejawne w ramach plików, wchodzące w skład zestawu definicji eksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="88c17-108">Specifies that exported type definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="88c17-109">W .NET Framework w wersji 1.0 i 1.1 Ta wartość jest zawsze zakłada się, że można ustawić.</span><span class="sxs-lookup"><span data-stu-id="88c17-109">In the .NET Framework versions 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afImplicitResources`|<span data-ttu-id="88c17-110">Określa, że definicje są niejawne w ramach plików, wchodzące w skład zestawu.</span><span class="sxs-lookup"><span data-stu-id="88c17-110">Specifies that resource definitions are implicit within the files that comprise the assembly.</span></span> <span data-ttu-id="88c17-111">W .NET Framework 1.0 i 1.1 Ta wartość jest zawsze zakłada się, że można ustawić.</span><span class="sxs-lookup"><span data-stu-id="88c17-111">In the .NET Framework 1.0 and 1.1, this value is always assumed to be set.</span></span>|  
|`afNonSideBySideAppDomain`|<span data-ttu-id="88c17-112">Określa, że zestaw nie można wykonać z innymi wersjami, jeśli są uruchomione w tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="88c17-112">Specifies that the assembly cannot execute with other versions if they are running in the same application domain.</span></span>|  
|`afNonSideBySideProcess`|<span data-ttu-id="88c17-113">Określa, że zestaw nie można wykonać z innymi wersjami, jeśli są uruchomione w tym samym procesie.</span><span class="sxs-lookup"><span data-stu-id="88c17-113">Specifies that the assembly cannot execute with other versions if they are running in the same process.</span></span>|  
|`afNonSideBySideMachine`|<span data-ttu-id="88c17-114">Określa, że zestaw nie można wykonać z innymi wersjami, jeśli są uruchomione na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="88c17-114">Specifies that the assembly cannot execute with other versions if they are running on the same computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88c17-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88c17-115">Remarks</span></span>  
 <span data-ttu-id="88c17-116">Wartości między 0x0010 i 0x0070 włącznie, są używane do opisywania funkcje zgodności side-by-side przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="88c17-116">The values between 0x0010 and 0x0070, inclusive, are used to describe side-by-side compatibility features of the referenced assembly.</span></span> <span data-ttu-id="88c17-117">Jeśli żadna z tych wartości są ustawione, zestaw zakłada się, że zgodne side-by-side.</span><span class="sxs-lookup"><span data-stu-id="88c17-117">If none of these values are set, the assembly is assumed to be side-by-side compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88c17-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88c17-118">Requirements</span></span>  
 <span data-ttu-id="88c17-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88c17-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88c17-120">**Nagłówek:** MsCorEE.h</span><span class="sxs-lookup"><span data-stu-id="88c17-120">**Header:** MsCorEE.h</span></span>  
  
 <span data-ttu-id="88c17-121">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="88c17-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="88c17-122">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88c17-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88c17-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88c17-123">See also</span></span>

- [<span data-ttu-id="88c17-124">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="88c17-124">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="88c17-125">IMetaDataAssemblyEmit, interfejs</span><span class="sxs-lookup"><span data-stu-id="88c17-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)

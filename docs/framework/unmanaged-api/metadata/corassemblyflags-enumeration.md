---
title: CorAssemblyFlags — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
ms.openlocfilehash: b1a83f07f03ddb17d5c306453cf838101a77ed65
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007939"
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="59da3-102">CorAssemblyFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="59da3-102">CorAssemblyFlags Enumeration</span></span>
<span data-ttu-id="59da3-103">Zawiera wartości opisujące metadane zastosowane do kompilacji zestawu.</span><span class="sxs-lookup"><span data-stu-id="59da3-103">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59da3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="59da3-104">Syntax</span></span>  
  
```cpp  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="59da3-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="59da3-105">Members</span></span>  
  
|<span data-ttu-id="59da3-106">Członek</span><span class="sxs-lookup"><span data-stu-id="59da3-106">Member</span></span>|<span data-ttu-id="59da3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="59da3-107">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="59da3-108">Wskazuje, że odwołanie do zestawu zawiera pełny, niezmieszany klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="59da3-108">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="59da3-109">Wskazuje, że nie określono architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="59da3-109">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="59da3-110">Wskazuje, że architektura procesora jest neutralna (PE32).</span><span class="sxs-lookup"><span data-stu-id="59da3-110">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="59da3-111">Wskazuje, że architektura procesora to x86 (PE32).</span><span class="sxs-lookup"><span data-stu-id="59da3-111">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="59da3-112">Wskazuje, że architektura procesora jest Itanium (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="59da3-112">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="59da3-113">Wskazuje, że architektura procesora to AMD x64 (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="59da3-113">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="59da3-114">Wskazuje, że architektura procesora to ARM (PE32).</span><span class="sxs-lookup"><span data-stu-id="59da3-114">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="59da3-115">Wskazuje, że zestaw jest zestawem referencyjnym; oznacza to, że ma zastosowanie do dowolnej architektury, ale nie może działać w żadnej architekturze.</span><span class="sxs-lookup"><span data-stu-id="59da3-115">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="59da3-116">W tym celu flaga jest taka sama jak `afPA_Mask` .</span><span class="sxs-lookup"><span data-stu-id="59da3-116">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="59da3-117">Wskazuje, że flagi architektury procesora powinny być propagowane do `AssemblyRef` rekordu.</span><span class="sxs-lookup"><span data-stu-id="59da3-117">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="59da3-118">Maska opisująca architekturę procesora.</span><span class="sxs-lookup"><span data-stu-id="59da3-118">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="59da3-119">Określa, że opis architektury procesora jest uwzględniany.</span><span class="sxs-lookup"><span data-stu-id="59da3-119">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="59da3-120">Wskazuje liczbę przesunięć w flagach architektury procesora do i z indeksu.</span><span class="sxs-lookup"><span data-stu-id="59da3-120">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="59da3-121">Wskazuje odpowiednią wartość z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="59da3-121">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="59da3-122">Wskazuje odpowiednią wartość z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute> .</span><span class="sxs-lookup"><span data-stu-id="59da3-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="59da3-123">Wskazuje, że zestaw można przekierować w czasie wykonywania do zestawu z innego wydawcy.</span><span class="sxs-lookup"><span data-stu-id="59da3-123">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="59da3-124">Maska opisująca typ zawartości.</span><span class="sxs-lookup"><span data-stu-id="59da3-124">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="59da3-125">Wskazuje domyślny typ zawartości.</span><span class="sxs-lookup"><span data-stu-id="59da3-125">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="59da3-126">Wskazuje typ zawartości środowisko wykonawcze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="59da3-126">Indicates the Windows Runtime content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="59da3-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="59da3-127">Requirements</span></span>  
 <span data-ttu-id="59da3-128">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59da3-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59da3-129">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="59da3-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="59da3-130">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59da3-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59da3-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59da3-131">See also</span></span>

- [<span data-ttu-id="59da3-132">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="59da3-132">Metadata Enumerations</span></span>](metadata-enumerations.md)

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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eca4b66a3f7c1a96bb06827dde477f34cb904ba3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906246"
---
# <a name="corassemblyflags-enumeration"></a><span data-ttu-id="0aecb-102">CorAssemblyFlags — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0aecb-102">CorAssemblyFlags Enumeration</span></span>
<span data-ttu-id="0aecb-103">Zawiera wartości, które opisują metadane stosowane do kompilacji zestawu.</span><span class="sxs-lookup"><span data-stu-id="0aecb-103">Contains values that describe the metadata applied to an assembly compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aecb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0aecb-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="0aecb-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0aecb-105">Members</span></span>  
  
|<span data-ttu-id="0aecb-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="0aecb-106">Member</span></span>|<span data-ttu-id="0aecb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0aecb-107">Description</span></span>|  
|------------|-----------------|  
|`afPublicKey`|<span data-ttu-id="0aecb-108">Wskazuje, że odwołanie do zestawu zawiera pełną, bez haszowania klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="0aecb-108">Indicates that the assembly reference holds the full, unhashed public key.</span></span>|  
|`afPA_None`|<span data-ttu-id="0aecb-109">Wskazuje, że architektura procesora jest nieokreślony.</span><span class="sxs-lookup"><span data-stu-id="0aecb-109">Indicates that the processor architecture is unspecified.</span></span>|  
|`afPA_MSIL`|<span data-ttu-id="0aecb-110">Wskazuje, że architektura procesora jest neutralny (PE32).</span><span class="sxs-lookup"><span data-stu-id="0aecb-110">Indicates that the processor architecture is neutral (PE32).</span></span>|  
|`afPA_x86`|<span data-ttu-id="0aecb-111">Wskazuje, że architektura procesora jest x86 (PE32).</span><span class="sxs-lookup"><span data-stu-id="0aecb-111">Indicates that the processor architecture is x86 (PE32).</span></span>|  
|`afPA_IA64`|<span data-ttu-id="0aecb-112">Wskazuje, że architektura procesora jest Itanium (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="0aecb-112">Indicates that the processor architecture is Itanium (PE32+).</span></span>|  
|`afPA_AMD64`|<span data-ttu-id="0aecb-113">Wskazuje, że architektura procesora jest AMD X64 (PE32 +).</span><span class="sxs-lookup"><span data-stu-id="0aecb-113">Indicates that the processor architecture is AMD X64 (PE32+).</span></span>|  
|`afPA_ARM`|<span data-ttu-id="0aecb-114">Wskazuje, że architektura procesora jest ARM (PE32).</span><span class="sxs-lookup"><span data-stu-id="0aecb-114">Indicates that the processor architecture is ARM (PE32).</span></span>|  
|`afPA_NoPlatform`|<span data-ttu-id="0aecb-115">Wskazuje, że zestaw jest zestaw odwołania; oznacza, że ma zastosowanie do dowolnej architekturze ale nie można uruchomić na dowolnej architektury.</span><span class="sxs-lookup"><span data-stu-id="0aecb-115">Indicates that the assembly is a reference assembly; that is, it applies to any architecture but cannot run on any architecture.</span></span> <span data-ttu-id="0aecb-116">W związku z tym, Flaga jest taka sama jak `afPA_Mask`.</span><span class="sxs-lookup"><span data-stu-id="0aecb-116">Thus, the flag is the same as `afPA_Mask`.</span></span>|  
|`afPA_Specified`|<span data-ttu-id="0aecb-117">Wskazuje, że flagi architektury procesora należy propagowane do `AssemblyRef` rekordu.</span><span class="sxs-lookup"><span data-stu-id="0aecb-117">Indicates that the processor architecture flags should be propagated to the `AssemblyRef` record.</span></span>|  
|`afPA_Mask`|<span data-ttu-id="0aecb-118">Maska, która zawiera opis architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="0aecb-118">A mask that describes the processor architecture.</span></span>|  
|`afPA_FullMask`|<span data-ttu-id="0aecb-119">Określa, czy znajduje się opis architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="0aecb-119">Specifies that the processor architecture description is included.</span></span>|  
|`afPA_Shift`|<span data-ttu-id="0aecb-120">Wskazuje liczbę shift in flagi architektury procesora, do i z indeksu.</span><span class="sxs-lookup"><span data-stu-id="0aecb-120">Indicates a shift count in the processor architecture flags to and from the index.</span></span>|  
|`afEnableJITcompileTracking`|<span data-ttu-id="0aecb-121">Wskazuje odpowiedniej wartości z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> z <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0aecb-121">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afDisableJITcompileOptimizer`|<span data-ttu-id="0aecb-122">Wskazuje odpowiedniej wartości z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> z <xref:System.Diagnostics.DebuggableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0aecb-122">Indicates the corresponding value from the <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> of the <xref:System.Diagnostics.DebuggableAttribute>.</span></span>|  
|`afRetargetable`|<span data-ttu-id="0aecb-123">Wskazuje, czy zestaw można przekierować go w czasie wykonywania do zestawu od innego wydawcy.</span><span class="sxs-lookup"><span data-stu-id="0aecb-123">Indicates that the assembly can be retargeted at run time to an assembly from a different publisher.</span></span>|  
|`afContentType_Mask`|<span data-ttu-id="0aecb-124">Maska, który opisuje typ zawartości.</span><span class="sxs-lookup"><span data-stu-id="0aecb-124">A mask that describes the content type.</span></span>|  
|`afContentType_Default`|<span data-ttu-id="0aecb-125">Określa domyślny typ zawartości.</span><span class="sxs-lookup"><span data-stu-id="0aecb-125">Indicates the default content type.</span></span>|  
|`afContentType_WindowsRuntime`|<span data-ttu-id="0aecb-126">Wskazuje [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typ zawartości.</span><span class="sxs-lookup"><span data-stu-id="0aecb-126">Indicates the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] content type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0aecb-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0aecb-127">Requirements</span></span>  
 <span data-ttu-id="0aecb-128">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aecb-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aecb-129">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="0aecb-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0aecb-130">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0aecb-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aecb-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0aecb-131">See also</span></span>

- [<span data-ttu-id="0aecb-132">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="0aecb-132">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

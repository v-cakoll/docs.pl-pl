---
title: "CorMethodImpl — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorMethodImpl
api_location: mscoree.dll
api_type: COM
f1_keywords: CorMethodImpl
helpviewer_keywords: CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e82eb50e4850ffbb4d5fc67d9603a3128cf8bcf6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="b4b9f-102">CorMethodImpl — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b4b9f-102">CorMethodImpl Enumeration</span></span>
<span data-ttu-id="b4b9f-103">Zawiera wartości, które opisują funkcji w implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="b4b9f-103">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4b9f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4b9f-104">Syntax</span></span>  
  
```  
typedef enum CorMethodImpl {  
  
    miCodeTypeMask      =   0x0003,  
    miIL                =   0x0000,  
    miNative            =   0x0001,  
    miOPTIL             =   0x0002,  
    miRuntime           =   0x0003,  
  
    miManagedMask       =   0x0004,  
    miUnmanaged         =   0x0004,  
    miManaged           =   0x0000,  
  
    miForwardRef        =   0x0010,  
    miPreserveSig       =   0x0080,  
  
    miInternalCall      =   0x1000,  
    miSynchronized      =   0x0020,  
    miNoInlining        =   0x0008,  
    miAggressiveInlining =  0x0100,  
    miNoOptimization     =  0x0040,  
    miMaxMethodImplVal  =   0xffff  
  
} CorMethodImpl;  
```  
  
## <a name="members"></a><span data-ttu-id="b4b9f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b4b9f-105">Members</span></span>  
  
|<span data-ttu-id="b4b9f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b4b9f-106">Member</span></span>|<span data-ttu-id="b4b9f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b4b9f-107">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="b4b9f-108">Flagi opisujące typ kodu.</span><span class="sxs-lookup"><span data-stu-id="b4b9f-108">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="b4b9f-109">Określa, że implementacja metody język pośredni firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="b4b9f-109">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="b4b9f-110">Określa, że implementacja metody natywnej.</span><span class="sxs-lookup"><span data-stu-id="b4b9f-110">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="b4b9f-111">Określa, że implementacja metody OPTIL.</span><span class="sxs-lookup"><span data-stu-id="b4b9f-111">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="b4b9f-112">Określa, że implementacja metody są dostarczane przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="b4b9f-112">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="b4b9f-113">Flagi, które wskazują, czy kod jest zarządzane lub niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="b4b9f-113">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="b4b9f-114">Określa, że implementacja metody niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="b4b9f-114">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="b4b9f-115">Określa, że jest zarządzana w implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="b4b9f-115">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="b4b9f-116">Określa, że metoda jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="b4b9f-116">Specifies that the method is defined.</span></span> <span data-ttu-id="b4b9f-117">Ta flaga jest wykorzystywana głównie w przypadku scenariuszy scalania.</span><span class="sxs-lookup"><span data-stu-id="b4b9f-117">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="b4b9f-118">Określa, że podpis metody nie zniekształcone konwersji HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b4b9f-118">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="b4b9f-119">Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="b4b9f-119">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="b4b9f-120">Określa, że metoda jest jednowątkowy za pośrednictwem jego treści.</span><span class="sxs-lookup"><span data-stu-id="b4b9f-120">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="b4b9f-121">Określa, że metoda nie może być wbudowane.</span><span class="sxs-lookup"><span data-stu-id="b4b9f-121">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="b4b9f-122">Określa, że metoda powinna być wbudowane, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="b4b9f-122">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="b4b9f-123">Określa, że metoda nie może zostać zoptymalizowana.</span><span class="sxs-lookup"><span data-stu-id="b4b9f-123">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="b4b9f-124">Maksymalna prawidłowa wartość dla `CorMethodImpl`.</span><span class="sxs-lookup"><span data-stu-id="b4b9f-124">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b4b9f-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4b9f-125">Requirements</span></span>  
 <span data-ttu-id="b4b9f-126">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4b9f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4b9f-127">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b4b9f-127">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b4b9f-128">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4b9f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4b9f-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4b9f-129">See Also</span></span>  
 [<span data-ttu-id="b4b9f-130">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="b4b9f-130">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

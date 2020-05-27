---
title: CorMethodImpl — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodImpl
helpviewer_keywords:
- CorMethodImpl enumeration [.NET Framework metadata]
ms.assetid: ffbb3caf-20da-4a4b-8983-77376e72b990
topic_type:
- apiref
ms.openlocfilehash: b32e8f0b03ef6d550c384f3d932cc295a7270028
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007666"
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="70c67-102">CorMethodImpl — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="70c67-102">CorMethodImpl Enumeration</span></span>
<span data-ttu-id="70c67-103">Zawiera wartości opisujące funkcje implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="70c67-103">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70c67-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="70c67-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="70c67-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="70c67-105">Members</span></span>  
  
|<span data-ttu-id="70c67-106">Członek</span><span class="sxs-lookup"><span data-stu-id="70c67-106">Member</span></span>|<span data-ttu-id="70c67-107">Opis</span><span class="sxs-lookup"><span data-stu-id="70c67-107">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="70c67-108">Flagi opisujące typ kodu.</span><span class="sxs-lookup"><span data-stu-id="70c67-108">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="70c67-109">Określa, że implementacja metody to język pośredni (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="70c67-109">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="70c67-110">Określa, że implementacja metody jest natywna.</span><span class="sxs-lookup"><span data-stu-id="70c67-110">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="70c67-111">Określa, że implementacja metody to OPTI.</span><span class="sxs-lookup"><span data-stu-id="70c67-111">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="70c67-112">Określa, że implementacja metody jest dostarczana przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="70c67-112">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="70c67-113">Flagi wskazujące, czy kod jest zarządzany lub niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="70c67-113">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="70c67-114">Określa, że implementacja metody jest niezarządzana.</span><span class="sxs-lookup"><span data-stu-id="70c67-114">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="70c67-115">Określa, że implementacja metody jest zarządzana.</span><span class="sxs-lookup"><span data-stu-id="70c67-115">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="70c67-116">Określa, że metoda jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="70c67-116">Specifies that the method is defined.</span></span> <span data-ttu-id="70c67-117">Ta flaga jest używana głównie w scenariuszach scalania.</span><span class="sxs-lookup"><span data-stu-id="70c67-117">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="70c67-118">Określa, że podpis metody nie może być zniekształcona dla konwersji HRESULT.</span><span class="sxs-lookup"><span data-stu-id="70c67-118">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="70c67-119">Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="70c67-119">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="70c67-120">Określa, że metoda jest jednowątkowa za pomocą jej treści.</span><span class="sxs-lookup"><span data-stu-id="70c67-120">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="70c67-121">Określa, że metoda nie może być wbudowana.</span><span class="sxs-lookup"><span data-stu-id="70c67-121">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="70c67-122">Określa, że metoda powinna być przedkreślona, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="70c67-122">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="70c67-123">Określa, że metoda nie powinna być zoptymalizowana.</span><span class="sxs-lookup"><span data-stu-id="70c67-123">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="70c67-124">Maksymalna prawidłowa wartość elementu `CorMethodImpl` .</span><span class="sxs-lookup"><span data-stu-id="70c67-124">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="70c67-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="70c67-125">Requirements</span></span>  
 <span data-ttu-id="70c67-126">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70c67-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70c67-127">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="70c67-127">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="70c67-128">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70c67-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70c67-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70c67-129">See also</span></span>

- [<span data-ttu-id="70c67-130">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="70c67-130">Metadata Enumerations</span></span>](metadata-enumerations.md)

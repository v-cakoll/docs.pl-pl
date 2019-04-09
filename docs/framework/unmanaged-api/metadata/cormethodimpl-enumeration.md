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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2138dd32cf39db7b7c8989ba5827178d1a1e46c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117238"
---
# <a name="cormethodimpl-enumeration"></a><span data-ttu-id="b27c0-102">CorMethodImpl — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="b27c0-102">CorMethodImpl Enumeration</span></span>
<span data-ttu-id="b27c0-103">Zawiera wartości, które opisano funkcje implementacji metody.</span><span class="sxs-lookup"><span data-stu-id="b27c0-103">Contains values that describe method implementation features.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b27c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b27c0-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="b27c0-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="b27c0-105">Members</span></span>  
  
|<span data-ttu-id="b27c0-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="b27c0-106">Member</span></span>|<span data-ttu-id="b27c0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b27c0-107">Description</span></span>|  
|------------|-----------------|  
|`miCodeTypeMask`|<span data-ttu-id="b27c0-108">Flagi, które opisują typ kodu.</span><span class="sxs-lookup"><span data-stu-id="b27c0-108">Flags that describe code type.</span></span>|  
|`miIL`|<span data-ttu-id="b27c0-109">Określa, że implementacja metody języka Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="b27c0-109">Specifies that the method implementation is Microsoft intermediate language (MSIL).</span></span>|  
|`miNative`|<span data-ttu-id="b27c0-110">Określa, że implementacja metody natywnej.</span><span class="sxs-lookup"><span data-stu-id="b27c0-110">Specifies that the method implementation is native.</span></span>|  
|`miOPTIL`|<span data-ttu-id="b27c0-111">Określa, że implementacja metody OPTIL.</span><span class="sxs-lookup"><span data-stu-id="b27c0-111">Specifies that the method implementation is OPTIL.</span></span>|  
|`miRuntime`|<span data-ttu-id="b27c0-112">Określa, że implementacja metody jest świadczona przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="b27c0-112">Specifies that the method implementation is provided by the common language runtime.</span></span>|  
|`miManagedMask`|<span data-ttu-id="b27c0-113">Flagi, które wskazują, czy kod jest zarządzany lub niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="b27c0-113">Flags that indicate whether the code is managed or unmanaged.</span></span>|  
|`miUnmanaged`|<span data-ttu-id="b27c0-114">Określa, że implementacja metody niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="b27c0-114">Specifies that the method implementation is unmanaged.</span></span>|  
|`miManaged`|<span data-ttu-id="b27c0-115">Określa, że implementacja metody jest zarządzana.</span><span class="sxs-lookup"><span data-stu-id="b27c0-115">Specifies that the method implementation is managed.</span></span>|  
|`miForwardRef`|<span data-ttu-id="b27c0-116">Określa, że metoda jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="b27c0-116">Specifies that the method is defined.</span></span> <span data-ttu-id="b27c0-117">Ta flaga jest używana głównie w scenariuszach scalania.</span><span class="sxs-lookup"><span data-stu-id="b27c0-117">This flag is used primarily in merge scenarios.</span></span>|  
|`miPreserveSig`|<span data-ttu-id="b27c0-118">Określa, że podpis metody nie zniekształcone konwersji HRESULT.</span><span class="sxs-lookup"><span data-stu-id="b27c0-118">Specifies that the method signature cannot be mangled for an HRESULT conversion.</span></span>|  
|`miInternalCall`|<span data-ttu-id="b27c0-119">Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="b27c0-119">Reserved for internal use by the common language runtime.</span></span>|  
|`miSynchronized`|<span data-ttu-id="b27c0-120">Określa, że metoda jest jednowątkowym za pośrednictwem jej treści.</span><span class="sxs-lookup"><span data-stu-id="b27c0-120">Specifies that the method is single-threaded through its body.</span></span>|  
|`miNoInlining`|<span data-ttu-id="b27c0-121">Określa, że metoda nie może być śródwierszowa.</span><span class="sxs-lookup"><span data-stu-id="b27c0-121">Specifies that the method cannot be inlined.</span></span>|  
|`miAggressiveInlining`|<span data-ttu-id="b27c0-122">Określa, że metoda powinna być śródwierszowa, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="b27c0-122">Specifies that the method should be inlined if possible.</span></span>|  
|`miNoOptimization`|<span data-ttu-id="b27c0-123">Określa metody nie powinny być zoptymalizowany.</span><span class="sxs-lookup"><span data-stu-id="b27c0-123">Specifies that the method should not be optimized.</span></span>|  
|`miMaxMethodImplVal`|<span data-ttu-id="b27c0-124">Maksymalna prawidłowa wartość dla `CorMethodImpl`.</span><span class="sxs-lookup"><span data-stu-id="b27c0-124">The maximum valid value for a `CorMethodImpl`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b27c0-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b27c0-125">Requirements</span></span>  
 <span data-ttu-id="b27c0-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b27c0-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b27c0-127">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b27c0-127">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="b27c0-128">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b27c0-128">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b27c0-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b27c0-129">See also</span></span>

- [<span data-ttu-id="b27c0-130">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="b27c0-130">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)

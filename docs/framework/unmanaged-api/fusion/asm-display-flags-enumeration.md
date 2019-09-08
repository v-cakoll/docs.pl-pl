---
title: ASM_DISPLAY_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- ASM_DISPLAY_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_DISPLAY_FLAGS
helpviewer_keywords:
- ASM_DISPLAY_FLAGS enumeration [.NET Framework fusion]
ms.assetid: dbade6c9-9d26-4a79-9fd2-46108edd12d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8befdb454a564ec834532653dd44cf230fa43d79
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795217"
---
# <a name="asm_display_flags-enumeration"></a><span data-ttu-id="6ac4f-102">ASM_DISPLAY_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6ac4f-102">ASM_DISPLAY_FLAGS Enumeration</span></span>
<span data-ttu-id="6ac4f-103">Wskazuje wersję, kompilację, kulturę, sygnaturę i tak dalej, zestawu, którego nazwa wyświetlana zostanie pobrana przez [IAssemblyName:: GetDisplayName](iassemblyname-getdisplayname-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="6ac4f-103">Indicates the version, build, culture, signature, and so on, of the assembly whose display name will be retrieved by the [IAssemblyName::GetDisplayName](iassemblyname-getdisplayname-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ac4f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ac4f-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
  
    ASM_DISPLAYF_VERSION                 = 0x01,  
    ASM_DISPLAYF_CULTURE                 = 0x02,  
    ASM_DISPLAYF_PUBLIC_KEY_TOKEN        = 0x04,  
    ASM_DISPLAYF_PUBLIC_KEY              = 0x08,  
    ASM_DISPLAYF_CUSTOM                  = 0x10,  
    ASM_DISPLAYF_PROCESSORARCHITECTURE   = 0x20,  
    ASM_DISPLAYF_LANGUAGEID              = 0x40,  
    ASM_DISPLAYF_RETARGET                = 0x80,  
    ASM_DISPLAYF_CONFIG_MASK             = 0x100,  
    ASM_DISPLAYF_MVID                    = 0x200,  
    ASM_DISPLAYF_FULL                    =   
                      ASM_DISPLAYF_VERSION           |   
                      ASM_DISPLAYF_CULTURE           |   
                      ASM_DISPLAYF_PUBLIC_KEY_TOKEN  |   
                      ASM_DISPLAYF_RETARGET          |   
                      ASM_DISPLAYF_PROCESSORARCHITECTURE  
  
} ASM_DISPLAY_FLAGS;  
```  
  
## <a name="remarks"></a><span data-ttu-id="6ac4f-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6ac4f-105">Remarks</span></span>  
 <span data-ttu-id="6ac4f-106">`ASM_DISPLAYF_FULL`odzwierciedla wszelkie zmiany wprowadzone w wersji obiektu [IAssemblyName](iassemblyname-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="6ac4f-106">`ASM_DISPLAYF_FULL` reflects any changes made to the version of the [IAssemblyName](iassemblyname-interface.md) object.</span></span> <span data-ttu-id="6ac4f-107">Nie należy zakładać, że zwracana wartość jest niezmienna.</span><span class="sxs-lookup"><span data-stu-id="6ac4f-107">Do not assume that the returned value is immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ac4f-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ac4f-108">Requirements</span></span>  
 <span data-ttu-id="6ac4f-109">**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ac4f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ac4f-110">**Nagłówki** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="6ac4f-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6ac4f-111">**Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6ac4f-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6ac4f-112">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ac4f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ac4f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ac4f-113">See also</span></span>

- [<span data-ttu-id="6ac4f-114">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="6ac4f-114">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="6ac4f-115">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="6ac4f-115">Fusion Enumerations</span></span>](fusion-enumerations.md)

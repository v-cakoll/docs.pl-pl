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
ms.openlocfilehash: 0871a06c6e27089d9e8fea6726d1d7b37fb75120
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561754"
---
# <a name="asmdisplayflags-enumeration"></a><span data-ttu-id="66fb0-102">ASM_DISPLAY_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="66fb0-102">ASM_DISPLAY_FLAGS Enumeration</span></span>
<span data-ttu-id="66fb0-103">Wskazuje, wersji, kompilacji, kultury, podpis i tak dalej, zestawu, którego nazwa wyświetlana będzie pobierany przez [iassemblyname::GetDisplayName —](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="66fb0-103">Indicates the version, build, culture, signature, and so on, of the assembly whose display name will be retrieved by the [IAssemblyName::GetDisplayName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66fb0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="66fb0-104">Syntax</span></span>  
  
```  
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
  
## <a name="remarks"></a><span data-ttu-id="66fb0-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="66fb0-105">Remarks</span></span>  
 <span data-ttu-id="66fb0-106">`ASM_DISPLAYF_FULL` odzwierciedla wszelkie zmiany wprowadzone do wersji [iassemblyname —](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="66fb0-106">`ASM_DISPLAYF_FULL` reflects any changes made to the version of the [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span> <span data-ttu-id="66fb0-107">Nie należy zakładać, że zwracana wartość jest niezmienny.</span><span class="sxs-lookup"><span data-stu-id="66fb0-107">Do not assume that the returned value is immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66fb0-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="66fb0-108">Requirements</span></span>  
 <span data-ttu-id="66fb0-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66fb0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66fb0-110">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="66fb0-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="66fb0-111">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="66fb0-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="66fb0-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66fb0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66fb0-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66fb0-113">See also</span></span>
- [<span data-ttu-id="66fb0-114">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="66fb0-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="66fb0-115">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="66fb0-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)

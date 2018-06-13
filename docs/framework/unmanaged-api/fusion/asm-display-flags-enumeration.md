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
ms.openlocfilehash: 9607aa99e1f1dbe0af3a868a32c70cd83d5e66a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429533"
---
# <a name="asmdisplayflags-enumeration"></a><span data-ttu-id="ec654-102">ASM_DISPLAY_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ec654-102">ASM_DISPLAY_FLAGS Enumeration</span></span>
<span data-ttu-id="ec654-103">Wskazuje wersję, kompilacji, kultury, sygnatury i tak dalej, zestawu, którego nazwa wyświetlana zostaną pobrane przez [IAssemblyName::GetDisplayName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="ec654-103">Indicates the version, build, culture, signature, and so on, of the assembly whose display name will be retrieved by the [IAssemblyName::GetDisplayName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec654-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec654-104">Syntax</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="ec654-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec654-105">Remarks</span></span>  
 <span data-ttu-id="ec654-106">`ASM_DISPLAYF_FULL` odzwierciedla żadnych zmian wprowadzonych w wersji [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="ec654-106">`ASM_DISPLAYF_FULL` reflects any changes made to the version of the [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) object.</span></span> <span data-ttu-id="ec654-107">Zakłada się, że zwracanej wartości nie można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="ec654-107">Do not assume that the returned value is immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec654-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec654-108">Requirements</span></span>  
 <span data-ttu-id="ec654-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec654-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec654-110">**Nagłówek:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="ec654-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="ec654-111">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ec654-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec654-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec654-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec654-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec654-113">See Also</span></span>  
 [<span data-ttu-id="ec654-114">IAssemblyName, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec654-114">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="ec654-115">Wyliczenia łączenia</span><span class="sxs-lookup"><span data-stu-id="ec654-115">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)

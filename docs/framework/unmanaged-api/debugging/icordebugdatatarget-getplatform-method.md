---
title: ICorDebugDataTarget::GetPlatform — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
ms.openlocfilehash: 3654c94975d16e35d5c3d8e762730d17509a2c6d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788878"
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="ecde5-102">ICorDebugDataTarget::GetPlatform — Metoda</span><span class="sxs-lookup"><span data-stu-id="ecde5-102">ICorDebugDataTarget::GetPlatform Method</span></span>
<span data-ttu-id="ecde5-103">Zawiera informacje na temat platformy, w tym architektury procesora i systemu operacyjnego, na których jest uruchomiony proces docelowy.</span><span class="sxs-lookup"><span data-stu-id="ecde5-103">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecde5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecde5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecde5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecde5-105">Parameters</span></span>  
 `pTargetPlatform`  
 <span data-ttu-id="ecde5-106">określoną Wskaźnik do wyliczenia [CorDebugPlatformEnum —](cordebugplatform-enumeration.md) , który opisuje platformę docelową.</span><span class="sxs-lookup"><span data-stu-id="ecde5-106">[out] A pointer to a [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecde5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ecde5-107">Remarks</span></span>  
 <span data-ttu-id="ecde5-108">Wartość zwracana `CorDebugPlatformEnum` wyliczeniem jest używana przez interfejs [ICorDebug](icordebug-interface.md) , aby określić szczegóły procesu docelowego, takie jak rozmiar wskaźnika, układ przestrzeni adresowej, zestaw rejestru, format instrukcji, układ kontekstu i konwencje wywoływania.</span><span class="sxs-lookup"><span data-stu-id="ecde5-108">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="ecde5-109">Wartość `pTargetPlatform` może odwoływać się do platformy, która jest emulowana dla elementu docelowego zamiast określania rzeczywistego sprzętu w użyciu.</span><span class="sxs-lookup"><span data-stu-id="ecde5-109">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="ecde5-110">Na przykład proces uruchomiony w środowisku systemu Windows w systemie Windows (WOW) w 64-bitowej wersji systemu operacyjnego Windows powinien używać wartości `CORDB_PLATFORM_WINDOWS_X86` wyliczenia [CorDebugPlatformEnum —](cordebugplatform-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ecde5-110">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="ecde5-111">Ta metoda musi zakończyć się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ecde5-111">This method must succeed.</span></span> <span data-ttu-id="ecde5-112">Jeśli to się nie powiedzie, platforma docelowa będzie bezużyteczny.</span><span class="sxs-lookup"><span data-stu-id="ecde5-112">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="ecde5-113">Metoda może zakończyć się niepowodzeniem z następujących powodów:</span><span class="sxs-lookup"><span data-stu-id="ecde5-113">The method may fail for the following reasons:</span></span>  
  
- <span data-ttu-id="ecde5-114">Platforma, która jest emulowana dla elementu docelowego, nie nadaje się do użytku.</span><span class="sxs-lookup"><span data-stu-id="ecde5-114">The platform that is being emulated for the target is unusable.</span></span>  
  
- <span data-ttu-id="ecde5-115">Rzeczywisty sprzęt na platformie docelowej nie nadaje się do użytku.</span><span class="sxs-lookup"><span data-stu-id="ecde5-115">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecde5-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ecde5-116">Requirements</span></span>  
 <span data-ttu-id="ecde5-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecde5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecde5-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ecde5-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ecde5-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ecde5-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecde5-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecde5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecde5-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecde5-121">See also</span></span>

- [<span data-ttu-id="ecde5-122">ICorDebugDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="ecde5-122">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="ecde5-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ecde5-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ecde5-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ecde5-124">Debugging</span></span>](index.md)

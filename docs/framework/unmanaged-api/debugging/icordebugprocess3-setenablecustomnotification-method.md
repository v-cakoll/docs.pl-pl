---
title: ICorDebugProcess3::SetEnableCustomNotification — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
ms.openlocfilehash: ec60274648315c4fa38f3832d8d39c1a269956b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129706"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="45ca1-102">ICorDebugProcess3::SetEnableCustomNotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="45ca1-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="45ca1-103">Włącza i wyłącza niestandardowe powiadomienia debugera określonego typu.</span><span class="sxs-lookup"><span data-stu-id="45ca1-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45ca1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="45ca1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45ca1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="45ca1-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="45ca1-106">podczas Typ, który określa niestandardowe powiadomienia debugera.</span><span class="sxs-lookup"><span data-stu-id="45ca1-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="45ca1-107">[in] `true` włączyć powiadomień debugera niestandardowego; `false` wyłączyć powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="45ca1-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="45ca1-108">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="45ca1-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45ca1-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45ca1-109">Remarks</span></span>  
 <span data-ttu-id="45ca1-110">Gdy `fEnable` jest ustawiona na `true`, wywołania metody <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> wyzwalają wywołanie zwrotne [ICorDebugManagedCallback3:: CustomNotification —](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="45ca1-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="45ca1-111">Powiadomienia są domyślnie wyłączone; w związku z tym debuger musi określić wszelkie typy powiadomień, o których wie i który chce obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="45ca1-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="45ca1-112">Ponieważ Klasa [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) jest objęta zakresem przez domenę aplikacji, debuger musi wywoływać `SetEnableCustomNotification` dla każdej domeny aplikacji w procesie, jeśli chce otrzymywać powiadomienie przez cały proces.</span><span class="sxs-lookup"><span data-stu-id="45ca1-112">Because the [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="45ca1-113">Począwszy od .NET Framework 4, jedyne obsługiwane powiadomienie to powiadomienie obejmujące zależność między wątkami.</span><span class="sxs-lookup"><span data-stu-id="45ca1-113">Starting with the .NET Framework 4, the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45ca1-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="45ca1-114">Requirements</span></span>  
 <span data-ttu-id="45ca1-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45ca1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45ca1-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="45ca1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45ca1-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="45ca1-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45ca1-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45ca1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45ca1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45ca1-119">See also</span></span>

- [<span data-ttu-id="45ca1-120">ICorDebugProcess3, interfejs</span><span class="sxs-lookup"><span data-stu-id="45ca1-120">ICorDebugProcess3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)
- [<span data-ttu-id="45ca1-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="45ca1-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="45ca1-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="45ca1-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

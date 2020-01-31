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
ms.openlocfilehash: f2f365f3fe1568f2dd3bad677dd77a13946002e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792466"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="25ef7-102">ICorDebugProcess3::SetEnableCustomNotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="25ef7-102">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>
<span data-ttu-id="25ef7-103">Włącza i wyłącza niestandardowe powiadomienia debugera określonego typu.</span><span class="sxs-lookup"><span data-stu-id="25ef7-103">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25ef7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25ef7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25ef7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25ef7-105">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="25ef7-106">podczas Typ, który określa niestandardowe powiadomienia debugera.</span><span class="sxs-lookup"><span data-stu-id="25ef7-106">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="25ef7-107">[in] `true` włączyć powiadomień debugera niestandardowego; `false` wyłączyć powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="25ef7-107">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="25ef7-108">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="25ef7-108">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25ef7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25ef7-109">Remarks</span></span>  
 <span data-ttu-id="25ef7-110">Gdy `fEnable` jest ustawiona na `true`, wywołania metody <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> wyzwalają wywołanie zwrotne [ICorDebugManagedCallback3:: CustomNotification —](icordebugmanagedcallback3-customnotification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="25ef7-110">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="25ef7-111">Powiadomienia są domyślnie wyłączone; w związku z tym debuger musi określić wszelkie typy powiadomień, o których wie i który chce obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="25ef7-111">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="25ef7-112">Ponieważ Klasa [ICorDebugClass](icordebug-interface.md) jest objęta zakresem przez domenę aplikacji, debuger musi wywoływać `SetEnableCustomNotification` dla każdej domeny aplikacji w procesie, jeśli chce otrzymywać powiadomienie przez cały proces.</span><span class="sxs-lookup"><span data-stu-id="25ef7-112">Because the [ICorDebugClass](icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="25ef7-113">Począwszy od .NET Framework 4, jedyne obsługiwane powiadomienie to powiadomienie obejmujące zależność między wątkami.</span><span class="sxs-lookup"><span data-stu-id="25ef7-113">Starting with the .NET Framework 4, the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25ef7-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25ef7-114">Requirements</span></span>  
 <span data-ttu-id="25ef7-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25ef7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25ef7-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="25ef7-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25ef7-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="25ef7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25ef7-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25ef7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ef7-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25ef7-119">See also</span></span>

- [<span data-ttu-id="25ef7-120">ICorDebugProcess3, interfejs</span><span class="sxs-lookup"><span data-stu-id="25ef7-120">ICorDebugProcess3 Interface</span></span>](icordebugprocess3-interface.md)
- [<span data-ttu-id="25ef7-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="25ef7-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="25ef7-122">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="25ef7-122">Debugging</span></span>](index.md)

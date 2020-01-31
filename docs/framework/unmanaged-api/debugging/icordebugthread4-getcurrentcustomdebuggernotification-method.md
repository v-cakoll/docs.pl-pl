---
title: ICorDebugThread4::GetCurrentCustomDebuggerNotification — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetCurrentCustomDebuggerNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetCurrentCustomDebuggerNotification
helpviewer_keywords:
- GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
- ICorDebugThread4::GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
ms.assetid: 57e0f2d2-5f0e-4e2d-99ec-3f26632eb693
topic_type:
- apiref
ms.openlocfilehash: a8a377074ca1005ad8089dfd8e2a6a464bb86f60
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791366"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="f5207-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification — Metoda</span><span class="sxs-lookup"><span data-stu-id="f5207-102">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="f5207-103">Pobiera bieżący obiekt [ICorDebugManagedCallback3:: CustomNotification —](icordebugmanagedcallback3-customnotification-method.md) w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="f5207-103">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="f5207-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f5207-104">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="f5207-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5207-105">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="f5207-106">określoną Wskaźnik do bieżącego obiektu `ICorDebugManagedCallback3::CustomNotification` w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="f5207-106">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5207-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f5207-107">Remarks</span></span>

<span data-ttu-id="f5207-108">Wartość `ppNotificationObject` ma wartość null, jeśli metoda nie jest wywoływana z poziomu wywołania zwrotnego `ICorDebugManagedCallback3::CustomNotification` lub jeśli nie istnieje bieżący obiekt powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="f5207-108">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="f5207-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f5207-109">Requirements</span></span>

<span data-ttu-id="f5207-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5207-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="f5207-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f5207-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="f5207-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f5207-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="f5207-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5207-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f5207-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5207-114">See also</span></span>

- [<span data-ttu-id="f5207-115">ICorDebugThread4, interfejs</span><span class="sxs-lookup"><span data-stu-id="f5207-115">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="f5207-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f5207-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f5207-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f5207-117">Debugging</span></span>](index.md)

---
title: ICorDebugProcess4, interfejs
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4
helpviewer_keywords:
- ICorDebugProcess4 interface [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 1bdc958f2516bcd7c2eb74312fbf478e6d49535a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948810"
---
# <a name="icordebugprocess4-interface"></a><span data-ttu-id="b0397-102">ICorDebugProcess4, interfejs</span><span class="sxs-lookup"><span data-stu-id="b0397-102">ICorDebugProcess4 Interface</span></span>

<span data-ttu-id="b0397-103">Zapewnia obsługę poza Kontrola wykonywania procesu.</span><span class="sxs-lookup"><span data-stu-id="b0397-103">Provides support for out of process execution control.</span></span>

## <a name="methods"></a><span data-ttu-id="b0397-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b0397-104">Methods</span></span>

| <span data-ttu-id="b0397-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b0397-105">Method</span></span>                                                                 | <span data-ttu-id="b0397-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b0397-106">Description</span></span>                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="b0397-107">ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="b0397-107">ProcessStateChanged</span></span>](icordebugprocess4-processstatechanged-method.md) | <span data-ttu-id="b0397-108">Powiadamia potoku ICorDebug, poza debugera proces kontynuuje wykonywanie debugee.</span><span class="sxs-lookup"><span data-stu-id="b0397-108">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span> |

## <a name="remarks"></a><span data-ttu-id="b0397-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0397-109">Remarks</span></span>

<span data-ttu-id="b0397-110">Ten interfejs znajduje się wewnątrz środowiska uruchomieniowego i nie jest dostępna za pośrednictwem wszystkich nagłówków lub pliki biblioteki.</span><span class="sxs-lookup"><span data-stu-id="b0397-110">This interface lives inside the runtime and isn't exposed through any headers or library files.</span></span> <span data-ttu-id="b0397-111">Jednak jest interfejsem COM, która pochodzi od klasy `IUnknown` o identyfikatorze GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` , można uzyskać za pośrednictwem zwykłych mechanizmów COM.</span><span class="sxs-lookup"><span data-stu-id="b0397-111">However, it's a COM interface that derives from `IUnknown` with GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="b0397-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0397-112">Requirements</span></span>

<span data-ttu-id="b0397-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0397-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="b0397-114">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="b0397-114">**Header:** None</span></span>

<span data-ttu-id="b0397-115">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="b0397-115">**Library:** None</span></span>

<span data-ttu-id="b0397-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0397-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b0397-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0397-117">See also</span></span>

- [<span data-ttu-id="b0397-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b0397-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b0397-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b0397-119">Debugging</span></span>](index.md)

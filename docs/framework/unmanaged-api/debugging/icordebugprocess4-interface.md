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
ms.openlocfilehash: fcf725ea98fa4351e72cf592f92968ee2233ecb0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213585"
---
# <a name="icordebugprocess4-interface"></a><span data-ttu-id="ebaa0-102">ICorDebugProcess4, interfejs</span><span class="sxs-lookup"><span data-stu-id="ebaa0-102">ICorDebugProcess4 Interface</span></span>

<span data-ttu-id="ebaa0-103">Zapewnia obsługę kontroli wykonywania poza procesem.</span><span class="sxs-lookup"><span data-stu-id="ebaa0-103">Provides support for out of process execution control.</span></span>

## <a name="methods"></a><span data-ttu-id="ebaa0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ebaa0-104">Methods</span></span>

| <span data-ttu-id="ebaa0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ebaa0-105">Method</span></span>                                                                 | <span data-ttu-id="ebaa0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ebaa0-106">Description</span></span>                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="ebaa0-107">ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="ebaa0-107">ProcessStateChanged</span></span>](icordebugprocess4-processstatechanged-method.md) | <span data-ttu-id="ebaa0-108">Powiadamia potok ICorDebug, że debuger out of process kontynuuje wykonywanie operacji debugee.</span><span class="sxs-lookup"><span data-stu-id="ebaa0-108">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span> |

## <a name="remarks"></a><span data-ttu-id="ebaa0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ebaa0-109">Remarks</span></span>

<span data-ttu-id="ebaa0-110">Ten interfejs jest wewnątrz środowiska uruchomieniowego i nie jest udostępniany przez żadne nagłówki lub pliki bibliotek.</span><span class="sxs-lookup"><span data-stu-id="ebaa0-110">This interface lives inside the runtime and isn't exposed through any headers or library files.</span></span> <span data-ttu-id="ebaa0-111">Jest to jednak interfejs COM pochodzący z `IUnknown` identyfikatora GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` , który można uzyskać za pomocą zwykłych mechanizmów com.</span><span class="sxs-lookup"><span data-stu-id="ebaa0-111">However, it's a COM interface that derives from `IUnknown` with GUID `E930C679-78AF-4953-8AB7-B0AABF0F9F80` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="ebaa0-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ebaa0-112">Requirements</span></span>

<span data-ttu-id="ebaa0-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebaa0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="ebaa0-114">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="ebaa0-114">**Header:** None</span></span>

<span data-ttu-id="ebaa0-115">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="ebaa0-115">**Library:** None</span></span>

<span data-ttu-id="ebaa0-116">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebaa0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ebaa0-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ebaa0-117">See also</span></span>

- [<span data-ttu-id="ebaa0-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="ebaa0-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ebaa0-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="ebaa0-119">Debugging</span></span>](index.md)

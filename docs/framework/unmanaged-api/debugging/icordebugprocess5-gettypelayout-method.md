---
title: ICorDebugProcess5::GetTypeLayout — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
ms.openlocfilehash: 306d881c05c2fcdb15a53a439bfce6eff3afffa8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792314"
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="1e3ef-102">ICorDebugProcess5::GetTypeLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="1e3ef-102">ICorDebugProcess5::GetTypeLayout Method</span></span>
<span data-ttu-id="1e3ef-103">Pobiera informacje o układzie obiektu w pamięci na podstawie jego identyfikatora typu.</span><span class="sxs-lookup"><span data-stu-id="1e3ef-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e3ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1e3ef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e3ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1e3ef-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="1e3ef-106">podczas Token [COR_TYPEID](cor-typeid-structure.md) , który określa typ, którego układ jest żądany.</span><span class="sxs-lookup"><span data-stu-id="1e3ef-106">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="1e3ef-107">określoną Wskaźnik do struktury [COR_TYPE_LAYOUT](cor-type-layout-structure.md) , która zawiera informacje o układzie obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="1e3ef-107">[out] A pointer to a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e3ef-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1e3ef-108">Remarks</span></span>  
 <span data-ttu-id="1e3ef-109">Metoda `ICorDebugProcess5::GetTypeLayout` zapewnia informacje o obiekcie na podstawie jego [COR_TYPEID](cor-typeid-structure.md), który jest zwracany przez wiele innych metod [ICorDebugProcess5](icordebugprocess5-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="1e3ef-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="1e3ef-110">Informacje są dostarczane przez strukturę [COR_TYPE_LAYOUT](cor-type-layout-structure.md) , która jest wypełniana przez metodę.</span><span class="sxs-lookup"><span data-stu-id="1e3ef-110">The information is provided by a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e3ef-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1e3ef-111">Requirements</span></span>  
 <span data-ttu-id="1e3ef-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e3ef-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e3ef-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1e3ef-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e3ef-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1e3ef-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e3ef-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e3ef-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e3ef-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e3ef-116">See also</span></span>

- [<span data-ttu-id="1e3ef-117">COR_TYPE_LAYOUT, struktura</span><span class="sxs-lookup"><span data-stu-id="1e3ef-117">COR_TYPE_LAYOUT Structure</span></span>](cor-type-layout-structure.md)
- [<span data-ttu-id="1e3ef-118">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="1e3ef-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="1e3ef-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1e3ef-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

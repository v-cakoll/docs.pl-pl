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
ms.openlocfilehash: 861af4ba9c6f4d4bdb16abb9d4e1fd79debac59b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205577"
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="be151-102">ICorDebugProcess5::GetTypeLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="be151-102">ICorDebugProcess5::GetTypeLayout Method</span></span>
<span data-ttu-id="be151-103">Pobiera informacje o układzie obiektu w pamięci na podstawie jego identyfikatora typu.</span><span class="sxs-lookup"><span data-stu-id="be151-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be151-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be151-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be151-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be151-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="be151-106">podczas Token [COR_TYPEID](cor-typeid-structure.md) , który określa typ, którego układ jest żądany.</span><span class="sxs-lookup"><span data-stu-id="be151-106">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="be151-107">określoną Wskaźnik do struktury [COR_TYPE_LAYOUT](cor-type-layout-structure.md) , która zawiera informacje o układzie obiektu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="be151-107">[out] A pointer to a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be151-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be151-108">Remarks</span></span>  
 <span data-ttu-id="be151-109">`ICorDebugProcess5::GetTypeLayout`Metoda zawiera informacje o obiekcie w oparciu o [COR_TYPEID](cor-typeid-structure.md), który jest zwracany przez wiele innych metod [ICorDebugProcess5](icordebugprocess5-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="be151-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="be151-110">Informacje są dostarczane przez strukturę [COR_TYPE_LAYOUT](cor-type-layout-structure.md) , która jest wypełniana przez metodę.</span><span class="sxs-lookup"><span data-stu-id="be151-110">The information is provided by a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be151-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be151-111">Requirements</span></span>  
 <span data-ttu-id="be151-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be151-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be151-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="be151-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be151-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="be151-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be151-115">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be151-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be151-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be151-116">See also</span></span>

- [<span data-ttu-id="be151-117">COR_TYPE_LAYOUT — Struktura</span><span class="sxs-lookup"><span data-stu-id="be151-117">COR_TYPE_LAYOUT Structure</span></span>](cor-type-layout-structure.md)
- [<span data-ttu-id="be151-118">ICorDebugProcess5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="be151-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="be151-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="be151-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

---
title: ICorDebugProcess5::GetArrayLayout — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
ms.openlocfilehash: ea7630efedb7b667dc58174eda0cb98d9f382cfc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792387"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="11da3-102">ICorDebugProcess5::GetArrayLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="11da3-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="11da3-103">Zawiera informacje na temat układu typów tablicowych.</span><span class="sxs-lookup"><span data-stu-id="11da3-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11da3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="11da3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11da3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="11da3-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="11da3-106">podczas Token [COR_TYPEID](cor-typeid-structure.md) , który określa tablicę, której układ jest żądany.</span><span class="sxs-lookup"><span data-stu-id="11da3-106">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="11da3-107">określoną Wskaźnik do struktury [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) , która zawiera informacje o układzie tablicy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="11da3-107">[out] A pointer to a [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11da3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11da3-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11da3-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11da3-109">Requirements</span></span>  
 <span data-ttu-id="11da3-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11da3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11da3-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="11da3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11da3-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="11da3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11da3-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11da3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11da3-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11da3-114">See also</span></span>

- [<span data-ttu-id="11da3-115">ICorDebugProcess5, interfejs</span><span class="sxs-lookup"><span data-stu-id="11da3-115">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="11da3-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="11da3-116">Debugging Interfaces</span></span>](debugging-interfaces.md)

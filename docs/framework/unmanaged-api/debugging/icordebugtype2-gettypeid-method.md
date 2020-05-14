---
title: 'ICorDebugType2:: GetTypeId — Metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
ms.openlocfilehash: 1c11946bc5ea69a090091c014aba859935b48b36
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396674"
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="bb160-102">ICorDebugType2:: GetTypeId — Metoda</span><span class="sxs-lookup"><span data-stu-id="bb160-102">ICorDebugType2::GetTypeID Method</span></span>
<span data-ttu-id="bb160-103">Pobiera [COR_TYPEID](cor-typeid-structure.md) dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="bb160-103">Gets a [COR_TYPEID](cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb160-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb160-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb160-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb160-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="bb160-106">określoną Wskaźnik do [COR_TYPEID](cor-typeid-structure.md) dla tego ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="bb160-106">[out] A pointer to the [COR_TYPEID](cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb160-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bb160-107">Return Value</span></span>  
 <span data-ttu-id="bb160-108">Wartość zwracana jest `S_OK` w przypadku powodzenia lub `HRESULT` Kod błędu w przypadku niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="bb160-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="bb160-109">`HRESULT`Kody obejmują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="bb160-109">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="bb160-110">Kod powrotu</span><span class="sxs-lookup"><span data-stu-id="bb160-110">Return code</span></span>|<span data-ttu-id="bb160-111">Opis</span><span class="sxs-lookup"><span data-stu-id="bb160-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="bb160-112">Metoda powiodła się.</span><span class="sxs-lookup"><span data-stu-id="bb160-112">Method succeeded.</span></span> <span data-ttu-id="bb160-113">Metoda pobrała prawidłowy [COR_TYPEID](cor-typeid-structure.md).</span><span class="sxs-lookup"><span data-stu-id="bb160-113">The method has retrieved a valid [COR_TYPEID](cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="bb160-114">Typ nie został załadowany.</span><span class="sxs-lookup"><span data-stu-id="bb160-114">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="bb160-115">Typ nie jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="bb160-115">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb160-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb160-116">Remarks</span></span>  
 <span data-ttu-id="bb160-117">Ta metoda zapewnia mapowanie od ICorDebugType, który reprezentuje typ, który może lub nie został załadowany do środowiska uruchomieniowego, do [COR_TYPEID](cor-typeid-structure.md), który służy jako uchwyt nieprzezroczysty, który identyfikuje typ załadowany do środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="bb160-117">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="bb160-118">Gdy typ, który ICorDebugType reprezentuje, nie został jeszcze załadowany, Metoda ta zwraca wartość `CORDBG_E_CLASS_NOT_LOADED` .</span><span class="sxs-lookup"><span data-stu-id="bb160-118">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="bb160-119">Jeśli typ nie jest obsługiwany, zwraca `CORDBG_E_UNSUPPORTED` .</span><span class="sxs-lookup"><span data-stu-id="bb160-119">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb160-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb160-120">Requirements</span></span>  
 <span data-ttu-id="bb160-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb160-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb160-122">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bb160-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb160-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bb160-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb160-124">**.NET Framework wersje:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb160-124">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb160-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb160-125">See also</span></span>

- [<span data-ttu-id="bb160-126">ICorDebugType2, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb160-126">ICorDebugType2 Interface</span></span>](icordebugtype2-interface.md)

---
title: ICorDebugArrayValue::HasBaseIndicies — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.HasBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type:
- apiref
ms.openlocfilehash: e6e8eb91bbc41faf0dcea010da9aa54995058653
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894980"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="3a4d2-102">ICorDebugArrayValue::HasBaseIndicies — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a4d2-102">ICorDebugArrayValue::HasBaseIndicies Method</span></span>
<span data-ttu-id="3a4d2-103">Pobiera wartość wskazującą, czy wszystkie wymiary tej tablicy mają indeks podstawowy różny od zera.</span><span class="sxs-lookup"><span data-stu-id="3a4d2-103">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a4d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a4d2-104">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a4d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a4d2-105">Parameters</span></span>  
 `pbHasBaseIndicies`  
 <span data-ttu-id="3a4d2-106">określoną Wskaźnik do wartości logicznej, która jest `true` , jeśli co najmniej jeden wymiar tego `ICorDebugArrayValue` obiektu ma indeks podstawowy różny od zera. w przeciwnym razie wartość logiczna to `false`.</span><span class="sxs-lookup"><span data-stu-id="3a4d2-106">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a4d2-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a4d2-107">Requirements</span></span>  
 <span data-ttu-id="3a4d2-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a4d2-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a4d2-109">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3a4d2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a4d2-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3a4d2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a4d2-111">**.NET Framework wersje:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a4d2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>

---
title: ICorDebugStringValue::GetLength — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetLength
helpviewer_keywords:
- ICorDebugStringValue::GetLength method [.NET Framework debugging]
- GetLength method [.NET Framework debugging]
ms.assetid: a1ebfc69-46a6-4225-8788-b7cfb2f15e1d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e62539304817432fcab8f3e0958e5a70b371b83d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416950"
---
# <a name="icordebugstringvaluegetlength-method"></a><span data-ttu-id="64cf2-102">ICorDebugStringValue::GetLength — Metoda</span><span class="sxs-lookup"><span data-stu-id="64cf2-102">ICorDebugStringValue::GetLength Method</span></span>
<span data-ttu-id="64cf2-103">Pobiera liczbę znaków w ciągu odwołuje się ten ICorDebugStringValue.</span><span class="sxs-lookup"><span data-stu-id="64cf2-103">Gets the number of characters in the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64cf2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="64cf2-104">Syntax</span></span>  
  
```  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64cf2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="64cf2-105">Parameters</span></span>  
 `pcchString`  
 <span data-ttu-id="64cf2-106">[out] Wskaźnik do wartości, który określa długość ciągu to odwołuje `ICorDebugStringValue` obiektu.</span><span class="sxs-lookup"><span data-stu-id="64cf2-106">[out] A pointer to a value that specifies the length of the string referenced by this `ICorDebugStringValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64cf2-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="64cf2-107">Requirements</span></span>  
 <span data-ttu-id="64cf2-108">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64cf2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64cf2-109">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64cf2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64cf2-110">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64cf2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64cf2-111">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64cf2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

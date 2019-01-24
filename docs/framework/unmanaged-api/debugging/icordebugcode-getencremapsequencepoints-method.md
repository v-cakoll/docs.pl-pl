---
title: ICorDebugCode::GetEnCRemapSequencePoints — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetEnCRemapSequencePoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetEnCRemapSequencePoints
helpviewer_keywords:
- GetEnCRemapSequencePoints method [.NET Framework debugging]
- ICorDebugCode::GetEnCRemapSequencePoints method [.NET Framework debugging]
ms.assetid: 8463a98a-de4a-418e-beb0-9611885ae6b0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bea6b11437367d5ba14167d9800f6c43e117d548
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533328"
---
# <a name="icordebugcodegetencremapsequencepoints-method"></a><span data-ttu-id="49dd8-102">ICorDebugCode::GetEnCRemapSequencePoints — Metoda</span><span class="sxs-lookup"><span data-stu-id="49dd8-102">ICorDebugCode::GetEnCRemapSequencePoints Method</span></span>
<span data-ttu-id="49dd8-103">Ta metoda nie jest zaimplementowana w bieżącej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="49dd8-103">This method is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49dd8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="49dd8-104">Syntax</span></span>  
  
```  
HRESULT GetEnCRemapSequencePoints(  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        ULONG32 offsets[]  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="49dd8-105">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49dd8-105">See also</span></span>


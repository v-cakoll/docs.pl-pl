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
ms.openlocfilehash: fd0607f2523e6f05065acc0078f4cb2848afd928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugcodegetencremapsequencepoints-method"></a><span data-ttu-id="d4514-102">ICorDebugCode::GetEnCRemapSequencePoints — Metoda</span><span class="sxs-lookup"><span data-stu-id="d4514-102">ICorDebugCode::GetEnCRemapSequencePoints Method</span></span>
<span data-ttu-id="d4514-103">Ta metoda nie jest zaimplementowana w bieżącej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d4514-103">This method is not implemented in the current version of the .NET Framework.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4514-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4514-104">Syntax</span></span>  
  
```  
HRESULT GetEnCRemapSequencePoints(  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        ULONG32 offsets[]  
);  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4514-105">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4514-105">See Also</span></span>  
 

---
title: "ICorDebugObjectValue2::GetVirtualMethodAndType — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue2.GetVirtualMethodAndType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue2::GetVirtualMethodAndType
helpviewer_keywords:
- GetVirtualMethodAndType method [.NET Framework debugging]
- ICorDebugObjectValue2::GetVirtualMethodAndType method
ms.assetid: 621b4543-a8f7-4117-98e4-930992cd688a
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae45088a95b887e10fef66b5c6feab57393c6c29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectvalue2getvirtualmethodandtype-method"></a>ICorDebugObjectValue2::GetVirtualMethodAndType — Metoda
Ta metoda nie została jeszcze zaimplementowana.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetVirtualMethodAndType (  
    [in] mdMemberRef          memberRef,  
    [out] ICorDebugFunction   **ppFunction,  
    [out] ICorDebugType       **ppType  
);  
```  
  
## <a name="remarks"></a>Uwagi  
 Pobiera interfejs wskaźników do wystąpień "ICorDebugFunction" i "ICorDebugType", które reprezentują najbardziej pochodnej metody i typu dla odwołania do określonego elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
    
 

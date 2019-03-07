---
title: EndMerge — Metoda
ms.date: 03/30/2017
api_name:
- IALink.EndMerge
- EndMerge
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EndMerge
helpviewer_keywords:
- EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d4b102485db0199f748f6c5b6c4ab40d21429e9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494418"
---
# <a name="endmerge-method"></a>EndMerge — Metoda
Wskazuje, że wszystkie atrybuty niestandardowe zostały scalone w zakresie emitowanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Identyfikator zestawu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h  
  
## <a name="see-also"></a>Zobacz także
- [IALink, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink, interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)

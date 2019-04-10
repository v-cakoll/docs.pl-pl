---
title: EmitAssembly — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf7b54ab7a2318e8194bf39dbe41b864633ddb43
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212914"
---
# <a name="emitassembly-method"></a>EmitAssembly — Metoda
Tworzy zestaw. Wywołaj tę metodę po zamknięciu wszystkich innych plików z wyjątkiem pliku zestawu. Ta metoda zostanie wywołana podczas produkowania niepowiązanych modułów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EmitAssembly(  
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

- [IALink — Interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 — Interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink — interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)

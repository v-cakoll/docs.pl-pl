---
title: ISymUnmanagedDispose::Destroy — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose.Destroy
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 51d2f0aedffdd88974a8184954ecbb9a231b70c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59213681"
---
# <a name="isymunmanageddisposedestroy-method"></a>ISymUnmanagedDispose::Destroy — Metoda
Powoduje, że obiekt jest zwolnienie wszystkich odwołań wewnętrznego i zwraca błąd na dowolne wywołania metody kolejne.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedDispose — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)

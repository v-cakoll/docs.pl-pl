---
title: ISymUnmanagedScope2::GetConstantCount — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstantCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d1dfc9ead6256ae700d5e619da4fae5745bdd759
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485161"
---
# <a name="isymunmanagedscope2getconstantcount-method"></a>ISymUnmanagedScope2::GetConstantCount — Metoda
Pobiera liczbę stałe zdefiniowane w tym zakresie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Wskaźnik do `ULONG32` rozmiar, który odbiera w postaci, buforu, muszą zawierać stałe.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także
- [ISymUnmanagedScope2, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)

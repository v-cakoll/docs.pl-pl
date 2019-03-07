---
title: ISymUnmanagedVariable::GetAddressKind — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressKind
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8b45cda05a386efef320d2caad0ed241a4767b9c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484852"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a>ISymUnmanagedVariable::GetAddressKind — Metoda
Pobiera rodzaj adres tej zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Wskaźnik do `ULONG32` , która otrzymuje wartość. Możliwe wartości są zdefiniowane w [corsymaddrkind —](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) wyliczenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także
- [ISymUnmanagedVariable, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)

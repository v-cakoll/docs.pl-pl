---
title: ISymUnmanagedVariable::GetSignature — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetSignature method [.NET Framework debugging]
ms.assetid: 78c1ba28-a410-4360-805c-23a95408964a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3cc616246812bb9643388d8ad57cf84bc387b55e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136425"
---
# <a name="isymunmanagedvariablegetsignature-method"></a>ISymUnmanagedVariable::GetSignature — Metoda
Pobiera podpis tej zmiennej.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cSig`  
 [in] Długość buforu wskazywany przez `sig` parametru.  
  
 `pcSig`  
 [out] Wskaźnik do `ULONG32` rozmiar, który odbiera w postaci, buforu, muszą zawierać podpis.  
  
 `sig`  
 [out] Bufor, który przechowuje podpisu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedVariable — Interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)

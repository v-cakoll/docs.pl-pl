---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f068b4cae3832802ab53404d35a5a30673cd967d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561858"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a>ISymUnmanagedENCUpdate::GetLocalVariableCount — Metoda
Pobiera liczbę zmiennych lokalnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mdMethodToken`  
 [in] Token metadanych z metod.  
  
 `pcLocals`  
 [out] Wskaźnik do `ULONG32` rozmiar, który odbiera w postaci, buforu, muszą zawierać liczbę zmiennych lokalnych.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także
- [ISymUnmanagedENCUpdate, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

---
title: ISymUnmanagedENCUpdate::GetLocalVariables — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16e91a0c748e5b148e79dc73cf213b03c68c5021
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59103756"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a>ISymUnmanagedENCUpdate::GetLocalVariables — Metoda
Pobiera zmienne lokalne.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a>Parametry  
 `mdMethodToken`  
 [in] Token metadanych metody.  
  
 `cLocals`  
 [in] A `ULONG` oznacza rozmiar `rgLocals` parametru.  
  
 `rgLocals`  
 [out] Tablica zwrócona [isymunmanagedvariable —](isymunmanagedvariable-interface.md) wystąpień.  
  
 `pceltFetched`  
 [out] Wskaźnik do `ULONG` wielkości, która otrzymuje `rgLocals` buforu, muszą zawierać zmienne lokalne.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedENCUpdate, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

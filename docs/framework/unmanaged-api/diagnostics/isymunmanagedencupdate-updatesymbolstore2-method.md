---
title: ISymUnmanagedENCUpdate::UpdateSymbolStore2 — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 78d9e27299c9d7ed7d6cb9b09dd659ba081c5fde
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45616065"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a>ISymUnmanagedENCUpdate::UpdateSymbolStore2 — Metoda
Umożliwia kompilatorowi pominąć funkcje, które nie zostały zmodyfikowane ze strumienia bazy danych (PDB) programu, pod warunkiem informacje wiersza spełnia wymagania. Informacje wiersza poprawne można ustalić przy użyciu starych informacji PDB w wierszu i jeden różnicowej dla wszystkich wierszy w funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pIStream`  
 [in] Wskaźnik do [IStream](/windows/desktop/api/objidl/nn-objidl-istream) zawierający informacje wiersza.  
  
 `pDeltaLines`  
 [in] Wskaźnik do [symlinedelta —](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) strukturę, która zawiera wiersze, które uległy zmianie.  
  
 `cDeltaLines`  
 [in] A `ULONG` reprezentujący liczbę wierszy, które uległy zmianie.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [ISymUnmanagedENCUpdate, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

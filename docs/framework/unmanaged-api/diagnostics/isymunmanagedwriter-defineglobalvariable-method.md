---
title: ISymUnmanagedWriter::DefineGlobalVariable — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
ms.openlocfilehash: 94d1aa5bba87e8ca11b58bdf89a697e1ccf500b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428026"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a>ISymUnmanagedWriter::DefineGlobalVariable — Metoda
Definiuje pojedynczą zmienną globalną.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 podczas Wskaźnik do `WCHAR`, który definiuje globalną nazwę zmiennej.  
  
 `attributes`  
 podczas Atrybuty zmiennej globalnej.  
  
 `cSig`  
 podczas `ULONG32`, który wskazuje rozmiar (w znakach) bufora `signature`.  
  
 `signature`  
 podczas Podpis zmiennej globalnej.  
  
 `addrKind`  
 podczas Typ adresu.  
  
 `addr1`  
 podczas Pierwszy adres dla specyfikacji parametru.  
  
 `addr2`  
 podczas Drugi adres dla specyfikacji parametru.  
  
 `addr3`  
 podczas Trzeci adres dla specyfikacji parametru.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [DefineLocalVariable, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)
- [DefineGlobalVariable2, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineglobalvariable2-method.md)

---
title: ISymUnmanagedWriter::DefineLocalVariable — Metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineLocalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineLocalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineLocalVariable method [.NET Framework debugging]
- DefineLocalVariable method [.NET Framework debugging]
ms.assetid: 6fab8a58-3883-490f-8b27-64042c90f104
topic_type:
- apiref
ms.openlocfilehash: f6a741df3ea57b5e9b4fa8bc5d304bfedd1d6c15
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428009"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>ISymUnmanagedWriter::DefineLocalVariable — Metoda
Definiuje pojedynczą zmienną w bieżącym zakresie leksykalnym. Tę metodę można wywołać wiele razy dla zmiennej o tej samej nazwie, która ma wiele domów w całym zakresie. Jednak w takim przypadku wartości `startOffset` i `endOffset` parametrów nie mogą nakładać się na siebie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DefineLocalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3,  
    [in] ULONG32      startOffset,  
    [in] ULONG32      endOffset);  
```  
  
## <a name="parameters"></a>Parametry  
 `name`  
 podczas Wskaźnik do `WCHAR`, który definiuje nazwę zmiennej lokalnej.  
  
 `attributes`  
 podczas Atrybuty zmiennej lokalnej.  
  
 `cSig`  
 podczas `ULONG32` wskazujący rozmiar buforu `signature` w bajtach.  
  
 `signature`  
 podczas Podpis zmiennej lokalnej.  
  
 `addrKind`  
 podczas Typ adresu.  
  
 `addr1`  
 podczas Pierwszy adres dla specyfikacji parametru.  
  
 `addr2`  
 podczas Drugi adres dla specyfikacji parametru.  
  
 `addr3`  
 podczas Trzeci adres dla specyfikacji parametru.  
  
 `startOffset`  
 podczas Przesunięcie początkowe dla zmiennej. Ten parametr jest opcjonalny. Jeśli wartość jest równa 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym zakresie. Jeśli jest to wartość różna od zera, zmienna znajduje się w przesunięciach bieżącego zakresu.  
  
 `endOffset`  
 podczas Przesunięcie końcowe dla zmiennej. Ten parametr jest opcjonalny. Jeśli wartość jest równa 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym zakresie. Jeśli jest to wartość różna od zera, zmienna znajduje się w przesunięciach bieżącego zakresu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub inny kod błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [DefineGlobalVariable, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
- [DefineLocalVariable2, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)

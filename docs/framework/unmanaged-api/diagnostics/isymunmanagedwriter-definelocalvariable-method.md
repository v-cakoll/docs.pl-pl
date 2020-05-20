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
ms.openlocfilehash: 5730cdd910257d762230f5e54576d5e0a7ac1adb
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614828"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>ISymUnmanagedWriter::DefineLocalVariable — Metoda
Definiuje pojedynczą zmienną w bieżącym zakresie leksykalnym. Tę metodę można wywołać wiele razy dla zmiennej o tej samej nazwie, która ma wiele domów w całym zakresie. Jednak w takim przypadku wartości `startOffset` `endOffset` parametrów i nie mogą nakładać się na siebie.  
  
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
 podczas Wskaźnik do elementu `WCHAR` , który definiuje nazwę zmiennej lokalnej.  
  
 `attributes`  
 podczas Atrybuty zmiennej lokalnej.  
  
 `cSig`  
 podczas `ULONG32`Wskazuje rozmiar bufora (w bajtach) `signature` .  
  
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

- [ISymUnmanagedWriter — Interfejs](isymunmanagedwriter-interface.md)
- [DefineGlobalVariable, metoda](isymunmanagedwriter-defineglobalvariable-method.md)
- [DefineLocalVariable2, metoda](isymunmanagedwriter2-definelocalvariable2-method.md)

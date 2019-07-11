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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9466df3f6413f86eb8558f0037b96c254b2a2e1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777341"
---
# <a name="isymunmanagedwriterdefinelocalvariable-method"></a>ISymUnmanagedWriter::DefineLocalVariable — Metoda
Definiuje pojedynczą zmienną w bieżącym zakresie leksykalnym. Tę metodę można wywoływać wielokrotnie dla zmiennej o tej samej nazwie, który ma wiele domów w całym zakresie. W takim jednak wartości `startOffset` i `endOffset` parametry nie mogą się nakładać.  
  
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
 [in] Wskaźnik do `WCHAR` definiujący lokalna nazwa zmiennej.  
  
 `attributes`  
 [in] Lokalne atrybuty zmiennej.  
  
 `cSig`  
 [in] A `ULONG32` rozmiar w bajtach, który wskazuje z `signature` buforu.  
  
 `signature`  
 [in] Sygnatura lokalna zmienna.  
  
 `addrKind`  
 [in] Typ adresu.  
  
 `addr1`  
 [in] Pierwszy adres specyfikację parametru.  
  
 `addr2`  
 [in] Drugi adres specyfikację parametru.  
  
 `addr3`  
 [in] Trzeci adres specyfikację parametru.  
  
 `startOffset`  
 [in] Przesunięcie początku dla zmiennej. Ten parametr jest opcjonalny. Jeśli jest 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym cały zakres. Jeśli jest wartość różną od zera, zmienna mieści się w przesunięcia bieżącego zakresu.  
  
 `endOffset`  
 [in] Przesunięcie zakończenia dla zmiennej. Ten parametr jest opcjonalny. Jeśli jest 0, ten parametr jest ignorowany, a zmienna jest zdefiniowana w całym cały zakres. Jeśli jest wartość różną od zera, zmienna mieści się w przesunięcia bieżącego zakresu.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda się powiedzie; w przeciwnym razie E_FAIL lub innego kodu błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz także

- [ISymUnmanagedWriter, interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [DefineGlobalVariable, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)
- [DefineLocalVariable2, metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-definelocalvariable2-method.md)

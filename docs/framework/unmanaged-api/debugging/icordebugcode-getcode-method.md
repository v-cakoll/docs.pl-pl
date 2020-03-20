---
title: ICorDebugCode::GetCode — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
ms.openlocfilehash: fde76c3b34fcc9f2321f3426d2801b310f681067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178997"
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode — Metoda
Pobiera cały kod dla określonej funkcji, sformatowany do demontażu. Ta metoda została przestarzała w .NET Framework w wersji 2.0. Zamiast tego użyj [funkcji ICorDebugCode2::GetCodeChunks.](icordebugcode2-getcodechunks-method.md)  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCode (  
    [in] ULONG32     startOffset,
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `startOffset`  
 [w] Przesunięcie początku funkcji.  
  
 `endOffset`  
 [w] Przesunięcie końca funkcji.  
  
 `cBufferAlloc`  
 [w] Rozmiar tablicy, `buffer` do której zostanie zwrócony kod.  
  
 `buffer`  
 [na zewnątrz] Tablica, do której zostanie zwrócony kod.  
  
 `pcBufferSize`  
 [na zewnątrz] Liczba zwracanych bajtów.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli kod funkcji został podzielony na wiele fragmentów, są one łączone w kolejności zwiększania natywnego odsunięcia. Granice instrukcji nie są sprawdzane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Zobacz też

- [GetCodeChunks, metoda](icordebugcode2-getcodechunks-method.md)

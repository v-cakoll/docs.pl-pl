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
ms.openlocfilehash: 14a72e4622aac09840e43f8bcdcf8a8c8d6e6892
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777914"
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode — Metoda
Pobiera cały kod dla określonej funkcji, sformatowany pod kątem demontażu. Ta metoda jest przestarzała w .NET Framework w wersji 2,0. Zamiast tego użyj [ICorDebugCode2:: GetCodeChunks —](icordebugcode2-getcodechunks-method.md) .  
  
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
 podczas Przesunięcie początku funkcji.  
  
 `endOffset`  
 podczas Przesunięcie końca funkcji.  
  
 `cBufferAlloc`  
 podczas Rozmiar tablicy `buffer`, do której zostanie zwrócony kod.  
  
 `buffer`  
 określoną Tablica, do której zostanie zwrócony kod.  
  
 `pcBufferSize`  
 określoną Liczba zwróconych bajtów.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli kod funkcji został podzielony na wiele fragmentów, są one łączone w kolejności rosnącego przesunięcia natywnego. Granice instrukcji nie są zaznaczone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:** 1,1, 1,0  
  
## <a name="see-also"></a>Zobacz także

- [GetCodeChunks, metoda](icordebugcode2-getcodechunks-method.md)

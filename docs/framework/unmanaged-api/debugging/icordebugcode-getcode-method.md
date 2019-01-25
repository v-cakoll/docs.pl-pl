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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d057032f2a46ef29a903ae21ab13af02f9d657f1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728768"
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode — Metoda
Pobiera cały kod dla określonej funkcji, sformatowane, aby dezasemblacji. Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0. Użyj [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCode (  
    [in] ULONG32     startOffset,   
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `startOffset`  
 [in] Przesunięcie początku funkcji.  
  
 `endOffset`  
 [in] Przesunięcia końca funkcji.  
  
 `cBufferAlloc`  
 [in] Rozmiar `buffer` tablicy, do której zostanie zwrócony kod.  
  
 `buffer`  
 [out] Tablica, do którego zostanie zwrócony kod.  
  
 `pcBufferSize`  
 [out] Liczba bajtów zwróconych.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli kod funkcji został podzielony na wiele fragmentów, są one łączone w celu zwiększenia przesunięciu macierzystym. Instrukcja granice nie są sprawdzane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Zobacz także
- [GetCodeChunks, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)


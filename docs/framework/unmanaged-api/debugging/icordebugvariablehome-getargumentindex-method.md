---
title: 'ICorDebugVariableHome:: GetArgumentIndex, Metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
ms.openlocfilehash: 12d4e63480f03bfad613f30362ddaeaf12b57a88
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791050"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a>ICorDebugVariableHome:: GetArgumentIndex, Metoda

Pobiera indeks argumentu funkcji.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a>Parametry

`pArgumentIndex`\
określoną Wskaźnik do indeksu argumentów.

## <a name="return-value"></a>Wartość zwrócona

Metoda zwraca następujące wartości.

|Wartość|Opis|
|-----------|-----------------|
|`S_OK`|Wywołanie metody zwróciło prawidłowy indeks argumentu.|
|`E_FAIL`|Bieżące wystąpienie [ICorDebugVariableHome](icordebugvariablehome-interface.md) reprezentuje zmienną lokalną.|

## <a name="remarks"></a>Uwagi

Indeks argumentu może służyć do pobierania metadanych dla tego argumentu.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** CorDebug. idl, CorDebug. h

**Biblioteka:** CorGuids. lib

**Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICorDebugVariableHome, interfejs](icordebugvariablehome-interface.md)

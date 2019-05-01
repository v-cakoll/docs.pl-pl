---
title: Metoda ICorDebugVariableHome::GetArgumentIndex
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2457dff3063e47f1fb9d040caac1bc08441e1739
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986794"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a>Metoda ICorDebugVariableHome::GetArgumentIndex

Pobiera indeks argumentu funkcji.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a>Parametry

`pArgumentIndex`\
[out] Wskaźnik do indeksu argumentu.

## <a name="return-value"></a>Wartość zwracana

Metoda zwraca następujące wartości.

|Wartość|Opis|
|-----------|-----------------|
|`S_OK`|Wywołanie metody zwracane indeksu nieprawidłowy argument.|
|`E_FAIL`|Bieżący [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpienie reprezentuje zmienną lokalną.|

## <a name="remarks"></a>Uwagi

Indeks argument może służyć do pobierania metadanych dla tego argumentu.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** CorDebug.idl, CorDebug.h

**Biblioteka:** CorGuids.lib

**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICorDebugVariableHome, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)

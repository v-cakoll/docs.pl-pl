---
title: ICorDebugProcess2::GetVersion — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 interface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type:
- apiref
ms.openlocfilehash: 391b848d3b3f66f6af6bf3adbefb6e94d526e748
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213507"
---
# <a name="icordebugprocess2getversion-method"></a>ICorDebugProcess2::GetVersion — Metoda

Pobiera numer wersji środowiska uruchomieniowego języka wspólnego (CLR), który jest uruchomiony w tym procesie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a>Parametry

`version`\
określoną Wskaźnik do struktury COR_VERSION, w której jest przechowywany numer wersji środowiska uruchomieniowego.

## <a name="remarks"></a>Uwagi

`GetVersion`Metoda zwraca kod błędu, jeśli nie załadowano środowiska uruchomieniowego w procesie.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** CorDebug. idl, CorDebug. h

**Biblioteka:** CorGuids. lib

**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

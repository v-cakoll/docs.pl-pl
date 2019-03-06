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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07f3be81431201a4bb6011ea9b8f973061d3d101
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361242"
---
# <a name="icordebugprocess2getversion-method"></a>ICorDebugProcess2::GetVersion — Metoda

Pobiera numer wersji środowisko uruchomieniowe języka wspólnego (CLR), który jest uruchomiony w ramach tego procesu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a>Parametry

`version`\
[out] Wskaźnik do cor_version — struktura, która przechowuje numer wersji środowiska uruchomieniowego.

## <a name="remarks"></a>Uwagi

`GetVersion` Metoda zwraca kod błędu, jeśli nie środowiska wykonawczego został załadowany w procesie.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** CorDebug.idl, CorDebug.h

**Biblioteka:** CorGuids.lib

**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

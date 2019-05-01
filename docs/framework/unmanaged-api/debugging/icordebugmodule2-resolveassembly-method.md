---
title: ICorDebugModule2::ResolveAssembly — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd899422287d34407778f67e5b4dfd2f33ffd00c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994828"
---
# <a name="icordebugmodule2resolveassembly-method"></a>ICorDebugModule2::ResolveAssembly — Metoda

Usuwa zestaw odwołuje się token określonych metadanych.

## <a name="syntax"></a>Składnia

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a>Parametry

`tkAssemblyRef`\
[in] `mdToken` Wartość, która odwołuje się do zestawu.

`ppAssembly`\
[out] Wskaźnik na adres obiektu ICorDebugAssembly, który reprezentuje zestaw.

## <a name="remarks"></a>Uwagi

Jeśli zestaw nie jest już załadowany gdy `ResolveAssembly` nosi nazwę, wartość HRESULT zostanie zwrócona wartość CORDBG_E_CANNOT_RESOLVE_ASSEMBLY.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** CorDebug.idl, CorDebug.h

**Biblioteka:** CorGuids.lib

**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

---
title: ICorDebugRegisterSet2::SetRegisters — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2.SetRegisters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2::SetRegisters
helpviewer_keywords:
- ICorDebugRegisterSet2::SetRegisters method [.NET Framework debugging]
- SetRegisters method, ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: fe0ac7e7-c9e1-4ec1-9f4e-1c56d63d73ac
topic_type:
- apiref
ms.openlocfilehash: 2dce97db3d209c51270a51ae92e9dce0b6861998
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792000"
---
# <a name="icordebugregisterset2setregisters-method"></a>ICorDebugRegisterSet2::SetRegisters — Metoda
`SetRegisters` nie została zaimplementowana w .NET Framework wersji 2,0. Nie wywołuj tej metody.  
  
> [!NOTE]
> Użyj operacji wyższego poziomu, takich jak [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) lub [ICorDebugNativeFrame:: SetIP](icordebugnativeframe-setip-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetRegisters (  
    [in] ULONG32 maskCount,  
    [in, size_is(maskCount)] BYTE mask[],  
    [in] ULONG32 regCount,  
    [in, size_is(regCount)] CORDB_REGISTER regBuffer[]  
);  
```  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugRegisterSet2, interfejs](icordebugregisterset2-interface.md)
- [ICorDebugRegisterSet, interfejs](icordebugregisterset-interface.md)

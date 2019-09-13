---
title: Wyliczenie ILCodeKind
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fea08331fffb85c91721d60764bae8bfe8b30e27
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928813"
---
# <a name="ilcodekind-enumeration"></a>Wyliczenie ILCodeKind
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Zawiera wartości, które określają, czy debuger może uzyskać dostęp do zmiennych lokalnych lub kodu dodanego w instrumentacji profilera ReJIT.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Nazwa elementu członkowskiego|Opis|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|Debuger nie ma dostępu do informacji z Instrumentacji ReJIT.|  
|`ILCODE_REJIT_IL`|Debuger ma dostęp do informacji z Instrumentacji ReJIT.|  
  
## <a name="remarks"></a>Uwagi  
 Element członkowski `ILCodeKind` wyliczenia można przesłać do [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) i [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) metod, aby określić, czy debuger może uzyskać dostęp do zmiennych dodanych w instrumentacji profilera ReJIT oraz do [ GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) metodę, aby określić, czy debuger może uzyskać dostęp do instrumentu Il.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [ICorDebugILFrame4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [ReJIT: Przewodnik krok po kroku](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)

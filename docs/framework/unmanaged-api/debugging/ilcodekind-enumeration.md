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
ms.openlocfilehash: 0881b3903200c023cfa2fe32bf89f62234da29c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424030"
---
# <a name="ilcodekind-enumeration"></a>Wyliczenie ILCodeKind
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Zawiera wartości, które określają, czy debuger jest w stanie uzyskać dostęp do zmiennych lokalnych lub kodzie dodanym w ReJIT Instrumentacji profilera.  
  
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
|`ILCODE_ORIGINAL_IL`|Debuger nie ma dostępu do informacji z ReJIT instrumentacji.|  
|`ILCODE_REJIT_IL`|Debuger ma dostęp do informacji z ReJIT instrumentacji.|  
  
## <a name="remarks"></a>Uwagi  
 Członek `ILCodeKind` wyliczenia mogą zostać przekazane do [EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) i [GetLocalVariableEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) metod umożliwiających ustalenie, czy debuger może uzyskiwać dostęp do zmiennych dodany do programu profiler Instrumentacja ReJIT i [GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) metodę, aby określić, czy debuger może uzyskiwać dostęp do Instrumentacji IL.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [ICorDebugILFrame4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 [ReJIT: Przewodnik](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)

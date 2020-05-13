---
title: Interfejs ICorDebugILFrame4
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
ms.openlocfilehash: d0b1c31d45efea4892182c43c801112530361994
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213705"
---
# <a name="icordebugilframe4-interface"></a>Interfejs ICorDebugILFrame4
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Zapewnia metody umożliwiające dostęp do zmiennych lokalnych i kodu w ramce stosu kodu języka pośredniego (IL). Parametr określa, czy debuger ma dostęp do zmiennych i kodu dodanych w Instrumentacji ReJIT profilera.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateLocalVariablesEx, metoda](icordebugilframe4-enumeratelocalvariablesex-method.md)|Zwraca listę zmiennych lokalnych dostępnych w bieżącej klatce.|  
|[GetCodeEx, metoda](icordebugilframe4-getcodeex-method.md)|Zwraca kod, w którym jest uruchomiona ta ramka stosu.|  
|[GetLocalVariableEx, metoda](icordebugilframe4-getlocalvariableex-method.md)|Zwraca wartość zmiennej lokalnej w ramce IL.|  
  
## <a name="remarks"></a>Uwagi  
 Te metody oferują funkcje oprócz tych zapewnianych przez metody [EnumerateLocalVariables —](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md)i [GetLocalVariable —](icordebugilframe-getlocalvariable-method.md) . Każda metoda zawiera `flags` parametr, który określa, czy są widoczne dodatkowe zmienne lokalne lub kod zdefiniowany przez żądanie ReJIT profilera.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)

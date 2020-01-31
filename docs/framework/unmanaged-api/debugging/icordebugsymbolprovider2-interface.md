---
title: ICorDebugSymbolProvider2, interfejs
ms.date: 03/30/2017
ms.assetid: 1c9c3d92-f0de-4d4d-87f1-0c702a4808af
ms.openlocfilehash: ca5bb822be515c936560eb4888c72ea306888ff3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791488"
---
# <a name="icordebugsymbolprovider2-interface"></a>ICorDebugSymbolProvider2, interfejs
Logicznie rozszerza interfejs [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) w celu pobrania dodatkowych informacji o symbolach debugowania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetFrameProps, metoda](icordebugsymbolprovider2-getframeprops-method.md)|Zwraca metodę rozpoczynającą względny adres wirtualny metody i ramkę nadrzędną, w której znajduje się adres wirtualny względem kodu.|  
|[GetGenericDictionaryInfo, metoda](icordebugsymbolprovider2-getgenericdictionaryinfo-method.md)|Pobiera mapę ogólnego słownika.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs jest dostępny tylko dla .NET Native. W przypadku zaimplementowania tego interfejsu dla scenariuszy ICorDebug poza .NET Native, środowisko uruchomieniowe języka wspólnego zignoruje ten interfejs.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugSymbolProvider, interfejs](icordebugsymbolprovider-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)

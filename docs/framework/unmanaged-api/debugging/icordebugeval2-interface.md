---
title: ICorDebugEval2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2
helpviewer_keywords: ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: fce34531-2687-406d-9131-d6ad94f2ce0e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fbcf36ff7aca84299c55083b4ae135ce0a9ec4f3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugeval2-interface1"></a>ICorDebugEval2 Interface1
Rozszerza "ICorDebugEval" Aby zapewnić obsługę dla typów ogólnych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CallParameterizedFunction — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)|Konfiguruje wywołanie do określonego "ICorDebugFunction", które mogą być zagnieżdżone wewnątrz typu, których konstruktora przyjmuje parametry typu lub mogą się zająć parametrów typu.|  
|[CreateValueForType — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)|Pobiera wskaźnik do nowego "ICorDebugValue" określonego typu o początkowej wartości null lub zero.|  
|[NewParameterizedArray — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)|Przydziela nowej tablicy o typie określonym elemencie i wymiary.|  
|[NewParameterizedObject — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)|Tworzy nowy obiekt sparametryzowany typ i wywołuje metodę konstruktora obiektu.|  
|[NewParameterizedObjectNoConstructor — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)|Tworzy nowy obiekt sparametryzowany typ określonej klasy bez próba wywołania metody konstruktora|  
|[NewStringWithLength — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newstringwithlength-method.md)|Tworzy nowy ciąg o określonej długości, przy użyciu określonej zawartości.|  
|[RudeAbort — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-rudeabort-method.md)|Przerywa obliczenia tego `ICorDebugEval2` wykonuje obecnie.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

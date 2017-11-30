---
title: ICorDebugILFrame Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame
helpviewer_keywords: ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d8d370fa971f698eb694127c72ff96499b85143d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugilframe-interface1"></a>ICorDebugILFrame Interface1
Reprezentuje ramka stosu kodu języka pośredniego (MSIL) firmy Microsoft. Ten interfejs jest podklasą klasy interfejsu ICorDebugFrame.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CanSetIP — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|Pobiera wartość wskazującą, czy jest to bezpieczne ustawienia wskaźnika instrukcji w określonej lokalizacji przesunięcia.|  
|[EnumerateArguments — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|Pobiera moduł wyliczający dla argumentów do tej ramki.|  
|[EnumerateLocalVariables — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|Pobiera moduł wyliczający dla zmiennych lokalnych w tej ramce.|  
|[GetArgument — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|Pobiera wartość określonego argumentu w tej ramce stosu MSIL.|  
|[GetIP — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|Pobiera wartość wskaźnika instrukcji i wartości bitowe połączenie, opisujące, jak uzyskano wartość wskaźnika instrukcji.|  
|[GetLocalVariable — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|Pobiera wartość zmiennej lokalnej określony w tej ramki stosu MSIL.|  
|[GetStackDepth — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|Nie jest zaimplementowana.|  
|[GetStackValue — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|Nie jest zaimplementowana.|  
|[SetIP — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|Ustawia wskaźnik instrukcji do określonej lokalizacji przesunięcia w kodzie MSIL.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugILFrame` Interfejs jest interfejsem ICorDebugFrame specjalne. Jest ona używana zarówno dla ramki kod MSIL i just-in-time (JIT) skompilowany ramki. Ramki kompilacji JIT implementować jednocześnie `ICorDebugILFrame` i interfejsem ICorDebugNativeFrame.  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: IAssemblyName — Interfejs
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aee9b986c1e26c1b2e34dac7151a00172451bbad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796555"
---
# <a name="iassemblyname-interface"></a>IAssemblyName — Interfejs
Zapewnia metody opisujące unikatową tożsamość zestawu i pracę z nim.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Clone, metoda](iassemblyname-clone-method.md)|Tworzy skróconą kopię tego `IAssemblyName` obiektu.|  
|[Finalize, metoda](iassemblyname-finalize-method.md)|Zezwala temu `IAssemblyName` obiektowi na zwalnianie zasobów i wykonywanie innych operacji czyszczenia przed wywołaniem destruktora.|  
|[GetDisplayName, metoda](iassemblyname-getdisplayname-method.md)|Pobiera nazwę zestawu, do którego odwołuje się ten `IAssemblyName` obiekt.|  
|[GetName, metoda](iassemblyname-getname-method.md)|Pobiera prostą, niezaszyfrowaną nazwę zestawu, do którego odwołuje `IAssemblyName` się ten obiekt.|  
|[GetProperty, metoda](iassemblyname-getproperty-method.md)|Pobiera wskaźnik do właściwości, do której odwołuje się `PropertyId`określony.|  
|[GetVersion, metoda](iassemblyname-getversion-method.md)|Pobiera informacje o wersji zestawu, do którego odwołuje `IAssemblyName` się ten obiekt.|  
|[IsEqual, metoda](iassemblyname-isequal-method.md)|Określa, czy określony `IAssemblyName` obiekt jest równy temu `IAssemblyName`, na podstawie określonych flag porównania.|  
|[SetProperty, metoda](iassemblyname-setproperty-method.md)|Ustawia wartość właściwości, do której odwołuje się określony `PropertyId`.|  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Fusion. h  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](fusion-interfaces.md)
- [IAssemblyEnum, interfejs](iassemblyenum-interface.md)

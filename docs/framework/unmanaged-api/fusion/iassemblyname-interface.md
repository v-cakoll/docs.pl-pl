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
ms.openlocfilehash: de49d66667033dfc6918b139f90cd5523661597f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134315"
---
# <a name="iassemblyname-interface"></a>IAssemblyName — Interfejs
Zapewnia metody opisujące unikatową tożsamość zestawu i pracę z nim.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Clone, metoda](iassemblyname-clone-method.md)|Tworzy skróconą kopię tego obiektu `IAssemblyName`.|  
|[Finalize, metoda](iassemblyname-finalize-method.md)|Umożliwia temu obiektowi `IAssemblyName` zwalnianie zasobów i wykonywanie innych operacji czyszczenia przed wywołaniem destruktora.|  
|[GetDisplayName, metoda](iassemblyname-getdisplayname-method.md)|Pobiera nazwę zestawu, do którego odwołuje się ten obiekt `IAssemblyName`.|  
|[GetName, metoda](iassemblyname-getname-method.md)|Pobiera prostą, niezaszyfrowaną nazwę zestawu, do którego odwołuje się ten obiekt `IAssemblyName`.|  
|[GetProperty, metoda](iassemblyname-getproperty-method.md)|Pobiera wskaźnik do właściwości, do której odwołuje się określony `PropertyId`.|  
|[GetVersion, metoda](iassemblyname-getversion-method.md)|Pobiera informacje o wersji zestawu, do którego odwołuje się ten obiekt `IAssemblyName`.|  
|[IsEqual, metoda](iassemblyname-isequal-method.md)|Określa, czy określony obiekt `IAssemblyName` jest równy temu `IAssemblyName`, na podstawie określonych flag porównania.|  
|[SetProperty, metoda](iassemblyname-setproperty-method.md)|Ustawia wartość właściwości, do której odwołuje się określony `PropertyId`.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](fusion-interfaces.md)
- [IAssemblyEnum, interfejs](iassemblyenum-interface.md)

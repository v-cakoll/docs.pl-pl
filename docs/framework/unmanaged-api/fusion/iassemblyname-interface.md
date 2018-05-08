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
ms.openlocfilehash: aa12252c4f2a8e710a4a880af103aa324f8118ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iassemblyname-interface"></a>IAssemblyName — Interfejs
Udostępnia metody opisujące i pracy z unikatowych tożsamości zestawu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Clone, metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|Tworzy kopię pobieżną to `IAssemblyName` obiektu.|  
|[Finalize, metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|Umożliwia to `IAssemblyName` obiekt, aby zwolnić zasoby i wykonywać inne zadania oczyszczania, przed jego destruktor jest wywoływany.|  
|[GetDisplayName, metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|Pobiera nazwę zrozumiałą zestawu odwołuje się ten `IAssemblyName` obiektu.|  
|[GetName, metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|Pobiera nazwę proste, niezaszyfrowanym zestawu odwołuje się ten `IAssemblyName` obiektu.|  
|[GetProperty, metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|Pobiera wskaźnik odwołuje się określony we właściwości `PropertyId`.|  
|[GetVersion, metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|Pobiera informacje o wersji dla zestawu odwołuje się ten `IAssemblyName` obiektu.|  
|[IsEqual, metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|Określa, czy określonej `IAssemblyName` obiekt jest taki sam `IAssemblyName`zgodnie flagi porównania określony.|  
|[SetProperty, metoda](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|Ustawia wartości właściwości odwołuje się określony `PropertyId`.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IAssemblyEnum, interfejs](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)

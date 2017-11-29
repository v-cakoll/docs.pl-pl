---
title: "IEnumReferenceIdentity — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumReferenceIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumReferenceIdentity
helpviewer_keywords: IEnumReferenceIdentity interface [.NET Framework fusion]
ms.assetid: a17b3155-7216-4e16-8c9f-abce21f549e7
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 49e1425e8e7e3d09dc36915916b887d2887dccff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ienumreferenceidentity-interface"></a>IEnumReferenceIdentity — Interfejs
Służy jako moduł wyliczający kolekcji `IReferenceIdentity` obiektów.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IEnumReferenceIdentity::Clone`|Pobiera wskaźnika interfejsu na nowy `IEnumReferenceIdentity` zawierający członkowie to `IEnumReferenceIdentity`.|  
|`IEnumReferenceIdentity::Next`|Pobiera określoną liczbę `IReferenceIdentity` obiektów, zaczynając od bieżącego położenia.|  
|`IEnumReferenceIdentity::Reset`|Przesuwa wskaźnik instrukcji na początku `IEnumReferenceIdentity`.|  
|`IEnumReferenceIdentity::Skip`|Przenosi do przodu wskaźnik instrukcji przez określoną liczbę elementów, licząc w bieżącym położeniu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [IReferenceIdentity — interfejs](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)

---
title: "_EFN_GetManagedObjectName — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _EFN_GetManagedObjectName
api_location: mscordbi.dll
api_type: COM
f1_keywords: _EFN_GetManagedObjectName
helpviewer_keywords: _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 80e36f6c60c4c305cad9176cd7f185d8b6d2fdf2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="efngetmanagedobjectname-function"></a>_EFN_GetManagedObjectName — Funkcja
Pobiera nazwę typu przy użyciu wskaźnika podanego obiektu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Client`  
 [in] Wskaźnik do klienta debugowania.  
  
 `objAddr`  
 [in] Wskaźnik do zarządzanego obiektu.  
  
 szName  
 [out] Nazwa typu.  
  
 `cbName`  
 [out] Liczba dostępnych w buforze ciąg znaków.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli istnieje żadnego kodu zarządzanego w wątku aktualnie w kontekście, funkcja zwraca HRESULT SOS_E_NOMANAGEDCODE z wartości instrumentu 0xa0 i błąd o kodzie 0x1000.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** SOS_Stacktrace.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Statyczne funkcje globalne debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

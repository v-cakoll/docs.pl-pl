---
title: ClrCreateManagedInstance — Funkcja
ms.date: 03/30/2017
api_name:
- ClrCreateManagedInstance
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a375ea586bacc2d3dafe53d493a7467730fae889
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432324"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance — Funkcja
Tworzy wystąpienie określonego typu zarządzanego.  
  
 Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Użyj aktywacji COM. można utworzyć wystąpienia typu zarządzanego lub hosting (zobacz [CLR hostingu interfejsów dodany do programu .NET Framework 4 i 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,   
    [in]  REFIID   riid,   
    [out] void     **ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pTypeName`  
 [in] Wskaźnik do nazwa żądanego typu wystąpienia.  
  
 `riid`  
 [in] `IID` Żądanego typu wystąpienia.  
  
 `ppObject`  
 [out] Wskaźnik na wskaźnik do wystąpienia typu zarządzanego, której zażądano przez obiekt wywołujący.  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego powinna już być załadowany do procesu. Na przykład mogą być ładowane przy użyciu wywołania [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) funkcji przed `ClrCreateManagedInstance` funkcja jest wywoływana. Jeśli środowisko uruchomieniowe nie został załadowany, `ClrCreateManagedInstance` po raz pierwszy próbuje załadować v1.0.3705 środowiska uruchomieniowego. W przypadku niepowodzenia próbuje załadować najnowszą wersję środowiska uruchomieniowego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)

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
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- ClrCreateManagedInstance
helpviewer_keywords:
- ClrCreateManagedInstance function [.NET Framework hosting]
ms.assetid: 58ba42c0-4857-43bf-a039-73a4dc6544c2
topic_type:
- apiref
ms.openlocfilehash: 7fbe0cf3e93d75749fa3f463f3f97dbd1bfe27a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176542"
---
# <a name="clrcreatemanagedinstance-function"></a>ClrCreateManagedInstance — Funkcja
Tworzy wystąpienie określonego typu zarządzanego.  
  
 Ta funkcja została przestarzała w .NET Framework 4. Użyj aktywacji COM, aby utworzyć wystąpienie typu zarządzanego lub użyć hostingu (zobacz [Clr Hosting Interfaces Added in the .NET Framework 4 and 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDAPI ClrCreateManagedInstance (  
    [in]  LPCWSTR  pTypeName,
    [in]  REFIID   riid,
    [out] void     **ppObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pTypeName`  
 [w] Wskaźnik do nazwy żądanego typu wystąpienia.  
  
 `riid`  
 [w] Typ `IID` wystąpienia, o które się ubiega.  
  
 `ppObject`  
 [na zewnątrz] Wskaźnik do wskaźnika do wystąpienia typu zarządzanego, który został poproszony przez wywołującego.  
  
## <a name="remarks"></a>Uwagi  
 Środowisko wykonawcze języka wspólnego należy już załadować do procesu. Na przykład można go załadować za pomocą wywołania [funkcji CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) przed wywołaniem `ClrCreateManagedInstance` funkcji. Jeśli środowisko wykonawcze nie `ClrCreateManagedInstance` jest ładowane, najpierw próbuje załadować v1.0.3705 środowiska wykonawczego. Jeśli to się nie powiedzie, próbuje załadować najnowszą wersję środowiska wykonawczego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Mscoree.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)

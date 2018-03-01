---
title: "GetCORSystemDirectory — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 02b695ac7f75dd38da8cd06e1444af4ae425ebd2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory — Funkcja
Zwraca katalog instalacyjny programu środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany do procesu. Katalogu instalacyjnego jest w pełni kwalifikowana, na przykład "c:\windows\microsoft.net\framework\v1.0.3705".  
  
 Ta funkcja jest przestarzała. Zostało zastąpione przez [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) metody w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a>Parametry  
 `pbuffer`  
 [out] Bufor, w którym środowiska uruchomieniowego zwraca ciąg zawierający w pełni kwalifikowaną nazwę katalogu instalacyjnego środowiska uruchomieniowego, który jest ładowany do procesu. Jeśli środowisko uruchomieniowe nie został jeszcze załadowany do procesu, funkcja zwraca informacje odpowiedniego katalogu dla najnowszej wersji środowiska uruchomieniowego zainstalowany na komputerze.  
  
 `cchBuffer`  
 [in] Rozmiar w bajtach z `pbuffer`.  
  
 `dwLength`  
 [out] Liczba znaków zwracane w `pbuffer`.  
  
## <a name="remarks"></a>Uwagi  
  
> [!CAUTION]
>  Nie należy używać tej funkcji w procesów uruchomionych w wersji 4 środowiska CLR. Jeśli starszej wersji środowiska CLR jest zainstalowany na komputerze, ta funkcja zwraca katalog instalacyjny dla tej wersji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** biblioteki MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

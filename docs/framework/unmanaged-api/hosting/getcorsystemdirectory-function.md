---
title: GetCORSystemDirectory — Funkcja
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8608a5438b31cad64bb27d2866109f479dad441
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739501"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory — Funkcja
Zwraca katalog instalacyjny środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany do procesu. Katalog instalacyjny jest w pełni kwalifikowany, na przykład "c:\windows\microsoft.net\framework\v1.0.3705".  
  
 Ta funkcja jest przestarzała. Zostało zastąpione przez [iclrruntimeinfo::getruntimedirectory —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) podany w metodzie [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
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
 [out] Bufor, w którym środowisko wykonawcze zwraca ciąg zawierający w pełni kwalifikowaną nazwę katalogu instalacyjnego dla środowiska uruchomieniowego, który jest ładowany do procesu. Jeśli środowisko wykonawcze nie został jeszcze załadowany do procesu, funkcja zwraca informacje odpowiedniego katalogu dla najnowszej wersji środowiska uruchomieniowego zainstalowanego na komputerze.  
  
 `cchBuffer`  
 [in] Rozmiar w bajtach z `pbuffer`.  
  
 `dwLength`  
 [out] Liczba znaków zwracane w `pbuffer`.  
  
## <a name="remarks"></a>Uwagi  
  
> [!CAUTION]
>  Nie należy używać tej funkcji w procesach, które działają w wersji 4 środowiska CLR. Jeśli starszą wersję środowiska CLR jest zainstalowany na komputerze, ta funkcja zwraca katalog instalacyjny dla danej wersji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)

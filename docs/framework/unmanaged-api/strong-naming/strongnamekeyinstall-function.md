---
title: "StrongNameKeyInstall — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameKeyInstall
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameKeyInstall
helpviewer_keywords: StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 60044e12a884a28cb7485118a95d2bf7650723fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamekeyinstall-function"></a>StrongNameKeyInstall — Funkcja
Importuje pary kluczy publicznych/prywatnych do kontenera.  
  
 Ta funkcja jest przestarzała. Użyj [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
BOOLEAN StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszKeyContainer`  
 [in] Nazwa kontenera kluczy. `wszKeyContainer`musi być niepustym ciągiem.  
  
 `pbKeyBlob`  
 [in] Binarny pary kluczy.  
  
 `cbKeyBlob`  
 [in] Rozmiar w bajtach z `pbKeyBlob`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Po pomyślnym ukończeniu; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Użyj [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) funkcji można usunąć kontenera klucza.  
  
 Jeśli `StrongNameKeyInstall` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** WindSee [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [StrongNameKeyInstall — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [StrongNameKeyDelete — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [ICLRStrongName — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

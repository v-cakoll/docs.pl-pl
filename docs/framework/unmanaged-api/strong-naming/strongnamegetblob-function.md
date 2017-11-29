---
title: "StrongNameGetBlob — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetBlob
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameGetBlob
helpviewer_keywords: StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0a88131e4a764c963d24a698935ebb12e0daa96c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetblob-function"></a>StrongNameGetBlob — Funkcja
Wstawia określony bufor binarna reprezentacja pliku wykonywalnego pod określonym adresem.  
  
 Ta funkcja jest przestarzała. Użyj [ICLRStrongName::StrongNameGetBLob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [in] Nieprawidłowa ścieżka do pliku wykonywalnego do załadowania.  
  
 `pbBlob`  
 [in] Bufor, do którego można załadować pliku wykonywalnego.  
  
 `pcbBlob`  
 [w, out] Żądane maksymalny rozmiar w bajtach `pbBlob`. Po powrocie, rzeczywisty rozmiar w bajtach z `pbBlob`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Po pomyślnym ukończeniu; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `StrongNameGetBlob` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [StrongNameGetBlob — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [StrongNameGetBlobFromImage — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [ICLRStrongName — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

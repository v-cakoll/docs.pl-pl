---
title: "StrongNameGetBlobFromImage — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetBlobFromImage
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameGetBlobFromImage
helpviewer_keywords: StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3dd5fa1838517baa97079f5d7f75a789384255a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamegetblobfromimage-function"></a>StrongNameGetBlobFromImage — Funkcja
Pobiera zestawu obraz to binarna reprezentacja pod adresem określonym pamięci.  
  
 Ta funkcja jest przestarzała. Użyj [ICLRStrongName::StrongNameGetBlobFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbBase`  
 [in] Adres pamięci manifest zestawu mapowane.  
  
 `dwLength`  
 [in] Rozmiar w bajtach obrazu w `pbBase`.  
  
 `pbBlob`  
 [in] Bufor zawiera binarna reprezentacja obrazu.  
  
 `pcbBlob`  
 [w, out] Żądane maksymalny rozmiar w bajtach `pbBlob`. Po powrocie, rzeczywisty rozmiar w bajtach z `pbBlob`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Po pomyślnym ukończeniu; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `StrongNameGetBlobFromImage` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [StrongNameGetBlobFromImage, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [StrongNameGetBlob, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

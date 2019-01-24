---
title: StrongNameGetBlob — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a465b38951593fea7f36ef4ffba32e282f079f77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533601"
---
# <a name="strongnamegetblob-function"></a>StrongNameGetBlob — Funkcja
Wstawia określony bufor binarna reprezentacja pliku wykonywalnego pod podanym adresem.  
  
 Ta funkcja jest przestarzała. Użyj [iclrstrongname::strongnamegetblob —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) metody zamiast tego.  
  
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
 [out w] Maksymalny rozmiar w bajtach, żądane `pbBlob`. Po powrocie, rzeczywisty rozmiar w bajtach, z `pbBlob`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `StrongNameGetBlob` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [StrongNameGetBlob, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [StrongNameGetBlobFromImage, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

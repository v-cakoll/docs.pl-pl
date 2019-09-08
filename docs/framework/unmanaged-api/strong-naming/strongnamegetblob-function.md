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
ms.openlocfilehash: 2d5b3d1d39b5d4c5b7d4db073b3ffaf1c6b88373
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799104"
---
# <a name="strongnamegetblob-function"></a>StrongNameGetBlob — Funkcja
Wypełnia określony bufor reprezentacją binarną pliku wykonywalnego pod określonym adresem.  
  
 Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: StrongNameGetBlob —](../hosting/iclrstrongname-strongnamegetblob-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 podczas Prawidłowa ścieżka do pliku wykonywalnego, który ma zostać załadowany.  
  
 `pbBlob`  
 podczas Bufor, do którego ma zostać załadowany plik wykonywalny.  
  
 `pcbBlob`  
 [in. out] Żądany maksymalny rozmiar, w bajtach, z `pbBlob`. Po powrocie, rzeczywisty rozmiar, w bajtach, `pbBlob`z.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Po pomyślnym zakończeniu; w przeciwnym razie. `false`  
  
## <a name="remarks"></a>Uwagi  
 Jeśli funkcja nie zakończy się pomyślnie, wywołaj funkcję StrongNameErrorInfo — w celu pobrania ostatniego wygenerowanego błędu. [](strongnameerrorinfo-function.md) `StrongNameGetBlob`  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** StrongName.h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameGetBlob, metoda](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [StrongNameGetBlobFromImage, metoda](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)

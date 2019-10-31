---
title: StrongNameGetBlobFromImage — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
ms.openlocfilehash: 41226cd909900bd2da7bdcf9b9a49567d3042b01
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094880"
---
# <a name="strongnamegetblobfromimage-function"></a>StrongNameGetBlobFromImage — Funkcja
Pobiera binarną reprezentację obrazu zestawu pod określonym adresem pamięci.  
  
 Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: StrongNameGetBlobFromImage —](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbBase`  
 podczas Adres pamięci mapowanego manifestu zestawu.  
  
 `dwLength`  
 podczas Rozmiar, w bajtach, obrazu w `pbBase`.  
  
 `pbBlob`  
 podczas Bufor zawierający reprezentację binarną obrazu.  
  
 `pcbBlob`  
 [in. out] Żądany maksymalny rozmiar w bajtach `pbBlob`. Po powrocie, rzeczywisty rozmiar w bajtach `pbBlob`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` po pomyślnym zakończeniu; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli funkcja `StrongNameGetBlobFromImage` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameGetBlobFromImage, metoda](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [StrongNameGetBlob, metoda](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)

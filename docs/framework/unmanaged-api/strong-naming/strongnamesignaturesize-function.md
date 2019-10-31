---
title: StrongNameSignatureSize — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
ms.openlocfilehash: a8856790b655f071df704879a247169f456ae2f5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130874"
---
# <a name="strongnamesignaturesize-function"></a>StrongNameSignatureSize — Funkcja
Zwraca rozmiar sygnatury silnej nazwy. `StrongNameSignatureSize` jest zwykle używany przez kompilatory do określenia ilości miejsca do zarezerwowania w pliku podczas tworzenia zestawu z opóźnieniem.  
  
 Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: StrongNameSignatureSize —](../hosting/iclrstrongname-strongnamesignaturesize-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a>Parametry  
 `pbPublicKeyBlob`  
 podczas Struktura typu [PublicKeyBlob —](publickeyblob-structure.md) , która zawiera publiczną część pary kluczy używanej do generowania podpisu silnej nazwy.  
  
 `cbPublicKeyBlob`  
 podczas Rozmiar w bajtach `pbPublicKeyBlob`.  
  
 `pcbSize`  
 podczas Liczba bajtów wymagana do zapisania sygnatury silnej nazwy.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` po pomyślnym zakończeniu; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli funkcja `StrongNameSignatureSize` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameSignatureSize, metoda](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)

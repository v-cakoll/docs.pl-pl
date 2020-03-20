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
ms.openlocfilehash: a19d875b8fb81f2af3821e69452f0f0ed591cd22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176893"
---
# <a name="strongnamesignaturesize-function"></a>StrongNameSignatureSize — Funkcja
Zwraca rozmiar podpisu silnej nazwy. `StrongNameSignatureSize`jest zazwyczaj używany przez kompilatory, aby określić, ile miejsca do zarezerwowania w pliku podczas tworzenia zestawu podpisane z opóźnieniem.  
  
 Ta funkcja została przestarzała. Zamiast tego należy użyć metody [ICLRStrongName::StrongNameSignatureSize.](../hosting/iclrstrongname-strongnamesignaturesize-method.md)  
  
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
 [w] Struktura typu [PublicKeyBlob,](publickeyblob-structure.md) który zawiera część publiczną pary kluczy używane do generowania podpisu silnej nazwy.  
  
 `cbPublicKeyBlob`  
 [w] Rozmiar w bajtach `pbPublicKeyBlob`.  
  
 `pcbSize`  
 [w] Liczba bajtów wymaganych do przechowywania podpisu silnej nazwy.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`po pomyślnym zakończeniu; w `false`przeciwnym razie , .  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `StrongNameSignatureSize` funkcja nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo,](strongnameerrorinfo-function.md) aby pobrać ostatni wygenerowany błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h (Nazwa siła)-h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [StrongNameSignatureSize, metoda](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)

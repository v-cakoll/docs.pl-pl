---
title: StrongNameTokenFromPublicKey — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
ms.openlocfilehash: b95c96efeb666f25d04118aa8cb9b0da3a2e7924
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104163"
---
# <a name="strongnametokenfrompublickey-function"></a>StrongNameTokenFromPublicKey — Funkcja
Pobiera token reprezentujący klucz publiczny. Token silnej nazwy to skrócona postać klucza publicznego.  
  
 Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: StrongNameTokenFromPublicKey —](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbPublicKeyBlob`  
 podczas Struktura typu [PublicKeyBlob —](publickeyblob-structure.md) , która zawiera publiczną część pary kluczy używanej do generowania podpisu silnej nazwy.  
  
 `cbPublicKeyBlob`  
 podczas Rozmiar w bajtach `pbPublicKeyBlob`.  
  
 `ppbStrongNameToken`  
 określoną Token silnej nazwy odpowiadający kluczowi przesłanemu `pbPublicKeyBlob`. Środowisko uruchomieniowe języka wspólnego przydziela pamięć, w której ma zostać zwrócony token. Obiekt wywołujący musi zwolnić tę pamięć przy użyciu funkcji [StrongNameFreeBuffer —](strongnamefreebuffer-function.md) .  
  
 `pcbStrongNameToken`  
 określoną Rozmiar (w bajtach) zwracanego tokenu silnej nazwy.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` po pomyślnym zakończeniu; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Token silnej nazwy to Skrócona forma klucza publicznego służąca do oszczędzania miejsca podczas przechowywania informacji o kluczu w metadanych. W odniesieniu do zestawu zależnego w odwołaniach do zestawów są używane tokeny silnej nazwy.  
  
 Jeśli funkcja `StrongNameTokenFromPublicKey` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece mscoree. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameTokenFromPublicKey, metoda](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [StrongNameGetPublicKey, metoda](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob, struktura](publickeyblob-structure.md)

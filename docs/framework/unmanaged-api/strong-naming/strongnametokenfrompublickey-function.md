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
ms.openlocfilehash: 20be3114908ef78966eead05ae8ba6333a491404
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175060"
---
# <a name="strongnametokenfrompublickey-function"></a>StrongNameTokenFromPublicKey — Funkcja
Pobiera token reprezentujący klucz publiczny. Token silnej nazwy jest skróconą formą klucza publicznego.  
  
 Ta funkcja została przestarzała. Zamiast tego należy użyć metody [ICLRStrongName::StrongNameTokenFromPublicKey.](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
  
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
 [w] Struktura typu [PublicKeyBlob,](publickeyblob-structure.md) który zawiera część publiczną pary kluczy używane do generowania podpisu silnej nazwy.  
  
 `cbPublicKeyBlob`  
 [w] Rozmiar w bajtach `pbPublicKeyBlob`.  
  
 `ppbStrongNameToken`  
 [na zewnątrz] Token silnej nazwy odpowiadający `pbPublicKeyBlob`kluczowi przekazanym w . Środowisko wykonawcze języka wspólnego przydziela pamięć, w której do zwrócenia tokenu. Wywołujący należy zwolnić tę pamięć przy użyciu [Funkcji StrongNameFreeBuffer.](strongnamefreebuffer-function.md)  
  
 `pcbStrongNameToken`  
 [na zewnątrz] Rozmiar w bajtach zwróconego tokenu silnej nazwy.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`po pomyślnym zakończeniu; w `false`przeciwnym razie , .  
  
## <a name="remarks"></a>Uwagi  
 Token silnej nazwy to skrócona forma klucza publicznego używana do zapisywania miejsca podczas przechowywania kluczowych informacji w metadanych. W szczególności tokeny silnej nazwy są używane w odwołaniach do zestawu w celu odwoływania się do zestawu zależnego.  
  
 Jeśli `StrongNameTokenFromPublicKey` funkcja nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo,](strongnameerrorinfo-function.md) aby pobrać ostatni wygenerowany błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h (Nazwa siła)-h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku mscoree.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [StrongNameTokenFromPublicKey, metoda](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [StrongNameGetPublicKey, metoda](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob — Struktura](publickeyblob-structure.md)

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68be16c559431de871dc9ddb1963897b0927d49a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783162"
---
# <a name="strongnametokenfrompublickey-function"></a>StrongNameTokenFromPublicKey — Funkcja
Pobiera token reprezentujący klucz publiczny. Token silna nazwa jest skrócona forma klucza publicznego.  
  
 Ta funkcja jest przestarzała. Użyj [iclrstrongname::strongnametokenfrompublickey —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md) metody zamiast tego.  
  
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
 [in] Struktury typu [publickeyblob —](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) zawierający publiczną część pary kluczy używanego do generowania podpisu silnej nazwy.  
  
 `cbPublicKeyBlob`  
 [in] Rozmiar w bajtach z `pbPublicKeyBlob`.  
  
 `ppbStrongNameToken`  
 [out] Przekazany token silną nazwę odpowiadającą kluczowi `pbPublicKeyBlob`. Środowisko uruchomieniowe języka wspólnego przydziela pamięć, w których ma zostać zwrócony token. Obiekt wywołujący musi zwolnić ta pamięć przy użyciu [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcji.  
  
 `pcbStrongNameToken`  
 [out] Rozmiar w bajtach, token zwrócony silnej nazwy.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Token silna nazwa jest skrócona forma kluczem publicznym, która pozwala zaoszczędzić miejsce, gdy kluczowe informacje są przechowywane w metadanych. W szczególności tokenów silnych nazw są używane w odwołania do zestawów do odwoływania się do zestawu zależnego.  
  
 Jeśli `StrongNameTokenFromPublicKey` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h  
  
 **Biblioteka:** Dołączony jako zasób w mscoree.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameTokenFromPublicKey, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [StrongNameGetPublicKey, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob, struktura](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)

---
title: StrongNameGetPublicKey — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
ms.openlocfilehash: 966a2a628f30f1999688da7b6ba435c1d6cb830c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094665"
---
# <a name="strongnamegetpublickey-function"></a>StrongNameGetPublicKey — Funkcja
Pobiera klucz publiczny z pary kluczy prywatnych/publicznych. Para kluczy może być podana jako nazwa kontenera klucza w ramach dostawcy usług kryptograficznych (CSP) lub jako pierwotna kolekcja bajtów.  
  
 Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: StrongNameGetPublicKey —](../hosting/iclrstrongname-strongnamegetpublickey-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szKeyContainer`  
 podczas Nazwa kontenera kluczy, który zawiera parę kluczy publiczny/prywatny. Jeśli `pbKeyBlob` ma wartość null, `szKeyContainer` musi określić prawidłowy kontener w ramach dostawcy CSP. W takim przypadku `StrongNameGetPublicKey` wyodrębnia klucz publiczny z pary kluczy przechowywanej w kontenerze.  
  
 Jeśli `pbKeyBlob` nie ma wartości null, przyjmuje się, że para kluczy jest zawarta w kluczowym dużym obiekcie binarnym (BLOB).  
  
 Klucze muszą być 1024-bitowe Rivest-Shamir-Adleman (RSA) kluczy podpisywania. W tej chwili nie są obsługiwane żadne inne typy kluczy.  
  
 `pbKeyBlob`  
 podczas Wskaźnik do pary kluczy publicznych/prywatnych. Ta para jest w formacie utworzonym przez funkcję `CryptExportKey` Win32. Jeśli `pbKeyBlob` ma wartość null, założono, że kontener kluczy określony przez `szKeyContainer` zostanie zawierający parę kluczy.  
  
 `cbKeyBlob`  
 podczas Rozmiar w bajtach `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 określoną Zwrócony obiekt BLOB klucza publicznego. Parametr `ppbPublicKeyBlob` jest przypisywany przez środowisko uruchomieniowe języka wspólnego i zwracany do obiektu wywołującego. Obiekt wywołujący musi zwolnić pamięć przy użyciu funkcji [StrongNameFreeBuffer —](strongnamefreebuffer-function.md) .  
  
 `pcbPublicKeyBlob`  
 określoną Rozmiar zwróconego obiektu BLOB klucza publicznego.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` po pomyślnym zakończeniu; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Klucz publiczny jest zawarty w strukturze [PublicKeyBlob —](publickeyblob-structure.md) .  
  
 Jeśli funkcja `StrongNameGetPublicKey` nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo —](strongnameerrorinfo-function.md) w celu pobrania ostatniego wygenerowanego błędu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameGetPublicKey, metoda](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [StrongNameTokenFromPublicKey, metoda](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
- [PublicKeyBlob, struktura](publickeyblob-structure.md)

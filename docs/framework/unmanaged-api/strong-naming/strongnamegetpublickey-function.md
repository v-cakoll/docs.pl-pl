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
ms.openlocfilehash: fcdd4a3f07b4499fd2388b5d165c409da9150466
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176932"
---
# <a name="strongnamegetpublickey-function"></a>StrongNameGetPublicKey — Funkcja
Pobiera klucz publiczny z pary klucza prywatnego/publicznego. Para kluczy może być podana jako nazwa kontenera klucza w dostawcy usług kryptograficznych (CSP) lub jako nieprzetworzona kolekcja bajtów.  
  
 Ta funkcja została przestarzała. Zamiast tego należy użyć metody [ICLRStrongName::StrongNameGetPublicKey.](../hosting/iclrstrongname-strongnamegetpublickey-method.md)  
  
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
 [w] Nazwa kontenera klucza zawierającego parę kluczy publicznych/prywatnych. Jeśli `pbKeyBlob` wartość `szKeyContainer` null jest zerowa, należy określić prawidłowy kontener w ramach usługi CSP. W takim `StrongNameGetPublicKey` przypadku wyodrębnia klucz publiczny z pary kluczy przechowywanych w kontenerze.  
  
 Jeśli `pbKeyBlob` nie ma wartości null, przyjmuje się, że para kluczy znajduje się w głównym obiekcie binarnym (BLOB).  
  
 Klucze muszą być 1024-bitowe klucze podpisywania Rivest-Shamir-Adleman (RSA). Żadne inne typy kluczy są obecnie obsługiwane.  
  
 `pbKeyBlob`  
 [w] Wskaźnik do pary kluczy publicznych/prywatnych. Ta para jest w formacie utworzonym `CryptExportKey` przez funkcję Win32. Jeśli `pbKeyBlob` ma wartość null, `szKeyContainer` przyjmuje się, że kontener kluczy określony przez zawiera parę kluczy.  
  
 `cbKeyBlob`  
 [w] Rozmiar w bajtach `pbKeyBlob`.  
  
 `ppbPublicKeyBlob`  
 [na zewnątrz] Zwrócony obiekt BLOB klucza publicznego. Parametr `ppbPublicKeyBlob` jest przydzielany przez środowisko uruchomieniowe języka wspólnego i zwracany do wywołującego. Wywołujący musi zwolnić pamięć przy użyciu [Funkcji StrongNameFreeBuffer.](strongnamefreebuffer-function.md)  
  
 `pcbPublicKeyBlob`  
 [na zewnątrz] Rozmiar zwracanego obiektu BLOB klucza publicznego.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`po pomyślnym zakończeniu; w `false`przeciwnym razie , .  
  
## <a name="remarks"></a>Uwagi  
 Klucz publiczny znajduje się w [strukturze PublicKeyBlob.](publickeyblob-structure.md)  
  
 Jeśli `StrongNameGetPublicKey` funkcja nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo,](strongnameerrorinfo-function.md) aby pobrać ostatni wygenerowany błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h (Nazwa siła)-h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [StrongNameGetPublicKey, metoda](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [StrongNameTokenFromPublicKey, metoda](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
- [PublicKeyBlob — Struktura](publickeyblob-structure.md)

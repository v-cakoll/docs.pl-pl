---
title: StrongNameSignatureGeneration — Funkcja
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
ms.openlocfilehash: d7f481e5c61ec65d2e7414bd47227866f3435028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176906"
---
# <a name="strongnamesignaturegeneration-function"></a>StrongNameSignatureGeneration — Funkcja
Generuje podpis silnej nazwy dla określonego zestawu.  
  
 Ta funkcja została przestarzała. Zamiast tego należy użyć metody [ICLRStrongName::StrongNameSignatureGeneration.](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
BOOLEAN StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [w] Ścieżka do pliku, który zawiera manifest zestawu, dla którego zostanie wygenerowany podpis silnej nazwy.  
  
 `wszKeyContainer`  
 [w] Nazwa kontenera klucza zawierającego parę kluczy publicznych/prywatnych.  
  
 Jeśli `pbKeyBlob` wartość `wszKeyContainer` null jest zerowa, należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP). W takim przypadku para kluczy przechowywana w kontenerze jest używana do podpisywania pliku.  
  
 Jeśli `pbKeyBlob` nie ma wartości null, przyjmuje się, że para kluczy znajduje się w głównym obiekcie binarnym (BLOB).  
  
 Klucze muszą być 1024-bitowe klucze podpisywania Rivest-Shamir-Adleman (RSA). Żadne inne typy kluczy są obecnie obsługiwane.  
  
 `pbKeyBlob`  
 [w] Wskaźnik do pary kluczy publicznych/prywatnych. Ta para jest w formacie utworzonym `CryptExportKey` przez funkcję Win32. Jeśli `pbKeyBlob` ma wartość null, `wszKeyContainer` przyjmuje się, że kontener kluczy określony przez zawiera parę kluczy.  
  
 `cbKeyBlob`  
 [w] Rozmiar w bajtach `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 [na zewnątrz] Wskaźnik do lokalizacji, do której środowisko uruchomieniowe języka wspólnego zwraca podpis. Jeśli `ppbSignatureBlob` wartość null ma wartość null, środowisko `wszFilePath`wykonawcze przechowuje podpis w pliku określonym przez program .  
  
 Jeśli `ppbSignatureBlob` nie jest null, środowisko uruchomieniowe języka wspólnego przydziela miejsce, w którym do zwrócenia podpisu. Wywołujący musi zwolnić to miejsce za pomocą [Funkcji StrongNameFreeBuffer.](strongnamefreebuffer-function.md)  
  
 `pcbSignatureBlob`  
 [na zewnątrz] Rozmiar w bajtach zwróconego podpisu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`po pomyślnym zakończeniu; w `false`przeciwnym razie , .  
  
## <a name="remarks"></a>Uwagi  
 Określ `wszFilePath` wartość null, aby obliczyć rozmiar podpisu bez tworzenia podpisu.  
  
 Podpis może być przechowywany bezpośrednio w pliku lub zwrócony do wywołującego.  
  
 Jeśli `StrongNameSignatureGeneration` funkcja nie zakończy się pomyślnie, wywołaj funkcję [StrongNameErrorInfo,](strongnameerrorinfo-function.md) aby pobrać ostatni wygenerowany błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h (Nazwa siła)-h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [StrongNameSignatureGeneration, metoda](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [StrongNameSignatureGenerationEx, metoda](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)

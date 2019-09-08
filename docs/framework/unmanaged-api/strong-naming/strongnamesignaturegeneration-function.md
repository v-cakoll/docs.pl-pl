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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48cdd550e5d8c7c75a603d74456e99a066d5c599
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798969"
---
# <a name="strongnamesignaturegeneration-function"></a>StrongNameSignatureGeneration — Funkcja
Generuje podpis silnej nazwy dla określonego zestawu.  
  
 Ta funkcja jest przestarzała. Zamiast tego użyj metody [ICLRStrongName:: StrongNameSignatureGeneration —](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) .  
  
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
 podczas Ścieżka do pliku zawierającego manifest zestawu, dla którego zostanie wygenerowany podpis silnej nazwy.  
  
 `wszKeyContainer`  
 podczas Nazwa kontenera kluczy, który zawiera parę kluczy publiczny/prywatny.  
  
 Jeśli `pbKeyBlob` ma wartość null `wszKeyContainer` , należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP). W takim przypadku para kluczy przechowywana w kontenerze jest używana do podpisania pliku.  
  
 Jeśli `pbKeyBlob` wartość nie jest równa null, przyjmuje się, że para kluczy jest zawarta w kluczowym dużym obiekcie binarnym (BLOB).  
  
 Klucze muszą być 1024-bitowe Rivest-Shamir-Adleman (RSA) kluczy podpisywania. W tej chwili nie są obsługiwane żadne inne typy kluczy.  
  
 `pbKeyBlob`  
 podczas Wskaźnik do pary kluczy publicznych/prywatnych. Ta para jest w formacie utworzonym przez funkcję Win32 `CryptExportKey` . Jeśli `pbKeyBlob` ma wartość null, zakłada się, że `wszKeyContainer` kontener kluczy określony przez ma zawierać parę kluczy.  
  
 `cbKeyBlob`  
 podczas Rozmiar, w bajtach, z `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 określoną Wskaźnik do lokalizacji, do której aparat plików wykonywalnych języka wspólnego zwraca sygnaturę. Jeśli `ppbSignatureBlob` ma wartość null, środowisko uruchomieniowe zapisuje podpis w pliku określonym przez `wszFilePath`.  
  
 Jeśli `ppbSignatureBlob` wartość nie jest równa null, środowisko uruchomieniowe języka wspólnego przydziela miejsce do zwrócenia sygnatury. Obiekt wywołujący musi zwolnić to miejsce przy użyciu funkcji [StrongNameFreeBuffer —](strongnamefreebuffer-function.md) .  
  
 `pcbSignatureBlob`  
 określoną Rozmiar zwróconej sygnatury w bajtach.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Po pomyślnym zakończeniu; w przeciwnym razie. `false`  
  
## <a name="remarks"></a>Uwagi  
 Określ wartość null `wszFilePath` dla, aby obliczyć rozmiar podpisu bez tworzenia podpisu.  
  
 Podpis może być przechowywany bezpośrednio w pliku lub zwracany do obiektu wywołującego.  
  
 Jeśli funkcja nie zakończy się pomyślnie, wywołaj funkcję StrongNameErrorInfo — w celu pobrania ostatniego wygenerowanego błędu. [](strongnameerrorinfo-function.md) `StrongNameSignatureGeneration`  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** StrongName.h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameSignatureGeneration, metoda](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [StrongNameSignatureGenerationEx, metoda](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)

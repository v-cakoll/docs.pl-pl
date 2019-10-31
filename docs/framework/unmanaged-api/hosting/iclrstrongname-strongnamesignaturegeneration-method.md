---
title: ICLRStrongName::StrongNameSignatureGeneration — Metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGeneration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type:
- apiref
ms.openlocfilehash: 8013d805716bbe6407eeed664966fe667282188a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135008"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a>ICLRStrongName::StrongNameSignatureGeneration — Metoda
Generuje podpis silnej nazwy dla określonego zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT StrongNameSignatureGeneration (   
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
  
 Jeśli `pbKeyBlob` ma wartość null, `wszKeyContainer` musi określić prawidłowego kontenera w ramach dostawcy usług kryptograficznych (CSP). W takim przypadku para kluczy przechowywana w kontenerze jest używana do podpisania pliku.  
  
 Jeśli `pbKeyBlob` nie ma wartości null, przyjmuje się, że para kluczy jest zawarta w kluczowym dużym obiekcie binarnym (BLOB).  
  
 Klucze muszą być 1024-bitowe Rivest-Shamir-Adleman (RSA) kluczy podpisywania. W tej chwili nie są obsługiwane żadne inne typy kluczy.  
  
 `pbKeyBlob`  
 podczas Wskaźnik do pary kluczy publicznych/prywatnych. Ta para jest w formacie utworzonym przez funkcję `CryptExportKey` Win32. Jeśli `pbKeyBlob` ma wartość null, założono, że kontener kluczy określony przez `wszKeyContainer` zostanie zawierający parę kluczy.  
  
 `cbKeyBlob`  
 podczas Rozmiar w bajtach `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 określoną Wskaźnik do lokalizacji, do której aparat plików wykonywalnych języka wspólnego zwraca sygnaturę. Jeśli `ppbSignatureBlob` ma wartość null, środowisko uruchomieniowe zapisuje podpis w pliku określonym przez `wszFilePath`.  
  
 Jeśli `ppbSignatureBlob` nie ma wartości null, środowisko uruchomieniowe języka wspólnego przydziela miejsce do zwrócenia sygnatury. Obiekt wywołujący musi zwolnić to miejsce przy użyciu metody [ICLRStrongName:: StrongNameFreeBuffer —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .  
  
 `pcbSignatureBlob`  
 określoną Rozmiar zwróconej sygnatury w bajtach.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`, jeśli metoda została ukończona pomyślnie; w przeciwnym razie wartość HRESULT wskazująca niepowodzenie (zobacz [typowe wartości HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) dla listy).  
  
## <a name="remarks"></a>Uwagi  
 Określ wartość null dla `wszFilePath`, aby obliczyć rozmiar podpisu bez tworzenia podpisu.  
  
 Podpis może być przechowywany bezpośrednio w pliku lub zwracany do obiektu wywołującego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameSignatureGenerationEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

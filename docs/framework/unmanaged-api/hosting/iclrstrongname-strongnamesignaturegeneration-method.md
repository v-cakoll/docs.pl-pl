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
ms.openlocfilehash: e58ac181c4e472c469076b880ff71e0c6afa30fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178051"
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
  
 Jeśli `ppbSignatureBlob` nie jest null, środowisko uruchomieniowe języka wspólnego przydziela miejsce, w którym do zwrócenia podpisu. Wywołujący musi zwolnić to miejsce przy użyciu [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metody.  
  
 `pcbSignatureBlob`  
 [na zewnątrz] Rozmiar w bajtach zwróconego podpisu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`jeśli metoda została pomyślnie ukończona; w przeciwnym razie wartość HRESULT wskazująca błąd (zobacz [typowe wartości HRESULT](/windows/win32/seccrypto/common-hresult-values) dla listy).  
  
## <a name="remarks"></a>Uwagi  
 Określ `wszFilePath` wartość null, aby obliczyć rozmiar podpisu bez tworzenia podpisu.  
  
 Podpis może być przechowywany bezpośrednio w pliku lub zwrócony do wywołującego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MSCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [StrongNameSignatureGenerationEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

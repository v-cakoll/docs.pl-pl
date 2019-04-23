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
ms.openlocfilehash: 0e7df65c28fad6fa79ec7a18d8511955330b2817
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227746"
---
# <a name="strongnamesignaturegeneration-function"></a>StrongNameSignatureGeneration — Funkcja
Generuje podpisu silnej nazwy dla określonego zestawu.  
  
 Ta funkcja jest przestarzała. Użyj [iclrstrongname::strongnamesignaturegeneration —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
 [in] Ścieżka do pliku, który zawiera manifest zestawu, dla którego zostanie wygenerowany podpisu silnej nazwy.  
  
 `wszKeyContainer`  
 [in] Nazwa kontenera kluczy, który zawiera pary kluczy publiczny/prywatny.  
  
 Jeśli `pbKeyBlob` ma wartość null, `wszKeyContainer` należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP). W tym przypadku parę kluczy, przechowywane w kontenerze służy do podpisywania pliku.  
  
 Jeśli `pbKeyBlob` nie ma wartości null, zakłada, że pary kluczy muszą być zawarte w kluczowych duży obiekt binarny (BLOB).  
  
 Klucze muszą być Rivest-Shamir-Adleman 1024-bitowy (RSA) kluczy podpisywania. Żadne inne typy kluczy są obsługiwane w tej chwili.  
  
 `pbKeyBlob`  
 [in] Wskaźnik do pary kluczy publiczny/prywatny. Ta para jest w formacie utworzone przez Win32 `CryptExportKey` funkcji. Jeśli `pbKeyBlob` jest null, kontenerze klucza określonym przez `wszKeyContainer` założono, że zawiera pary kluczy.  
  
 `cbKeyBlob`  
 [in] Rozmiar w bajtach z `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 [out] Wskaźnik do lokalizacji, do której środowisko uruchomieniowe języka wspólnego zwraca podpis. Jeśli `ppbSignatureBlob` jest wartość null, środowisko uruchomieniowe przechowuje podpisu w pliku określonym przez `wszFilePath`.  
  
 Jeśli `ppbSignatureBlob` jest inna niż null, środowisko uruchomieniowe języka wspólnego przydziela miejsce, w której ma zostać zwrócone podpis. Obiekt wywołujący musi zwolnić tego miejsca przy użyciu [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcji.  
  
 `pcbSignatureBlob`  
 [out] Rozmiar w bajtach sygnatury zwracanego.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Po pomyślnym zakończeniu; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Określ wartość null w przypadku `wszFilePath` do obliczania rozmiaru podpisu bez tworzenia podpisu.  
  
 Podpis może być przechowywany bezpośrednio w pliku lub zwracane do obiektu wywołującego.  
  
 Jeśli `StrongNameSignatureGeneration` funkcja nie jest ukończone pomyślnie, wywołaj [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcję, aby pobrać ostatni błąd wygenerowany.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StrongNameSignatureGeneration, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [StrongNameSignatureGenerationEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

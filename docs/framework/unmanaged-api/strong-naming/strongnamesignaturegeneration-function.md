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
ms.openlocfilehash: c0555299779aebc6cc37c3863e8b5504b357b262
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461496"
---
# <a name="strongnamesignaturegeneration-function"></a>StrongNameSignatureGeneration — Funkcja
Generuje podpisu silnej nazwy dla określonego zestawu.  
  
 Ta funkcja jest przestarzała. Użyj [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md) metody zamiast tego.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `wszFilePath`  
 [in] Ścieżka do pliku, który zawiera manifest zestawu, dla którego zostanie wygenerowana podpisu silnej nazwy.  
  
 `wszKeyContainer`  
 [in] Nazwa kontenera klucza, który zawiera pary kluczy publiczny/prywatny.  
  
 Jeśli `pbKeyBlob` ma wartość null, `wszKeyContainer` należy określić prawidłowy kontener w ramach dostawcy usług kryptograficznych (CSP). W takim przypadku pary kluczy przechowywanych w kontenerze jest używany do podpisywania pliku.  
  
 Jeśli `pbKeyBlob` nie ma wartości null, zakłada, że pary kluczy muszą być zawarte w klucza dużego obiektu binarnego (BLOB).  
  
 Klucze muszą być Rivest-Shamir-Adleman (RSA 1024-bitowe) kluczy podpisywania. Żadne inne typy klucze są obsługiwane w tej chwili.  
  
 `pbKeyBlob`  
 [in] Wskaźnik do pary kluczy publiczny/prywatny. Tej pary jest w formacie utworzone przez Win32 `CryptExportKey` funkcji. Jeśli `pbKeyBlob` jest null, określony przez kontener klucza `wszKeyContainer` założono, że zawiera pary kluczy.  
  
 `cbKeyBlob`  
 [in] Rozmiar w bajtach z `pbKeyBlob`.  
  
 `ppbSignatureBlob`  
 [out] Wskaźnik do lokalizacji, do którego środowisko uruchomieniowe języka wspólnego zwraca podpis. Jeśli `ppbSignatureBlob` jest wartość null, środowisko uruchomieniowe przechowuje podpisu pliku określonego przez `wszFilePath`.  
  
 Jeśli `ppbSignatureBlob` jest niezerowa, środowisko uruchomieniowe języka wspólnego przydziela miejsce, do której należy zwrócić podpisu. Obiekt wywołujący musi zwolnić przy użyciu tego miejsca [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcji.  
  
 `pcbSignatureBlob`  
 [out] Rozmiar w bajtach zwrócony podpisu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true` Po pomyślnym ukończeniu; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 Określ wartość null dla `wszFilePath` obliczyć rozmiar podpisu bez tworzenia podpisu.  
  
 Podpis może być przechowywana bezpośrednio w pliku lub zwracany do obiektu wywołującego.  
  
 Jeśli `StrongNameSignatureGeneration` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [StrongNameSignatureGeneration, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [StrongNameSignatureGenerationEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)

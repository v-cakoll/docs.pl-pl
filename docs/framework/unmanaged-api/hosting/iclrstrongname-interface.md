---
title: ICLRStrongName — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRStrongName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName
helpviewer_keywords:
- ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 2fac66fd-6b3b-4dbd-8baf-86038bd85526
topic_type:
- apiref
ms.openlocfilehash: 4f774915cdbb12b13fa334db37c8e0fa2a7e5829
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135140"
---
# <a name="iclrstrongname-interface"></a>ICLRStrongName — Interfejs
Udostępnia podstawowe globalne funkcje statyczne do podpisywania zestawów o silnych nazwach. Wszystkie metody `ICLRStrongName` zwracają standardowe wartości HRESULT modelu COM.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetHashFromAssemblyFile, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)|Pobiera skrót określonego pliku zestawu przy użyciu określonego algorytmu wyznaczania wartości skrótu.|  
|[GetHashFromAssemblyFileW, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)|Pobiera skrót pliku zestawu określony jako ciąg Unicode przy użyciu określonego algorytmu wyznaczania wartości skrótu.|  
|[GetHashFromBlob, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)|Pobiera skrót zestawu pod określonym adresem pamięci przy użyciu określonego algorytmu wyznaczania wartości skrótu.|  
|[GetHashFromFile, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)|Generuje skrót do zawartości określonego pliku.|  
|[GetHashFromFileW, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)|Generuje skrót do zawartości pliku określonego przez ciąg Unicode.|  
|[GetHashFromHandle, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)|Generuje skrót do zawartości pliku z określonym dojściem do pliku przy użyciu określonego algorytmu wyznaczania wartości skrótu.|  
|[StrongNameCompareAssemblies, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)|Określa, czy dwa zestawy różnią się tylko sygnaturami silnej nazwy.|  
|[StrongNameFreeBuffer, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)|Zwalnia pamięć, która została przypisana przy użyciu poprzedniego wywołania metody silnej nazwy, takiej jak [StrongNameGetPublicKey —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [StrongNameTokenFromPublicKey —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)lub [StrongNameSignatureGeneration —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).|  
|[StrongNameGetBlob, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)|Wypełnia określony bufor reprezentacją binarną pliku wykonywalnego pod określonym adresem.|  
|[StrongNameGetBlobFromImage, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)|Pobiera binarną reprezentację obrazu zestawu pod określonym adresem pamięci.|  
|[StrongNameGetPublicKey, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)|Pobiera klucz publiczny z pary kluczy prywatnych/publicznych.|  
|[StrongNameHashSize, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)|Pobiera rozmiar buforu wymagany dla skrótu przy użyciu określonego algorytmu wyznaczania wartości skrótu.|  
|[StrongNameKeyDelete, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)|Usuwa określony kontener kluczy.|  
|[StrongNameKeyGen, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)|Tworzy nową parę kluczy publiczny/prywatny w celu użycia silnej nazwy.|  
|[StrongNameKeyGenEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)|Generuje nową parę kluczy publicznych/prywatnych z określonym rozmiarem klucza w celu użycia silnej nazwy.|  
|[StrongNameKeyInstall, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)|Importuje parę kluczy publiczny/prywatny do kontenera.|  
|[StrongNameSignatureGeneration, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)|Generuje podpis silnej nazwy dla określonego zestawu.|  
|[StrongNameSignatureGenerationEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)|Generuje podpis silnej nazwy dla określonego zestawu, na podstawie określonych flag.|  
|[StrongNameSignatureSize, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)|Zwraca rozmiar sygnatury silnej nazwy.|  
|[StrongNameSignatureVerification, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)|Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera sygnaturę silnej nazwy, która jest sprawdzana według określonych flag.|  
|[StrongNameSignatureVerificationEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)|Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpis silnej nazwy.|  
|[StrongNameSignatureVerificationFromImage, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)|Sprawdza, czy zestaw, który został już zamapowany na pamięć, jest prawidłowy dla skojarzonego klucza publicznego.|  
|[StrongNameTokenFromAssembly, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)|Tworzy token silnej nazwy z określonego pliku zestawu.|  
|[StrongNameTokenFromAssemblyEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)|Tworzy token silnej nazwy z określonego pliku zestawu i zwraca klucz publiczny.|  
|[StrongNameTokenFromPublicKey, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)|Pobiera token reprezentujący klucz publiczny.|  
  
## <a name="remarks"></a>Uwagi  
 Możesz uzyskać wystąpienie `ICLRStrongName`, wywołując metodę [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) przy użyciu `CLSID_CLRStrongName` i `IID_ICLRStrongName` jako parametry.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)

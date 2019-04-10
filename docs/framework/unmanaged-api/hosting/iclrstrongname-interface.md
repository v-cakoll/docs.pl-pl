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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abe967195694dd61b4af18fb4eebbc3caad2ef4f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205865"
---
# <a name="iclrstrongname-interface"></a>ICLRStrongName — Interfejs
Zawiera podstawowe statyczne funkcje globalne do podpisywania zestawów o silnych nazwach. Wszystkie `ICLRStrongName` metody zwracają standardowa COM wartości HRESULT.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetHashFromAssemblyFile, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)|Pobiera skrót pliku określonego zestawu, przy użyciu określonego algorytmu skrótu.|  
|[GetHashFromAssemblyFileW, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)|Pobiera skrót pliku zestawu, określony jako ciąg Unicode przy użyciu określonego algorytmu skrótu.|  
|[GetHashFromBlob, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)|Pobiera skrót zestawu pod adresem określonym pamięci, przy użyciu określonego algorytmu skrótu.|  
|[GetHashFromFile, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)|Generuje skrót nad zawartość określonego pliku.|  
|[GetHashFromFileW, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)|Generuje skrót nad zawartość pliku określonego przez ciąg Unicode.|  
|[GetHashFromHandle, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)|Generuje skrót nad zawartość pliku przy użyciu określone dojście do pliku, przy użyciu określonego algorytmu skrótu.|  
|[StrongNameCompareAssemblies, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)|Określa, czy dwa zestawy różnią się tylko ich podpisy silnej nazwy.|  
|[StrongNameFreeBuffer, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)|Zwalnia pamięć, która została przydzielona z poprzedniego wywołania do metody silnej nazwy, takie jak [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), lub [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).|  
|[StrongNameGetBlob, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)|Wstawia określony bufor binarna reprezentacja pliku wykonywalnego pod podanym adresem.|  
|[StrongNameGetBlobFromImage, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)|Pobiera reprezentacja binarna obrazu zestawu pod adresem określonym pamięci.|  
|[StrongNameGetPublicKey, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)|Pobiera klucz publiczny z pary kluczy publiczny/prywatny.|  
|[StrongNameHashSize, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)|Pobiera rozmiar bufora wymaganych do wyznaczania wartości skrótu, za pomocą określonego algorytmu skrótu.|  
|[StrongNameKeyDelete, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)|Usuwa określony kontener kluczy.|  
|[StrongNameKeyGen, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)|Tworzy nową parę kluczy publiczny/prywatny do użytku silnej nazwy.|  
|[StrongNameKeyGenEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)|Generuje nową parę kluczy publiczny/prywatny z określonego rozmiaru klucza do użycia silnej nazwy.|  
|[StrongNameKeyInstall, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)|Importuje pary kluczy publiczny/prywatny w kontenerze.|  
|[StrongNameSignatureGeneration, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)|Generuje podpisu silnej nazwy dla określonego zestawu.|  
|[StrongNameSignatureGenerationEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)|Generuje podpisu silnej nazwy dla określonego zestawu, w oparciu o określone flagi.|  
|[StrongNameSignatureSize, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)|Zwraca rozmiar podpisu silnej nazwy.|  
|[StrongNameSignatureVerification, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)|Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpisu silnej nazwy, który jest weryfikowany zgodnie z określone flagi.|  
|[StrongNameSignatureVerificationEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)|Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpisu silnej nazwy.|  
|[StrongNameSignatureVerificationFromImage, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)|Sprawdza, czy zestaw, który został już zmapowany do pamięci jest prawidłowa dla skojarzonego klucza publicznego.|  
|[StrongNameTokenFromAssembly, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)|Tworzy token silnej nazwy z określonego pliku zestawu.|  
|[StrongNameTokenFromAssemblyEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)|Tworzy token silnej nazwy z określonego pliku zestawu i zwraca klucz publiczny.|  
|[StrongNameTokenFromPublicKey, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)|Pobiera token reprezentujący klucz publiczny.|  
  
## <a name="remarks"></a>Uwagi  
 Można pobrać wystąpienia `ICLRStrongName` przez wywołanie metody [iclrruntimeinfo::getinterface —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) przy użyciu metody `CLSID_CLRStrongName` i `IID_ICLRStrongName` jako parametry.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting — Interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)

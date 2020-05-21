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
ms.openlocfilehash: 04260429dd69f5ba1d6a94b6628979341d12b9e8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762079"
---
# <a name="iclrstrongname-interface"></a>ICLRStrongName — Interfejs
Udostępnia podstawowe globalne funkcje statyczne do podpisywania zestawów o silnych nazwach. Wszystkie `ICLRStrongName` metody zwracają standardowe wartości HRESULT modelu com.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetHashFromAssemblyFile, metoda](iclrstrongname-gethashfromassemblyfile-method.md)|Pobiera skrót określonego pliku zestawu przy użyciu określonego algorytmu wyznaczania wartości skrótu.|  
|[GetHashFromAssemblyFileW, metoda](iclrstrongname-gethashfromassemblyfilew-method.md)|Pobiera skrót pliku zestawu określony jako ciąg Unicode przy użyciu określonego algorytmu wyznaczania wartości skrótu.|  
|[GetHashFromBlob, metoda](iclrstrongname-gethashfromblob-method.md)|Pobiera skrót zestawu pod określonym adresem pamięci przy użyciu określonego algorytmu wyznaczania wartości skrótu.|  
|[GetHashFromFile, metoda](iclrstrongname-gethashfromfile-method.md)|Generuje skrót do zawartości określonego pliku.|  
|[GetHashFromFileW, metoda](iclrstrongname-gethashfromfilew-method.md)|Generuje skrót do zawartości pliku określonego przez ciąg Unicode.|  
|[GetHashFromHandle, metoda](iclrstrongname-gethashfromhandle-method.md)|Generuje skrót do zawartości pliku z określonym dojściem do pliku przy użyciu określonego algorytmu wyznaczania wartości skrótu.|  
|[StrongNameCompareAssemblies, metoda](iclrstrongname-strongnamecompareassemblies-method.md)|Określa, czy dwa zestawy różnią się tylko sygnaturami silnej nazwy.|  
|[StrongNameFreeBuffer, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)|Zwalnia pamięć, która została przypisana przy użyciu poprzedniego wywołania metody silnej nazwy, takiej jak [StrongNameGetPublicKey —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [StrongNameTokenFromPublicKey —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)lub [StrongNameSignatureGeneration —](iclrstrongname-strongnamesignaturegeneration-method.md).|  
|[StrongNameGetBlob, metoda](iclrstrongname-strongnamegetblob-method.md)|Wypełnia określony bufor reprezentacją binarną pliku wykonywalnego pod określonym adresem.|  
|[StrongNameGetBlobFromImage, metoda](iclrstrongname-strongnamegetblobfromimage-method.md)|Pobiera binarną reprezentację obrazu zestawu pod określonym adresem pamięci.|  
|[StrongNameGetPublicKey, metoda](iclrstrongname-strongnamegetpublickey-method.md)|Pobiera klucz publiczny z pary kluczy prywatnych/publicznych.|  
|[StrongNameHashSize, metoda](iclrstrongname-strongnamehashsize-method.md)|Pobiera rozmiar buforu wymagany dla skrótu przy użyciu określonego algorytmu wyznaczania wartości skrótu.|  
|[StrongNameKeyDelete, metoda](iclrstrongname-strongnamekeydelete-method.md)|Usuwa określony kontener kluczy.|  
|[StrongNameKeyGen, metoda](iclrstrongname-strongnamekeygen-method.md)|Tworzy nową parę kluczy publiczny/prywatny w celu użycia silnej nazwy.|  
|[StrongNameKeyGenEx, metoda](iclrstrongname-strongnamekeygenex-method.md)|Generuje nową parę kluczy publicznych/prywatnych z określonym rozmiarem klucza w celu użycia silnej nazwy.|  
|[StrongNameKeyInstall, metoda](iclrstrongname-strongnamekeyinstall-method.md)|Importuje parę kluczy publiczny/prywatny do kontenera.|  
|[StrongNameSignatureGeneration, metoda](iclrstrongname-strongnamesignaturegeneration-method.md)|Generuje podpis silnej nazwy dla określonego zestawu.|  
|[StrongNameSignatureGenerationEx, metoda](iclrstrongname-strongnamesignaturegenerationex-method.md)|Generuje podpis silnej nazwy dla określonego zestawu, na podstawie określonych flag.|  
|[StrongNameSignatureSize, metoda](iclrstrongname-strongnamesignaturesize-method.md)|Zwraca rozmiar sygnatury silnej nazwy.|  
|[StrongNameSignatureVerification, metoda](iclrstrongname-strongnamesignatureverification-method.md)|Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera sygnaturę silnej nazwy, która jest sprawdzana według określonych flag.|  
|[StrongNameSignatureVerificationEx, metoda](iclrstrongname-strongnamesignatureverificationex-method.md)|Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpis silnej nazwy.|  
|[StrongNameSignatureVerificationFromImage, metoda](iclrstrongname-strongnamesignatureverificationfromimage-method.md)|Sprawdza, czy zestaw, który został już zamapowany na pamięć, jest prawidłowy dla skojarzonego klucza publicznego.|  
|[StrongNameTokenFromAssembly, metoda](iclrstrongname-strongnametokenfromassembly-method.md)|Tworzy token silnej nazwy z określonego pliku zestawu.|  
|[StrongNameTokenFromAssemblyEx, metoda](iclrstrongname-strongnametokenfromassemblyex-method.md)|Tworzy token silnej nazwy z określonego pliku zestawu i zwraca klucz publiczny.|  
|[StrongNameTokenFromPublicKey, metoda](iclrstrongname-strongnametokenfrompublickey-method.md)|Pobiera token reprezentujący klucz publiczny.|  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie obiektu można uzyskać, `ICLRStrongName` wywołując metodę [ICLRRuntimeInfo:: GetInterface](iclrruntimeinfo-getinterface-method.md) przy użyciu `CLSID_CLRStrongName` `IID_ICLRStrongName` parametrów i jako.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Hosting, interfejsy](hosting-interfaces.md)
- [Hosting](index.md)

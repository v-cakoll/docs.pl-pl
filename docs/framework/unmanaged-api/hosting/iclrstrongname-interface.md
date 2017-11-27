---
title: "ICLRStrongName — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName
helpviewer_keywords: ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 2fac66fd-6b3b-4dbd-8baf-86038bd85526
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f8e8a3c9ff4ec3d6b124f95edd31e277db3eb872
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongname-interface"></a>ICLRStrongName — Interfejs
Podpisywanie zestawów o silnych nazwach zapewnia podstawowe statyczne funkcje globalne. Wszystkie `ICLRStrongName` metody zwracają standardowe COM wyników HRESULT.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetHashFromAssemblyFile — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)|Pobiera skrót określonego pliku zestawu, przy użyciu określonego algorytmu skrótu.|  
|[GetHashFromAssemblyFileW — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)|Pobiera skrót pliku zestawu określony jako ciągu Unicode, przy użyciu określonego algorytmu skrótu.|  
|[GetHashFromBlob — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)|Pobiera skrót zestawu pod adresem określonym pamięci, przy użyciu określonego algorytmu skrótu.|  
|[GetHashFromFile — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfile-method.md)|Generuje skrót za pośrednictwem zawartość określonego pliku.|  
|[GetHashFromFileW — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)|Generuje skrót za pośrednictwem zawartość pliku określona przez ciąg Unicode.|  
|[GetHashFromHandle — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)|Generuje skrót za pośrednictwem zawartość pliku z dojściem określonego pliku, przy użyciu określonego algorytmu skrótu.|  
|[StrongNameCompareAssemblies — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)|Określa, czy dwa zestawy różnią się tylko ich podpisów silnej nazwy.|  
|[StrongNameFreeBuffer — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)|Zwalnia pamięć, która została przydzielona z poprzedniego wywołania metody silnej nazwy, takie jak [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md), lub [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md).|  
|[StrongNameGetBlob — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)|Wstawia określony bufor binarna reprezentacja pliku wykonywalnego pod określonym adresem.|  
|[StrongNameGetBlobFromImage — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)|Pobiera zestawu obraz to binarna reprezentacja pod adresem określonym pamięci.|  
|[StrongNameGetPublicKey — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)|Pobiera klucz publiczny z pary kluczy publiczny/prywatny.|  
|[StrongNameHashSize — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamehashsize-method.md)|Pobiera wymagane dla skrótu, przy użyciu algorytmu wyznaczania wartości skrótu określonej rozmiar buforu.|  
|[StrongNameKeyDelete — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)|Usuwa określony kontener klucza.|  
|[StrongNameKeyGen — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)|Tworzy nową parę kluczy publicznych/prywatnych do użytku silnej nazwy.|  
|[StrongNameKeyGenEx — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)|Generuje nową parę kluczy publicznych i prywatnych z określonym rozmiarem klucza do użycia silnej nazwy.|  
|[StrongNameKeyInstall — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)|Importuje pary kluczy publicznych/prywatnych do kontenera.|  
|[StrongNameSignatureGeneration — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)|Generuje podpisu silnej nazwy dla określonego zestawu.|  
|[StrongNameSignatureGenerationEx — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)|Generuje podpisu silnej nazwy dla określonego zestawu, oparte na określonych flag.|  
|[StrongNameSignatureSize — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturesize-method.md)|Zwraca rozmiar podpisu silnej nazwy.|  
|[StrongNameSignatureVerification — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)|Pobiera wartość wskazującą, czy manifest zestawu w podana ścieżka zawiera podpisu silnej nazwy, która zostanie poddana weryfikacji zgodnie z określonym flagi.|  
|[StrongNameSignatureVerificationEx — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)|Pobiera wartość wskazującą, czy manifest zestawu w podana ścieżka zawiera podpisu silnej nazwy.|  
|[StrongNameSignatureVerificationFromImage — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)|Sprawdza, czy zestaw, który został już zmapowany do pamięci jest nieprawidłowa dla klucza publicznego.|  
|[StrongNameTokenFromAssembly — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)|Tworzy token silnej nazwy z określonego pliku zestawu.|  
|[StrongNameTokenFromAssemblyEx — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)|Tworzy token silnej nazwy z określonego pliku zestawu i zwraca klucz publiczny.|  
|[StrongNameTokenFromPublicKey — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)|Pobiera token reprezentujący klucza publicznego.|  
  
## <a name="remarks"></a>Uwagi  
 Można pobrać wystąpienia `ICLRStrongName` przez wywołanie metody [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) przy użyciu metody `CLSID_CLRStrongName` i `IID_ICLRStrongName` jako parametry.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting — interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)

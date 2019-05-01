---
title: Silne nazewnictwo (Niezarządzany wykaz interfejsów API)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 32e74a76b6b1bedee4efc5715d0710c8efce2455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049378"
---
# <a name="strong-naming-unmanaged-api-reference"></a>Silne nazewnictwo (Niezarządzany wykaz interfejsów API)
Silnych nazw interfejsu API umożliwia klientowi do administrowania podpisywania zestawów silnymi nazwami.  
  
 Podpisanie zestawu silną nazwą dodaje szyfrowanie kluczem publicznym do pliku zawierającego manifest zestawu. Podpis silnej nazwy pomaga zweryfikować unikatowość nazwy, uniemożliwia fałszowanie nazwy i zapewnia wywołań przy użyciu unikatowych tożsamości, gdy odwołanie nie zostanie rozwiązany. Jednak żaden poziom zaufania jest skojarzony z silną nazwą.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
> [!NOTE]
>  Wszystkie te funkcje są przestarzałe począwszy od [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Sugerowane rozwiązania alternatywne, można zobaczyć [iclrstrongname —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) interfejsu.  
  
 [GetHashFromAssemblyFile, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfile-function.md)  
 Pobiera skrót pliku określonego zestawu, przy użyciu określonego algorytmu skrótu. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromAssemblyFileW, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfilew-function.md)  
 Pobiera skrót pliku zestawu, określony jako ciąg Unicode przy użyciu określonego algorytmu skrótu. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromBlob, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromblob-function.md)  
 Pobiera skrót zestawu pod adresem określonym pamięci, przy użyciu określonego algorytmu skrótu. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromFile, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)  
 Generuje skrót nad zawartość określonego pliku.  Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromFileW, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)  
 Generuje skrót nad zawartość pliku określonego przez ciąg Unicode. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromHandle, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromhandle-function.md)  
 Generuje skrót nad zawartość pliku przy użyciu określone dojście do pliku, przy użyciu określonego algorytmu skrótu.  Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameCompareAssemblies, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamecompareassemblies-function.md)  
 Określa, czy dwa zestawy różnią się tylko ich podpisy silnej nazwy. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameErrorInfo, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)  
 Pobiera kod ostatniego błędu, który został zgłoszony przez jedną z funkcji silnej nazwy.  
  
 [StrongNameFreeBuffer, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)  
 Zwalnia pamięć, która została przydzielona z poprzedniego wywołania do funkcji silnej nazwy, takie jak [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), lub [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).   Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameGetBlob, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblob-function.md)  
 Wstawia określony bufor binarna reprezentacja pliku wykonywalnego pod podanym adresem. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameGetBlobFromImage, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblobfromimage-function.md)  
 Pobiera reprezentacja binarna obrazu zestawu pod adresem określonym pamięci. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameGetPublicKey, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 Pobiera klucz publiczny z pary kluczy publiczny/prywatny. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameHashSize, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamehashsize-function.md)  
 Pobiera rozmiar bufora wymaganych do wyznaczania wartości skrótu, za pomocą określonego algorytmu skrótu.  Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyDelete, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)  
 Usuwa określony kontener kluczy. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyGen, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygen-function.md)  
 Tworzy nową parę kluczy publiczny/prywatny do użytku silnej nazwy.  Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyGenEx, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygenex-function.md)  
 Generuje nową parę kluczy publiczny/prywatny z określonego rozmiaru klucza do użycia silnej nazwy. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyInstall, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)  
 Importuje pary kluczy publiczny/prywatny w kontenerze.  Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureGeneration, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 Generuje podpisu silnej nazwy dla określonego zestawu.   Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureGenerationEx, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegenerationex-function.md)  
 Generuje podpisu silnej nazwy dla określonego zestawu, w oparciu o określone flagi.    Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureSize, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)  
 Zwraca rozmiar podpisu silnej nazwy. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureVerification, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)  
 Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpisu silnej nazwy, który jest weryfikowany zgodnie z określone flagi. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureVerificationEx, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationex-function.md)  
 Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpisu silnej nazwy.  Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureVerificationFromImage, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationfromimage-function.md)  
 Sprawdza, czy zestaw, który został już zmapowany do pamięci jest prawidłowa dla skojarzonego klucza publicznego. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromAssembly, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)  
 Tworzy token silnej nazwy z określonego pliku zestawu.  Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromAssemblyEx, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassemblyex-function.md)  
 Tworzy token silnej nazwy z określonego pliku zestawu i zwraca klucz publiczny. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromPublicKey, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)  
 Pobiera token reprezentujący klucz publiczny. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [PublicKeyBlob, struktura](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 Reprezentuje klucz publiczny z pary kluczy publiczny/prywatny w formacie binarnym.  
  
## <a name="see-also"></a>Zobacz także

- [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [Niezarządzane interfejsy API — informacje](../../../../docs/framework/unmanaged-api/index.md)

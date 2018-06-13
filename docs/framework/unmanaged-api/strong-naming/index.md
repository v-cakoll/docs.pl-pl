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
ms.openlocfilehash: 6c397a325edb49e3f10a46b242888b8d138957af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33462380"
---
# <a name="strong-naming-unmanaged-api-reference"></a>Silne nazewnictwo (Niezarządzany wykaz interfejsów API)
Silnych nazw interfejsu API umożliwia klientowi administrowania silnej nazwy podpisywania dla zestawów.  
  
 Podpisanie zestawu silną nazwą dodaje szyfrowanie kluczem publicznym do pliku zawierającego manifest zestawu. Podpisywanie silną nazwą pomaga Sprawdź unikatowość nazwy uniemożliwia fałszowania nazwy i udostępnia obiekty wywołujące unikatową tożsamość, gdy odwołanie zostało rozpoznane. Jednak żaden poziom zaufania jest skojarzony z silnej nazwy.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Silnych nazw statyczne funkcje globalne](http://msdn.microsoft.com/library/efa715df-e8cc-48f2-9ec4-26586f0dc8d0)  
 Opisuje niezarządzane statyczne funkcje globalne, używane silnych nazw interfejsu API.  
  
> [!NOTE]
>  Wszystkie te funkcje są przestarzałe począwszy od [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Aby sugerowane rozwiązań alternatywnych, zobacz [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) interfejsu.  
  
 [GetHashFromAssemblyFile, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfile-function.md)  
 Pobiera skrót określonego pliku zestawu, przy użyciu określonego algorytmu skrótu. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromAssemblyFileW, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromassemblyfilew-function.md)  
 Pobiera skrót pliku zestawu określony jako ciągu Unicode, przy użyciu określonego algorytmu skrótu. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromBlob, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromblob-function.md)  
 Pobiera skrót zestawu pod adresem określonym pamięci, przy użyciu określonego algorytmu skrótu. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromFile, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfile-function.md)  
 Generuje skrót za pośrednictwem zawartość określonego pliku.  Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromFileW, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromfilew-function.md)  
 Generuje skrót za pośrednictwem zawartość pliku określona przez ciąg Unicode. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [GetHashFromHandle, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/gethashfromhandle-function.md)  
 Generuje skrót za pośrednictwem zawartość pliku z dojściem określonego pliku, przy użyciu określonego algorytmu skrótu.  Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameCompareAssemblies, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamecompareassemblies-function.md)  
 Określa, czy dwa zestawy różnią się tylko ich podpisów silnej nazwy. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameErrorInfo, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)  
 Pobiera ostatni kod błędu zgłoszonego przez jedną z funkcji silnej nazwy.  
  
 [StrongNameFreeBuffer, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)  
 Zwalnia pamięć, która została przydzielona z poprzedniego wywołania funkcji silnej nazwy, takie jak [StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), lub [StrongNameSignatureGeneration ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).   Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameGetBlob, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblob-function.md)  
 Wstawia określony bufor binarna reprezentacja pliku wykonywalnego pod określonym adresem. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameGetBlobFromImage, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetblobfromimage-function.md)  
 Pobiera zestawu obraz to binarna reprezentacja pod adresem określonym pamięci. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameGetPublicKey, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md)  
 Pobiera klucz publiczny z pary kluczy publiczny/prywatny. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameHashSize, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamehashsize-function.md)  
 Pobiera wymagane dla skrótu, przy użyciu algorytmu wyznaczania wartości skrótu określonej rozmiar buforu.  Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyDelete, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md)  
 Usuwa określony kontener klucza. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyGen, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygen-function.md)  
 Tworzy nową parę kluczy publicznych/prywatnych do użytku silnej nazwy.  Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyGenEx, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeygenex-function.md)  
 Generuje nową parę kluczy publicznych i prywatnych z określonym rozmiarem klucza do użycia silnej nazwy. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameKeyInstall, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md)  
 Importuje pary kluczy publicznych/prywatnych do kontenera.  Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureGeneration, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md)  
 Generuje podpisu silnej nazwy dla określonego zestawu.   Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureGenerationEx, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegenerationex-function.md)  
 Generuje podpisu silnej nazwy dla określonego zestawu, oparte na określonych flag.    Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureSize, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md)  
 Zwraca rozmiar podpisu silnej nazwy. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureVerification, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)  
 Pobiera wartość wskazującą, czy manifest zestawu w podana ścieżka zawiera podpisu silnej nazwy, która zostanie poddana weryfikacji zgodnie z określonym flagi. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureVerificationEx, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationex-function.md)  
 Pobiera wartość wskazującą, czy manifest zestawu w podana ścieżka zawiera podpisu silnej nazwy.  Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameSignatureVerificationFromImage, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverificationfromimage-function.md)  
 Sprawdza, czy zestaw, który został już zmapowany do pamięci jest nieprawidłowa dla klucza publicznego. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromAssembly, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassembly-function.md)  
 Tworzy token silnej nazwy z określonego pliku zestawu.  Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromAssemblyEx, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfromassemblyex-function.md)  
 Tworzy token silnej nazwy z określonego pliku zestawu i zwraca klucz publiczny. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [StrongNameTokenFromPublicKey, funkcja](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md)  
 Pobiera token reprezentujący klucza publicznego. Przestarzałe, począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
 [Silne nazewnictwo — struktura](http://msdn.microsoft.com/library/4b041a2f-fd12-4b91-aacd-bc3b34a5124d)  
 W tym artykule opisano struktura niezarządzana, używaną do administrowania silnej nazwy podpisywania dla zestawów silnych nazw interfejsu API...  
  
 [PublicKeyBlob, struktura](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 Reprezentuje klucz publiczny w formacie binarnym pary kluczy publiczny/prywatny.  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [Niezarządzane interfejsy API — informacje](../../../../docs/framework/unmanaged-api/index.md)

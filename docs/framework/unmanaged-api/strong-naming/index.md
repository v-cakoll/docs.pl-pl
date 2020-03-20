---
title: Silne nazewnictwo (Niezarządzany wykaz interfejsów API)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 7d18513450111d58b5d26fd834addd465cfc4267
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73140632"
---
# <a name="strong-naming-unmanaged-api-reference"></a>Silne nazewnictwo (Niezarządzany wykaz interfejsów API)
Silny interfejs API nazewnictwa umożliwia klientowi administrowanie podpisywaniem silnej nazwy dla zestawów.  
  
 Podpisanie zestawu silną nazwą dodaje szyfrowanie kluczem publicznym do pliku zawierającego manifest zestawu. Silne podpisywanie nazw pomaga zweryfikować unikatowość nazwy, zapobiega fałszowaniu nazw i zapewnia wywołującym unikatową tożsamość po rozwiązaniu odwołania. Jednak żaden poziom zaufania nie jest skojarzony z silną nazwą.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
> [!NOTE]
> Wszystkie te funkcje zostały przestarzałe, począwszy od programu .NET Framework 4. Aby uzyskać sugerowane alternatywy, zobacz interfejs [ICLRStrongName.](../hosting/iclrstrongname-interface.md)  
  
 [GetHashFromAssemblyFile, funkcja](gethashfromassemblyfile-function.md)  
 Pobiera skrót określonego pliku zestawu, przy użyciu określonego algorytmu mieszania. Przestarzałe począwszy od programu .NET Framework 4.  
  
 [GetHashFromAssemblyFileW, funkcja](gethashfromassemblyfilew-function.md)  
 Pobiera skrót pliku zestawu określony jako ciąg Unicode, przy użyciu określonego algorytmu mieszania. Przestarzałe począwszy od programu .NET Framework 4.  
  
 [GetHashFromBlob, funkcja](gethashfromblob-function.md)  
 Pobiera skrót zestawu przy określonym adresie pamięci, przy użyciu określonego algorytmu mieszania. Przestarzałe począwszy od programu .NET Framework 4.  
  
 [GetHashFromFile — Funkcja](gethashfromfile-function.md)  
 Generuje skrót nad zawartością określonego pliku.  Przestarzałe począwszy od programu .NET Framework 4.  
  
 [GetHashFromFileW, funkcja](gethashfromfilew-function.md)  
 Generuje skrót nad zawartością pliku określonego przez ciąg Unicode. Przestarzałe począwszy od programu .NET Framework 4.  
  
 [GetHashFromHandle, funkcja](gethashfromhandle-function.md)  
 Generuje skrót nad zawartością pliku z określonym uchwytem pliku przy użyciu określonego algorytmu mieszania.  Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameCompareAssemblies — Funkcja](strongnamecompareassemblies-function.md)  
 Określa, czy dwa zestawy różnią się tylko ich silne podpisy nazw. Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameErrorInfo, funkcja](strongnameerrorinfo-function.md)  
 Pobiera ostatni kod błędu, który został podniesiony przez jedną z funkcji silnej nazwy.  
  
 [StrongNameFreeBuffer — Funkcja](strongnamefreebuffer-function.md)  
 Zwalnia pamięć, która została przydzielona przy poprzednim wywołaniu funkcji silnej nazwy, takiej jak [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)lub [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).   Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameGetBlob, funkcja](strongnamegetblob-function.md)  
 Wypełnia określony bufor binarną reprezentacją pliku wykonywalnego pod określonym adresem. Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameGetBlobFromImage, funkcja](strongnamegetblobfromimage-function.md)  
 Pobiera binarną reprezentację obrazu zestawu pod określonym adresem pamięci. Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameGetPublicKey, funkcja](strongnamegetpublickey-function.md)  
 Pobiera klucz publiczny z pary klucza prywatnego/publicznego. Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameHashSize — Funkcja](strongnamehashsize-function.md)  
 Pobiera rozmiar buforu wymagane dla mieszania, przy użyciu algorytmu określonego mieszania.  Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameKeyDelete — Funkcja](strongnamekeydelete-function.md)  
 Usuwa określony kontener kluczy. Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameKeyGen, funkcja](strongnamekeygen-function.md)  
 Tworzy nową parę kluczy publicznych/prywatnych do silnego używania nazw.  Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameKeyGenEx, funkcja](strongnamekeygenex-function.md)  
 Generuje nową parę klucza publicznego/prywatnego o określonym rozmiarze klucza dla silnego użycia nazwy. Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameKeyInstall, funkcja](strongnamekeyinstall-function.md)  
 Importuje parę klucza publicznego/prywatnego do kontenera.  Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameSignatureGeneration, funkcja](strongnamesignaturegeneration-function.md)  
 Generuje podpis silnej nazwy dla określonego zestawu.   Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameSignatureGenerationEx — Funkcja](strongnamesignaturegenerationex-function.md)  
 Generuje podpis silnej nazwy dla określonego zestawu, na podstawie określonych flag.    Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameSignatureSize, funkcja](strongnamesignaturesize-function.md)  
 Zwraca rozmiar podpisu silnej nazwy. Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameSignatureVerification, funkcja](strongnamesignatureverification-function.md)  
 Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpis silnej nazwy, który jest weryfikowany zgodnie z określonymi flagami. Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameSignatureVerificationEx, funkcja](strongnamesignatureverificationex-function.md)  
 Pobiera wartość wskazującą, czy manifest zestawu w podanej ścieżce zawiera podpis silnej nazwy.  Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameSignatureVerificationFromImage, funkcja](strongnamesignatureverificationfromimage-function.md)  
 Sprawdza, czy zestaw, który został już zamapowany do pamięci jest prawidłowy dla skojarzonego klucza publicznego. Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameTokenFromAssembly, funkcja](strongnametokenfromassembly-function.md)  
 Tworzy token silnej nazwy z określonego pliku zestawu.  Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameTokenFromAssemblyEx, funkcja](strongnametokenfromassemblyex-function.md)  
 Tworzy token silnej nazwy z określonego pliku zestawu i zwraca klucz publiczny. Przestarzałe począwszy od programu .NET Framework 4.  
  
 [StrongNameTokenFromPublicKey, funkcja](strongnametokenfrompublickey-function.md)  
 Pobiera token reprezentujący klucz publiczny. Przestarzałe począwszy od programu .NET Framework 4.  
  
 [PublicKeyBlob — Struktura](publickeyblob-structure.md)  
 Reprezentuje klucz publiczny pary klucza publicznego/prywatnego w formacie binarnym.  
  
## <a name="see-also"></a>Zobacz też

- [ICLRStrongName, interfejs](../hosting/iclrstrongname-interface.md)
- [Niezarządzany wykaz interfejsów API](../index.md)

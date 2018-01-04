---
title: "Porady: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d459ac318f2c4a3911830d08e26b31ae5366e896
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a>Porady: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe
Istnieją dwa sposoby Generowanie podstawowego zestawu międzyoperacyjnego:  
  
-   Przy użyciu [wpisz Importer biblioteki (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) dostarczonych przez [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
     Najbardziej oczywistym sposobem uzyskania podstawowe zestawy międzyoperacyjne jest użycie [Tlbimp.exe (Importer biblioteki typów)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Tlbimp.exe zapewnia następujące mechanizmy:  
  
    -   Sprawdza, czy inne zarejestrowane podstawowe zestawy międzyoperacyjne przed utworzeniem nowego zestawy międzyoperacyjne odwołań biblioteki typu zagnieżdżonego.  
  
    -   Nie można wyemitować podstawowego zestawu międzyoperacyjnego, jeśli nie określisz kontener lub nazwę pliku, aby zapewnić podstawowy zestaw międzyoperacyjny silnej nazwy.  
  
    -   Nie można wyemitować podstawowego zestawu międzyoperacyjnego, jeśli pominięto odwołania do zestawów zależnych.  
  
    -   Nie można wyemitować podstawowy zestaw międzyoperacyjny dodania odwołania do zestawów zależnych, które nie są podstawowe zestawy międzyoperacyjne.  
  
-   Podstawowe zestawy międzyoperacyjne ręczne tworzenie w kodzie źródłowym przy użyciu języka, który jest zgodny z typowych Language Specification (ze specyfikacją CLS), takich jak C#. Takie rozwiązanie jest przydatne, gdy biblioteka typów jest niedostępny.  
  
 Musi mieć pary kluczy kryptograficznych można podpisać zestawu o silnej nazwie. Aby uzyskać więcej informacji, zobacz [tworzenie pary klucz A](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).  
  
### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a>Aby wygenerować podstawowego zestawu międzyoperacyjnego przy użyciu Tlbimp.exe  
  
1.  W wierszu polecenia wpisz polecenie:  
  
     **tlbimp** *tlbfile***/primary/KeyFile:** *filename* **/out:** *assemblyname*   
  
     W tym poleceniu *tlbfile* jest plik zawierający biblioteki typów COM *filename* to nazwa kontenera lub plik, który zawiera pary kluczy i *assemblyname* jest Nazwa logowania przy użyciu silnej nazwy zestawu.  
  
 Podstawowe zestawy międzyoperacyjne może odwoływać się tylko inne podstawowe zestawy międzyoperacyjne. Jeśli Twoje zestawu odwołuje się do typów z biblioteki typów COM innych firm, należy uzyskać podstawowy zestaw międzyoperacyjny wydawcy przed wygenerowaniem Twojego podstawowego zestawu międzyoperacyjnego. Jeśli jesteś wydawcy, należy wygenerować podstawowy zestaw międzyoperacyjny dla biblioteki typów zależnych przed wygenerowaniem odwołaniem do podstawowego zestawu międzyoperacyjnego.  
  
 Zależne podstawowego zestawu międzyoperacyjnego z numerem wersji, która różni się od oryginalnej biblioteki typów nie jest wykrywalny, gdy zainstalowane w bieżącym katalogu. Należy zarejestrować zależnych podstawowy zestaw międzyoperacyjny w rejestrze systemu Windows lub użyj **/reference** opcji, należy upewnić się, że Tlbimp.exe znajdzie zależnej biblioteki DLL.  
  
 Można również zawijać wielu wersji biblioteki typów. Aby uzyskać instrukcje, zobacz [porady: zawijanie wielu wersji z biblioteki typów](http://msdn.microsoft.com/en-us/79eefe04-a770-4bc3-8ea2-e90ddb8ec31f).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład importuje Biblioteka typów COM `LibUtil.tlb` i podpisuje zestawu `LibUtil.dll` przy użyciu silnej nazwy przy użyciu pliku klucza `CompanyA.snk`. Pomijając nazwę określonych przestrzeni nazw, w tym przykładzie tworzy domyślną przestrzeń nazw, `LibUtil`.  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll  
```  
  
 Dla nazwy opisowej (przy użyciu *Nazwa_producenta*. *LibraryName* nazewnictwa wytyczne), poniższy przykład przesłania domyślną nazwę pliku zestawu i nazwa przestrzeni nazw.  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll  
```  
  
 Poniższy przykład importuje `MyLib.tlb`, które odwołania `CompanyA.LibUtil.dll`, i podpisuje zestawu `CompanyB.MyLib.dll` przy użyciu silnej nazwy przy użyciu pliku klucza `CompanyB.snk`. Przestrzeń nazw, `CompanyB.MyLib`, zastępuje domyślną nazwę przestrzeni nazw.  
  
```  
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Rejestrowanie podstawowych zestawów międzyoperacyjnych](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)

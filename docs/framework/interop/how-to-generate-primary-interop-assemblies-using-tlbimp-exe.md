---
title: 'Instrukcje: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe'
ms.date: 03/30/2017
helpviewer_keywords:
- primary interop assemblies, generating
- Tlbimp.exe
- Type Library Importer
ms.assetid: 5419011c-6e57-40f6-8c65-386db8f7a651
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a944cf87783c59c21bffc9c48a18237c9fe6cdec
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295500"
---
# <a name="how-to-generate-primary-interop-assemblies-using-tlbimpexe"></a>Instrukcje: Generowanie zestawów podstawowej obsługi międzyoperacyjnej przy użyciu programu Tlbimp.exe
Istnieją dwa sposoby generowania podstawowego zestawu międzyoperacyjnego:  
  
-   Za pomocą [wpisz Importer biblioteki (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) dostarczone przez [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].  
  
     Najprostszy sposób do tworzenia podstawowych zestawów międzyoperacyjnych polega na użyciu [Tlbimp.exe (Importer biblioteki typów)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Tlbimp.exe zawiera następujące mechanizmy:  
  
    -   Sprawdza, czy inne zarejestrowanych podstawowych zestawach międzyoperacyjnych, przed utworzeniem nowego zestawy międzyoperacyjne dla żadnych odwołań do biblioteki typu zagnieżdżonego.  
  
    -   Nie Emituj podstawowego zestawu międzyoperacyjnego, jeśli nie określisz kontenera lub nazwę pliku, aby zapewnić podstawowy zestaw międzyoperacyjny silnej nazwy.  
  
    -   Nie można wyemitować podstawowy zestaw międzyoperacyjny, jeśli pominięto odwołania do zestawów zależnych.  
  
    -   Nie Emituj podstawowy zestaw międzyoperacyjny, po dodaniu odwołania do zestawów zależnych, które nie są podstawowe zestawy międzyoperacyjne.  
  
-   Ręczne tworzenie podstawowych zestawów międzyoperacyjnych w kodzie źródłowym przy użyciu języka, który jest zgodny z Common Language Specification (CLS), takich jak C#. Takie podejście jest przydatne, gdy biblioteki typów jest niedostępny.  
  
 Musisz mieć parę kluczy kryptograficznych, aby podpisać zestaw silną nazwą. Aby uzyskać więcej informacji, zobacz [tworzenia pary klucz](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md).  
  
### <a name="to-generate-a-primary-interop-assembly-using-tlbimpexe"></a>Aby wygenerować podstawowego zestawu międzyoperacyjnego przy użyciu Tlbimp.exe  
  
1. W wierszu polecenia wpisz polecenie:  
  
     **tlbimp** *tlbfile***/primary/KeyFile:** *filename* **/out:** *assemblyname*  
  
     W tym poleceniu *tlbfile* to plik biblioteki typów modelu COM, zawierającą *filename* to nazwa kontenera lub pliku, który zawiera pary kluczy i *assemblyname* jest Nazwa zestawu, aby zalogować się przy użyciu silnej nazwy.  
  
 Podstawowe zestawy międzyoperacyjne może odwoływać się tylko inne podstawowe zestawy międzyoperacyjne. Jeśli zestaw odwołuje się do typów w bibliotece typów modelu COM innych firm, należy uzyskać podstawowy zestaw międzyoperacyjny od wydawcy przed wygenerowaniem Twojego podstawowego zestawu międzyoperacyjnego. Jeśli jesteś wydawcą, należy wygenerować podstawowego zestawu międzyoperacyjnego dla zależnej biblioteki typów przed wygenerowaniem odwołujący się podstawowy zestaw międzyoperacyjny.  
  
 Zależne podstawowego zestawu międzyoperacyjnego z numerem wersji, która różni się od oryginalnej biblioteki typów nie jest stała się wykrywalna zainstalowany w bieżącym katalogu. Należy zarejestrować zależne podstawowy zestaw międzyoperacyjny w rejestrze systemu Windows lub użyj **/reference** opcji, należy upewnić się, że Tlbimp.exe znajdzie zależnej biblioteki DLL.  
  
 Można również opakować wielu wersji biblioteki typów. Aby uzyskać instrukcje, zobacz [jak: OPAKOWYWANIE wielu wersji bibliotek typów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/1565h6hc(v=vs.100)).  
  
## <a name="example"></a>Przykład  
 Następujący przykład importuje biblioteki typów COM `LibUtil.tlb` i podpisuje zestaw `LibUtil.dll` silną nazwą przy użyciu pliku klucza `CompanyA.snk`. Pomijając nazwę określonej przestrzeni nazw, ten przykład generuje domyślny obszar nazw `LibUtil`.  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /out:LibUtil.dll  
```  
  
 Aby uzyskać bardziej opisową nazwę (przy użyciu *Nazwa_producenta*. *LibraryName* wskazówkami dotyczącymi nazewnictwa), poniższy przykład zastępuje domyślną nazwę pliku zestawu i przestrzeni nazw.  
  
```  
tlbimp LibUtil.tlb /primary /keyfile:CompanyA.snk /namespace:CompanyA.LibUtil /out:CompanyA.LibUtil.dll  
```  
  
 Następujący przykład importuje `MyLib.tlb`, która odwołuje się do `CompanyA.LibUtil.dll`, i podpisuje zestaw `CompanyB.MyLib.dll` silną nazwą przy użyciu pliku klucza `CompanyB.snk`. Przestrzeń nazw, `CompanyB.MyLib`, przesłania domyślną nazwę przestrzeni nazw.  
  
```  
tlbimp MyLib.tlb /primary /keyfile:CompanyB.snk /namespace:CompanyB.MyLib /reference:CompanyA.LibUtil.dll /out:CompanyB.MyLib.dll  
```  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Rejestrowanie podstawowych zestawów międzyoperacyjnych](../../../docs/framework/interop/how-to-register-primary-interop-assemblies.md)

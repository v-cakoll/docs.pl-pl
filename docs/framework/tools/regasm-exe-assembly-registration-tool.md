---
title: "Regasm.exe (Narzędzie rejestracji zestawów)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Assembly Registration tool
- assemblies [.NET Framework], registering
- Regasm.exe
- registering assemblies
ms.assetid: e190e342-36ef-4651-a0b4-0e8c2c0281cb
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 21da853d442a86eb42d04ff4f32d9f2798e14477
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="regasmexe-assembly-registration-tool"></a>Regasm.exe (Narzędzie rejestracji zestawów)
Narzędzie do rejestracji zestawów czyta metadane w zestawie i dodaje niezbędne wpisy do rejestru, co umożliwia klientom COM przejrzyste tworzenie klas .NET Framework. Po zarejestrowaniu klasy dowolny klient COM może jej używać tak, jakby była klasą modelu COM. Klasa jest rejestrowana tylko raz, kiedy zestaw jest instalowany. Nie można utworzyć wystąpień klas w zestawie z COM, dopóki nie zostaną one faktycznie zarejestrowane.  
  
 Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
regasm assemblyFile [options]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|*assemblyFile*|Zestaw do rejestracji w modelu COM.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/ codebase**|Tworzy wpis Codebase w rejestrze. Wpis Codebase określa ścieżkę pliku dla zestawu, który nie jest zainstalowany w globalnej pamięci podręcznej zestawów. Nie należy określać tej opcji, jeśli później instalowany będzie zestaw, który jest rejestrowany w globalnej pamięci podręcznej zestawów. *AssemblyFile* argument, który określisz z **/ codebase** opcja musi być [zestawu z silną nazwą](../../../docs/framework/app-domains/strong-named-assemblies.md).|  
|**/ zarejestrowany**|Określa, że narzędzie będzie odnosić się tylko do bibliotek typów, które zostały już zarejestrowane.|  
|**asmpath**|Określa katalog zawierający odwołania do zestawów. Musi być używany z **/RegFile** opcji.|  
|**/ nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/ RegFile** [**:** *polecenia regFile*]|Generuje określony plik reg dla zestawu zawierający potrzebne wpisy rejestru. Zaznaczenie tej opcji nie powoduje zmiany rejestru. Nie można użyć tej opcji z **/u** lub **/TLB** opcje.|  
|**/ silent** lub   **/s**|Pomija wyświetlanie komunikatów o sukcesie.|  
|**/ TLB** [**:** *typeLibFile*]|Generuje bibliotekę typów z określonego zestawu zawierającego definicje dostępnych typów zdefiniowanych w zestawie.|  
|**/ unregister** lub **/u**|Wyrejestrowuje możliwość utworzenia klasy w *assemblyFile*. Pominięcie tej opcji powoduje, że Regasm.exe rejestruje utworzone klasy w zestawie.|  
|**/ verbose**|Określa tryb pełny; Wyświetla listę wszelkie odwołania do zestawów, dla których ma zostać wygenerowany, gdy określony za pomocą biblioteki typów **/TLB** opcji.|  
|**/?** lub   **/help**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
> [!NOTE]
>  W opcjach wiersza polecenia programu Regasm.exe nie jest rozróżniana wielkość liter. Wystarczy podać część nazwy opcji umożliwiającą jej jednoznaczną identyfikację. Na przykład  **/n**  jest odpowiednikiem **/nologo** i **/t:** *outfile.tlb* jest odpowiednikiem   **/TLB:**  *outfile.tlb*.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć **/RegFile** opcję, aby wygenerować plik .reg, który zawiera wpisy rejestru zamiast wprowadzania zmian bezpośrednio do rejestru. Można zaktualizować rejestr na komputerze przez zaimportowanie pliku reg za pomocą narzędzia Edytora rejestru (Regedit.exe). Należy zauważyć, że plik reg nie zawiera żadnych aktualizacji rejestru, które mogą być wykonane przez funkcje rejestru zdefiniowane przez użytkownika.  Należy pamiętać, że **/RegFile** opcji emituje tylko wpisy rejestru dla klas zarządzanych.  Ta opcja nie Emituj wpisy dla `TypeLibID`s lub `InterfaceID`s.  
  
 Po określeniu **/TLB** opcji Regasm.exe generuje i rejestruje zawierająca opis typów w zestawie znaleziono biblioteki typów. Regasm.exe umieszcza wygenerowane biblioteki typów w bieżącym katalogu roboczym lub katalogu określonym dla pliku wyjściowego. Generowanie biblioteki typów dla zestawu, który odwołuje się do innych zestawów może spowodować, że zostanie wygenerowanych kilka bibliotek typów na raz. Można podać informacje o typie do narzędzi programistycznych, takich jak biblioteki typów [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]. Nie należy używać **/TLB** opcji rejestrowania zestaw został utworzony przez Importer biblioteki typów ([Tlbimp.exe](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)). Nie można wyeksportować biblioteki typów z zestawu, który został zaimportowany z biblioteki typów. Przy użyciu **/TLB** opcja działa tak samo jak przy użyciu Eksporter biblioteki typów ([Tlbexp.exe](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)) i Regasm.exe z Tlbexp.exe nie zarejestrować biblioteki typów, generuje wyjątek.  Jeśli używasz **/TLB** opcję, aby zarejestrować biblioteki typów, możesz użyć **/TLB** opcję z **/ unregister** opcję, aby wyrejestrować biblioteki typów. Użycie obu tych opcji razem wyrejestruje bibliotekę typów i wpisy interfejsu, co może znacznie oczyścić rejestr.  
  
 Po zarejestrowaniu zestawu do użycia przez model COM, Regasm.exe dodaje wpisy do rejestru komputera lokalnego. Dokładniej, tworzy zależne od wersji klucze rejestru, które umożliwiają równoległe uruchomienie na komputerze wielu wersji tego samego zestawu. Gdy zestaw jest rejestrowany po raz pierwszy, tworzony jest jeden klucz najwyższego poziomu dla zestawu i unikatowy podklucz dla określonej wersji. Za każdym razem, gdy rejestrowana jest nowa wersja zestawu, Regasm.exe tworzy podklucz dla nowej wersji.  
  
 Na przykład rozważmy scenariusz, w którym rejestrujemy składnik zarządzany myComp.dll w wersji 1.0.0.0 do użycia przez model COM. Później można zarejestrować myComp.dll w wersji 2.0.0.0. Należy określić, że wszystkie aplikacje klienckie modelu COM na komputerze używają myComp.dll w wersji 2.0.0.0 i użytkownik decyduje się wyrejestrować myComponent.dll w wersji 1.0.0.0. Schemat rejestru umożliwia wyrejestrowanie myComp.dll w wersji 1.0.0.0, ponieważ jest usuwany tylko podklucz wersji 1.0.0.0.  
  
 Po zarejestrowaniu zestawu za pomocą Regasm.exe, możesz je zainstalować w [Globalna pamięć podręczna zestawów](../../../docs/framework/app-domains/gac.md) , dzięki czemu można aktywować za pomocą dowolnego klienta COM. Jeżeli zestaw będzie aktywowany tylko przez jedną aplikację, należy go umieścić w katalogu tej aplikacji.  
  
## <a name="examples"></a>Przykłady  
 Polecenie rejestruje wszystkie klasy publicznej zawarte w `myTest.dll`.  
  
```  
regasm myTest.dll  
```  
  
 Polecenie generuje plik `myTest.reg`, który zawiera wszystkie wpisy rejestru niezbędne. Polecenie to nie powoduje aktualizacji rejestru.  
  
```  
regasm myTest.dll /regfile:myTest.reg  
```  
  
 Polecenie rejestruje wszystkie klasy publicznej zawarte w `myTest.dll`i generuje oraz rejestruje biblioteki typów `myTest.tlb`, który zawiera definicje wszystkie typy publiczne zdefiniowane w `myTest.dll`.  
  
```  
regasm myTest.dll /tlb:myTest.tlb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Tlbexp.exe (Eksporter biblioteki typów)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)  
 [Tlbimp.exe (Importer biblioteki typów)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 [Rejestrowanie zestawów w modelu COM](../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

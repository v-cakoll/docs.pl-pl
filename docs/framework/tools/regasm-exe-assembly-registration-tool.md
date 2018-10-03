---
title: Regasm.exe (Narzędzie rejestracji zestawów)
ms.date: 03/30/2017
helpviewer_keywords:
- Assembly Registration tool
- assemblies [.NET Framework], registering
- Regasm.exe
- registering assemblies
ms.assetid: e190e342-36ef-4651-a0b4-0e8c2c0281cb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30b13c75907ad0bc4d6dbce6a3ecd07f1fbede11
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030392"
---
# <a name="regasmexe-assembly-registration-tool"></a>Regasm.exe (Narzędzie rejestracji zestawów)

Narzędzie do rejestracji zestawów czyta metadane w zestawie i dodaje niezbędne wpisy do rejestru, co umożliwia klientom COM przejrzyste tworzenie klas .NET Framework. Po zarejestrowaniu klasy dowolny klient COM może jej używać tak, jakby była klasą modelu COM. Klasa jest rejestrowana tylko raz, kiedy zestaw jest instalowany. Nie można utworzyć wystąpień klas w zestawie z COM, dopóki nie zostaną one faktycznie zarejestrowane.

Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio. Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```
regasm assemblyFile [options]
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*AssemblyFile*|Zestaw do rejestracji w modelu COM.|

|Opcja|Opis|
|------------|-----------------|
|**/ codebase**|Tworzy wpis Codebase w rejestrze. Wpis Codebase określa ścieżkę pliku dla zestawu, który nie jest zainstalowany w globalnej pamięci podręcznej zestawów. Nie należy określać tej opcji, jeśli później instalowany będzie zestaw, który jest rejestrowany w globalnej pamięci podręcznej zestawów. *AssemblyFile* argument, określ **/ codebase** opcja musi być [zestawu z silną nazwą](../../../docs/framework/app-domains/strong-named-assemblies.md).|
|**/ zarejestrowane**|Określa, że narzędzie będzie odnosić się tylko do bibliotek typów, które zostały już zarejestrowane.|
|**/asmpath:Directory**|Określa katalog zawierający odwołania do zestawów. Może być używany z **/regfile razem** opcji.|
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|
|**/ regfile razem** [**:** *regFile*]|Generuje określony plik reg dla zestawu zawierający potrzebne wpisy rejestru. Zaznaczenie tej opcji nie powoduje zmiany rejestru. Nie można użyć tej opcji z **/u** lub **/TLB** opcje.|
|**/ silent** lub **/s**|Pomija wyświetlanie komunikatów o sukcesie.|
|**/ TLB** [**:** *typeLibFile*]|Generuje bibliotekę typów z określonego zestawu zawierającego definicje dostępnych typów zdefiniowanych w zestawie.|
|**/ unregister** lub **/u**|Wyrejestrowuje utworzone klasy znalezione w *assemblyFile*. Pominięcie tej opcji powoduje, że Regasm.exe rejestruje utworzone klasy w zestawie.|
|**/verbose**|Określa tryb pełnej informacji; Wyświetla listę wszelkich zestawów, dla których Biblioteka typów musi zostać wygenerowane, gdy określony za pomocą występujących w odwołaniu **/TLB** opcji.|
|**/?** lub   **/help**|Wyświetla składnię polecenia i opcje narzędzia.|

> [!NOTE]
> W opcjach wiersza polecenia programu Regasm.exe nie jest rozróżniana wielkość liter. Wystarczy podać część nazwy opcji umożliwiającą jej jednoznaczną identyfikację. Na przykład **/n** jest odpowiednikiem **/nologo** i **t:** *outfile.tlb* jest odpowiednikiem **/TLB:**  *outfile.tlb*.

## <a name="remarks"></a>Uwagi

Możesz użyć **/regfile razem** opcję, aby wygenerować plik reg, który zawiera wpisy rejestru zamiast wprowadzania zmian bezpośrednio w rejestrze. Można zaktualizować rejestr na komputerze przez zaimportowanie pliku reg za pomocą narzędzia Edytora rejestru (Regedit.exe). Należy zauważyć, że plik reg nie zawiera żadnych aktualizacji rejestru, które mogą być wykonane przez funkcje rejestru zdefiniowane przez użytkownika.  Należy pamiętać, że **/regfile razem** opcji emituje tylko wpisy rejestru dla klas zarządzanych.  Opcja ta nie emituje wpisów dla `TypeLibID`s lub `InterfaceID`s.

Po określeniu **/TLB** opcji, Regasm.exe generuje i rejestruje bibliotekę typów, zawierająca opis typów znalezionych w zestawie. Regasm.exe umieszcza wygenerowane biblioteki typów w bieżącym katalogu roboczym lub katalogu określonym dla pliku wyjściowego. Generowanie biblioteki typów dla zestawu, który odwołuje się do innych zestawów może spowodować, że zostanie wygenerowanych kilka bibliotek typów na raz. Aby zapewnić informacje o typie do narzędzi programistycznych, takich jak Visual Studio, można użyć biblioteki typów. Nie należy używać **/TLB** opcję, jeśli rejestrowany zestaw został wyprodukowany przez Importer biblioteki typów ([Tlbimp.exe](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)). Nie można wyeksportować biblioteki typów z zestawu, który został zaimportowany z biblioteki typów. Za pomocą **/TLB** opcja ma ten sam efekt jak użycie eksportera biblioteki typów ([Tlbexp.exe](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)) i Regasm.exe, z wyjątkiem, że Tlbexp.exe nie rejestruje biblioteki typów generuje.  Jeśli używasz **/TLB** możliwość zarejestrowania biblioteki typów, możesz użyć **/TLB** z opcją **/ unregister** do niezarejestrowanej biblioteki typów. Użycie obu tych opcji razem wyrejestruje bibliotekę typów i wpisy interfejsu, co może znacznie oczyścić rejestr.

Po zarejestrowaniu zestawu do użycia przez model COM, Regasm.exe dodaje wpisy do rejestru komputera lokalnego. Dokładniej, tworzy zależne od wersji klucze rejestru, które umożliwiają równoległe uruchomienie na komputerze wielu wersji tego samego zestawu. Gdy zestaw jest rejestrowany po raz pierwszy, tworzony jest jeden klucz najwyższego poziomu dla zestawu i unikatowy podklucz dla określonej wersji. Za każdym razem, gdy rejestrowana jest nowa wersja zestawu, Regasm.exe tworzy podklucz dla nowej wersji.

Na przykład rozważmy scenariusz, w którym rejestrujemy składnik zarządzany myComp.dll w wersji 1.0.0.0 do użycia przez model COM. Później można zarejestrować myComp.dll w wersji 2.0.0.0. Należy określić, że wszystkie aplikacje klienckie modelu COM na komputerze używają myComp.dll w wersji 2.0.0.0 i użytkownik decyduje się wyrejestrować myComponent.dll w wersji 1.0.0.0. Schemat rejestru umożliwia wyrejestrowanie myComp.dll w wersji 1.0.0.0, ponieważ jest usuwany tylko podklucz wersji 1.0.0.0.

Po zarejestrowaniu zestawu przy użyciu Regasm.exe można zainstalować go w [globalnej pamięci podręcznej](../../../docs/framework/app-domains/gac.md) , dzięki czemu może być aktywowany z dowolnego klienta com. Jeżeli zestaw będzie aktywowany tylko przez jedną aplikację, należy go umieścić w katalogu tej aplikacji.

## <a name="examples"></a>Przykłady

Następujące polecenie rejestruje wszystkie klasy publiczne zawarte w `myTest.dll`.

```
regasm myTest.dll
```

Następujące polecenie generuje plik `myTest.reg`, który zawiera wszystkie niezbędne wpisy rejestru. Polecenie to nie powoduje aktualizacji rejestru.

```
regasm myTest.dll /regfile:myTest.reg
```

Następujące polecenie rejestruje wszystkie klasy publiczne zawarte w `myTest.dll`, a także generuje i rejestruje bibliotekę typów `myTest.tlb`, która zawiera definicje typów publicznych określonych w `myTest.dll`.

```
regasm myTest.dll /tlb:myTest.tlb
```

## <a name="see-also"></a>Zobacz także

- [Narzędzia](../../../docs/framework/tools/index.md)
- [Tlbexp.exe (eksporter biblioteki typów)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)
- [Tlbimp.exe (importer biblioteki typów)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)
- [Rejestrowanie zestawów do użycia z modelem COM](../../../docs/framework/interop/registering-assemblies-with-com.md)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

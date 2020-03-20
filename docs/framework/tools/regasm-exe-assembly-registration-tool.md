---
title: Regasm.exe (Narzędzie rejestracji zestawów)
ms.date: 03/30/2017
helpviewer_keywords:
- Assembly Registration tool
- assemblies [.NET Framework], registering
- Regasm.exe
- registering assemblies
ms.assetid: e190e342-36ef-4651-a0b4-0e8c2c0281cb
ms.openlocfilehash: 45b4c6c08d3afb948444a8c97dc32bd41f2615ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73104949"
---
# <a name="regasmexe-assembly-registration-tool"></a>Regasm.exe (Narzędzie rejestracji zestawów)

Narzędzie do rejestracji zestawów czyta metadane w zestawie i dodaje niezbędne wpisy do rejestru, co umożliwia klientom COM przejrzyste tworzenie klas .NET Framework. Po zarejestrowaniu klasy dowolny klient COM może jej używać tak, jakby była klasą modelu COM. Klasa jest rejestrowana tylko raz, kiedy zestaw jest instalowany. Nie można utworzyć wystąpień klas w zestawie z COM, dopóki nie zostaną one faktycznie zarejestrowane.

Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```console
regasm assemblyFile [options]
```

## <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Assemblyfile*|Zestaw do rejestracji w modelu COM.|

|Opcja|Opis|
|------------|-----------------|
|**/codebase**|Tworzy wpis Codebase w rejestrze. Wpis Codebase określa ścieżkę pliku dla zestawu, który nie jest zainstalowany w globalnej pamięci podręcznej zestawów. Nie należy określać tej opcji, jeśli później instalowany będzie zestaw, który jest rejestrowany w globalnej pamięci podręcznej zestawów. Argument *assemblyFile,* który określisz za pomocą opcji **/codebase,** musi być [zestawem o silnej nazwie.](../../standard/assembly/strong-named.md)|
|**/zarejestrowany**|Określa, że narzędzie będzie odnosić się tylko do bibliotek typów, które zostały już zarejestrowane.|
|**/asmpath:katalog**|Określa katalog zawierający odwołania do zestawów. Musi być używany z opcją **/regfile.**|
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|
|**/regfile** [**:** *regFile*]|Generuje określony plik reg dla zestawu zawierający potrzebne wpisy rejestru. Zaznaczenie tej opcji nie powoduje zmiany rejestru. Nie można użyć tej opcji z opcjami **/u** lub **/tlb.**|
|**/silent** lub **/s**|Pomija wyświetlanie komunikatów o sukcesie.|
|**/tlb** [**:** *typeLibFile*]|Generuje bibliotekę typów z określonego zestawu zawierającego definicje dostępnych typów zdefiniowanych w zestawie.|
|**/wyrejestrować** lub **/u**|Wyrejestrowaj klasy możliwe do *utworzenia*znalezione w pliku zestawu . Pominięcie tej opcji powoduje, że Regasm.exe rejestruje utworzone klasy w zestawie.|
|**/pełne**|Określa tryb pełne; wyświetla listę wszelkich zestawów, do których istnieje odwołanie, dla których musi zostać wygenerowana biblioteka typów, po określeniu za pomocą opcji **/tlb.**|
|**/?** lub **/help**|Wyświetla składnię polecenia i opcje narzędzia.|

> [!NOTE]
> W opcjach wiersza polecenia programu Regasm.exe nie jest rozróżniana wielkość liter. Wystarczy podać część nazwy opcji umożliwiającą jej jednoznaczną identyfikację. Na przykład **/n** jest odpowiednikiem **/nologo** i **/t:** *outfile.tlb* jest odpowiednikiem **/tlb:** *outfile.tlb*.

## <a name="remarks"></a>Uwagi

Za pomocą opcji **/regfile** można wygenerować plik reg zawierający wpisy rejestru zamiast wszudowywszuchek do rejestru. Można zaktualizować rejestr na komputerze przez zaimportowanie pliku reg za pomocą narzędzia Edytora rejestru (Regedit.exe). Należy zauważyć, że plik reg nie zawiera żadnych aktualizacji rejestru, które mogą być wykonane przez funkcje rejestru zdefiniowane przez użytkownika.  Należy zauważyć, że opcja **/regfile** emituje tylko wpisy rejestru dla klas zarządzanych.  Ta opcja nie emituje `TypeLibID`wpisów dla s lub `InterfaceID`s.

Po określeniu opcji **/tlb** program Regasm.exe generuje i rejestruje bibliotekę typów opisującą typy znalezione w zestawie. Regasm.exe umieszcza wygenerowane biblioteki typów w bieżącym katalogu roboczym lub katalogu określonym dla pliku wyjściowego. Generowanie biblioteki typów dla zestawu, który odwołuje się do innych zestawów może spowodować, że zostanie wygenerowanych kilka bibliotek typów na raz. Biblioteka typów służy do dostarczania informacji o typie do narzędzi programistycznych, takich jak Visual Studio. Nie należy używać opcji **/tlb,** jeśli zarejestrowany zestaw został wyprodukowany przez importera biblioteki typów ([Tlbimp.exe](tlbimp-exe-type-library-importer.md)). Nie można wyeksportować biblioteki typów z zestawu, który został zaimportowany z biblioteki typów. Użycie opcji **/tlb** ma taki sam efekt jak przy użyciu programu Type Library Exporter ([Tlbexp.exe](tlbexp-exe-type-library-exporter.md)) i Regasm.exe, z wyjątkiem tego, że program Tlbexp.exe nie rejestruje biblioteki typów, którą tworzy.  Jeśli do zarejestrowania biblioteki typów jest używana opcja **/tlb,** można użyć opcji **/tlb** z opcją **/wyrejestruaj** do wyrejestrowania biblioteki typów. Użycie obu tych opcji razem wyrejestruje bibliotekę typów i wpisy interfejsu, co może znacznie oczyścić rejestr.

Po zarejestrowaniu zestawu do użycia przez model COM, Regasm.exe dodaje wpisy do rejestru komputera lokalnego. Dokładniej, tworzy zależne od wersji klucze rejestru, które umożliwiają równoległe uruchomienie na komputerze wielu wersji tego samego zestawu. Gdy zestaw jest rejestrowany po raz pierwszy, tworzony jest jeden klucz najwyższego poziomu dla zestawu i unikatowy podklucz dla określonej wersji. Za każdym razem, gdy rejestrowana jest nowa wersja zestawu, Regasm.exe tworzy podklucz dla nowej wersji.

Na przykład rozważmy scenariusz, w którym rejestrujemy składnik zarządzany myComp.dll w wersji 1.0.0.0 do użycia przez model COM. Później można zarejestrować myComp.dll w wersji 2.0.0.0. Należy określić, że wszystkie aplikacje klienckie modelu COM na komputerze używają myComp.dll w wersji 2.0.0.0 i użytkownik decyduje się wyrejestrować myComponent.dll w wersji 1.0.0.0. Schemat rejestru umożliwia wyrejestrowanie myComp.dll w wersji 1.0.0.0, ponieważ jest usuwany tylko podklucz wersji 1.0.0.0.

Po zarejestrowaniu zestawu przy użyciu programu Regasm.exe można go zainstalować w [globalnej pamięci podręcznej zestawów,](../app-domains/gac.md) aby można było go aktywować z dowolnego klienta COM. Jeżeli zestaw będzie aktywowany tylko przez jedną aplikację, należy go umieścić w katalogu tej aplikacji.

## <a name="examples"></a>Przykłady

Następujące polecenie rejestruje wszystkie klasy publiczne `myTest.dll`zawarte w .

```console
regasm myTest.dll
```

Następujące polecenie generuje plik `myTest.reg`, który zawiera wszystkie niezbędne wpisy rejestru. Polecenie to nie powoduje aktualizacji rejestru.

```console
regasm myTest.dll /regfile:myTest.reg
```

Następujące polecenie rejestruje wszystkie klasy publiczne `myTest.dll`zawarte w , i generuje `myTest.tlb`i rejestruje bibliotekę typów , `myTest.dll`która zawiera definicje wszystkich typów publicznych zdefiniowanych w .

```console
regasm myTest.dll /tlb:myTest.tlb
```

## <a name="see-also"></a>Zobacz też

- [narzędzia](index.md)
- [Tlbexp.exe (Eksporter biblioteki typów)](tlbexp-exe-type-library-exporter.md)
- [Tlbimp.exe (importer biblioteki typów)](tlbimp-exe-type-library-importer.md)
- [Rejestrowanie zestawów do użycia z modelem COM](../interop/registering-assemblies-with-com.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)

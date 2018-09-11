---
title: -target (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e3f691da48db863edd20bc6881785940a5451ef
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44265237"
---
# <a name="-target-visual-basic"></a>-target (Visual Basic)
Określa format danych wyjściowych kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono efekt `-target` opcji.  
  
|**Option**|**Behavior**|  
|----------------|------------------|  
|`-target:exe`|Powoduje, że kompilator, aby utworzyć aplikację konsoli pliku wykonywalnego.<br /><br /> Jest to opcja domyślna, gdy nie `-target` określono opcję. Plik wykonywalny jest tworzony z rozszerzeniem .exe.<br /><br /> Chyba że określono inaczej, za pomocą `/out` opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera `Sub Main` procedury.<br /><br /> Tylko jeden `Sub Main` procedura jest wymagana w plikach kodu źródłowego, które są kompilowane do pliku .exe. Użyj `-main` opcję kompilatora, aby określić, która klasa zawiera `Sub Main` procedury.|  
|`-target:library`|Powoduje, że kompilator do tworzenia biblioteki dołączanej (dynamicznie DLL).<br /><br /> Plik biblioteki dołączanej jest tworzony z rozszerzeniem dll.<br /><br /> Chyba że określono inaczej, za pomocą `-out` opcji Nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego.<br /><br /> Podczas tworzenia biblioteki DLL, `Sub Main` procedura nie jest wymagana.|  
|`-target:module`|Powoduje, że kompilator do generowania modułu, który można dodać do zestawu.<br /><br /> Plik wyjściowy został utworzony z rozszerzeniem .netmodule.<br /><br /> .NET CLR nie można załadować pliku, który nie ma zestawu. Jednak można zastosować takiego pliku do manifestu zestawu zestawu przy użyciu `-reference`.<br /><br /> Gdy kod w jednym module odwołuje się do wewnętrznych typów w innym module, oba moduły musi być włączona do manifestu zestawu przy użyciu `-reference`.<br /><br /> [- Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) opcja importuje metadane z modułu.|  
|`-target:winexe`|Powoduje, że kompilator do utworzenia pliku wykonywalnego aplikacji systemu Windows.<br /><br /> Plik wykonywalny jest tworzony z rozszerzeniem .exe. Windows aplikacji to taki, który zapewnia interfejs użytkownika z poziomu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteki klas lub za pomocą interfejsów API systemu Win32.<br /><br /> Chyba że określono inaczej, za pomocą `-out` opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera `Sub Main` procedury.<br /><br /> Tylko jeden `Sub Main` procedura jest wymagana w plikach kodu źródłowego, które są kompilowane do pliku .exe. W przypadkach, gdy kod ma więcej niż jedną klasę, która ma `Sub Main` procedurę, użyj `-main` opcję kompilatora, aby określić, która klasa zawiera `Sub Main` procedury|  
|`-target:appcontainerexe`|Powoduje, że kompilator tworzenia pliku wykonywalnego aplikacji opartych na Windows, która musi być uruchamiany w kontenerze aplikacji. To ustawienie jest przeznaczone do użytku z [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikacji.<br /><br /> **Appcontainerexe** ustawienie ustawia bit w polu właściwości [przenośny plik wykonywalny](/windows/desktop/Debug/pe-format) pliku. Ten bit wskazuje, że aplikacja musi zostać uruchomiony w kontenerze aplikacji. Jeśli ten bit jest ustawiony, wystąpi błąd, jeśli `CreateProcess` metoda próbuje uruchomić aplikację poza kontenerem aplikacji. Oprócz tego bit ustawienie **-target: appcontainerexe** jest odpowiednikiem **-target: winexe**.<br /><br /> Plik wykonywalny jest tworzony z rozszerzeniem .exe.<br /><br /> Chyba że określono inaczej używając `-out` opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera `Sub Main` procedury.<br /><br /> Tylko jeden `Sub Main` procedura jest wymagana w plikach kodu źródłowego, które są kompilowane do pliku .exe. Jeśli kod zawiera więcej niż jedną klasę, która ma `Sub Main` procedurę, użyj `-main` opcję kompilatora, aby określić, która klasa zawiera `Sub Main` procedury|  
|`-target:winmdobj`|Powoduje, że kompilator, aby utworzyć plik pośredni, który można przekonwertować na plik binarny (.winmd) środowiska wykonawczego Windows. Plik .winmd mogą być używane przez programy JavaScript i C++, oprócz programów zarządzanych języka.<br /><br /> Pośredni plik jest tworzony z rozszerzeniem .winmdobj.<br /><br /> Chyba że określono inaczej używając `-out` opcji Nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego. A `Sub Main` procedura nie jest wymagana.<br /><br /> Plik .winmdobj jest przeznaczony do użycia jako dane wejściowe dla <xref:Microsoft.Build.Tasks.WinMDExp> wyeksportować narzędzie w celu utworzenia pliku metadanych (WinMD) Windows. Plik WinMD ma rozszerzenie winmd i zawiera kod z oryginalnej biblioteki i definicje WinMD przez język JavaScript, C++ i użyj środowiska wykonawczego Windows.|  
  
 Jeśli nie określisz `-target:module`, `-target` powoduje, że [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] manifestu zestawu, które mają zostać dodane do pliku wyjściowego.  
  
 Każde wystąpienie Vbc.exe tworzy, co najwyżej jeden plik wyjściowy. Jeśli określisz opcję kompilatora takich jak `-out` lub `-target` więcej niż jeden raz, ostatni z nich procesów kompilatora zacznie obowiązywać. Informacje o wszystkich plików w kompilacji są dodawane do manifestu. Wszystkie pliki, z wyjątkiem tych utworzonych za pomocą wyjściowe `-target:module` zawierać metadane zestawu w manifeście. Użyj [Ildasm.exe (dezasembler IL)](../../../framework/tools/ildasm-exe-il-disassembler.md) wyświetlanie metadanych w pliku wyjściowym.  
  
 Krótkiej formy `-target` jest `-t`.  
  
### <a name="to-set--target-in-the-visual-studio-ide"></a>Aby ustawić - docelowy w środowisku IDE programu Visual Studio  
  
1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.   
  
2.  Kliknij przycisk **aplikacji** kartę.  
  
3.  Zmodyfikuj wartość w **typ aplikacji** pole.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `in.vb`, tworzenie `in.dll`:  
  
```console
vbc -target:library in.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)  
- [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
- [— Odwołanie (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
- [-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)  
- [Zestawy i globalna pamięć podręczna zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

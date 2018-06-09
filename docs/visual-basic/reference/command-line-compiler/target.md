---
title: -docelowego (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4097d82772c24bb0416bcb3f6d48bd1c7f101b95
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231440"
---
# <a name="-target-visual-basic"></a>-docelowego (Visual Basic)
Określa format danych wyjściowych kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono wpływ `-target` opcji.  
  
|**Option**|**Behavior**|  
|----------------|------------------|  
|`-target:exe`|Umożliwia kompilatorowi tworzenia aplikacji konsoli pliku wykonywalnego.<br /><br /> To jest opcją domyślną, gdy nie `-target` określono opcję. Plik wykonywalny jest tworzony z rozszerzeniem .exe.<br /><br /> Jeżeli nie określono inaczej z `/out` opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera `Sub Main` procedury.<br /><br /> Tylko jeden `Sub Main` procedura jest wymagana w plikach kodu źródłowego, które są łączone w pliku .exe. Użyj `-main` opcję kompilatora, aby określić, która klasa zawiera `Sub Main` procedury.|  
|`-target:library`|Powoduje, że kompilator, aby utworzyć biblioteki dołączanej (dynamicznie DLL).<br /><br /> Plik biblioteki dołączanej jest tworzony z rozszerzeniem dll.<br /><br /> Jeżeli nie określono inaczej z `-out` opcji Nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego.<br /><br /> Podczas tworzenia biblioteki DLL, `Sub Main` procedura nie jest wymagana.|  
|`-target:module`|Umożliwia kompilatorowi Generowanie moduł, który można dodać do zestawu.<br /><br /> Plik wyjściowy jest tworzony z rozszerzeniem modułu .netmodule.<br /><br /> NET common language runtime nie może załadować pliku, który nie ma zestawu. Jednak można zastosować takiego pliku w manifeście zestawu zestawu przy użyciu `-reference`.<br /><br /> Gdy kod w jednym module odwołuje się do wewnętrznej typów w innym module, zarówno modułów musi być włączona do manifestu zestawu przy użyciu `-reference`.<br /><br /> [- Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) opcja importuje metadane z modułu.|  
|`-target:winexe`|Umożliwia kompilatorowi tworzenia pliku wykonywalnego aplikacji opartych na systemie Windows.<br /><br /> Plik wykonywalny jest tworzony z rozszerzeniem .exe. Udostępnia interfejs użytkownika z dowolnej aplikacji systemu Windows, jest [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteki klas lub za pomocą interfejsów API systemu Win32.<br /><br /> Jeżeli nie określono inaczej z `-out` opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera `Sub Main` procedury.<br /><br /> Tylko jeden `Sub Main` procedura jest wymagana w plikach kodu źródłowego, które są łączone w pliku .exe. W przypadkach, gdy kod ma więcej niż jedną klasę, która ma `Sub Main` procedury, użyj `-main` opcję kompilatora, aby określić, która klasa zawiera `Sub Main` procedury|  
|`-target:appcontainerexe`|Powoduje, że kompilator do utworzenia pliku wykonywalnego aplikacji opartych na systemie Windows, która musi zostać uruchomiony w kontenerze aplikacji. To ustawienie jest przeznaczone do użycia dla [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikacji.<br /><br /> **Appcontainerexe** ustawienie ustawia bit w polu właściwości [przenośny plik wykonywalny](https://msdn.microsoft.com/library/windows/desktop/ms680547(v=vs.85).aspx?id=19509) pliku. Ten bit wskazuje, że aplikacja musi zostać uruchomiony w kontenerze aplikacji. Gdy ten bit jest ustawiona, jeśli wystąpi błąd `CreateProcess` metoda próbuje uruchomić aplikację poza kontenerem aplikacji. Jako uzupełnienie to bit ustawienie **-docelowych: appcontainerexe** jest odpowiednikiem **-docelowych: winexe**.<br /><br /> Plik wykonywalny jest tworzony z rozszerzeniem .exe.<br /><br /> O ile nie określono inaczej przy użyciu `-out` opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera `Sub Main` procedury.<br /><br /> Tylko jeden `Sub Main` procedura jest wymagana w plikach kodu źródłowego, które są łączone w pliku .exe. Jeśli kod zawiera więcej niż jedną klasę, która ma `Sub Main` procedury, użyj `-main` opcję kompilatora, aby określić, która klasa zawiera `Sub Main` procedury|  
|`-target:winmdobj`|Powoduje, że kompilator, aby utworzyć plik pośredni, który można przekonwertować na plik binarny (.winmd) środowiska wykonawczego systemu Windows. Plik winmd mogą być używane przez programy JavaScript i C++, oprócz programów zarządzanych języka.<br /><br /> Pośredni plik jest tworzony z rozszerzeniem .winmdobj.<br /><br /> Jeśli nie określono inaczej przy użyciu `-out` opcji Nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego. A `Sub Main` procedura nie jest wymagane.<br /><br /> Plik .winmdobj jest przeznaczony do użycia jako dane wejściowe dla <xref:Microsoft.Build.Tasks.WinMDExp> wyeksportować narzędzie w celu utworzenia pliku metadanych (WinMD) systemu Windows. Plik WinMD ma rozszerzenie winmd i zawiera kod z oryginalnej biblioteki i definicje WinMD, że JavaScript, C++ i użyj środowiska wykonawczego systemu Windows.|  
  
 Jeśli nie podasz `-target:module`, `-target` powoduje, że [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] manifest zestawu, które mają zostać dodane do pliku wyjściowego.  
  
 Każde wystąpienie Vbc.exe powoduje, co najwyżej jeden plik wyjściowy. Jeśli określono opcję kompilatora takich jak `-out` lub `-target` więcej niż jeden raz, ostatnią procesów kompilatora zacznie obowiązywać. Informacje o wszystkich plików w kompilacji są dodawane do manifestu. Wszystkie pliki z wyjątkiem tych, utworzone za pomocą wyjściowe `-target:module` zawierać metadane zestawu w manifeście. Użyj [Ildasm.exe (dezasembler IL)](https://msdn.microsoft.com/library/f7dy01k1) Aby wyświetlić metadane w pliku wyjściowym.  
  
 Krótka forma z `-target` jest `-t`.  
  
### <a name="to-set--target-in-the-visual-studio-ide"></a>Aby ustawić — obiektów docelowych w środowisku IDE programu Visual Studio  
  
1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.   
  
2.  Kliknij przycisk **aplikacji** kartę.  
  
3.  Zmodyfikuj wartość w **typu aplikacji** pole.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `in.vb`, tworzenie `in.dll`:  
  
```console
vbc -target:library in.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [-odwołania (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)  
 [Zestawy i globalna pamięć podręczna zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

---
title: '-target: winmdobj (C# opcje kompilatora)'
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 85ae9a3f5e9b038c0c56935ec5af2b9b09d19f20
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204493"
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-target: winmdobj (C# opcje kompilatora)
W przypadku użycia opcji kompilatora **-target: winmdobj** kompilator tworzy plik pośredni. winmdobj, który można przekonwertować na środowisko wykonawcze systemu Windows plik binarny (. winmd). Plik. winmd może być następnie używany przez JavaScript i C++ programy, oprócz programów języka zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>Uwagi  
 Ustawienie **winmdobj** sygnalizuje kompilatorowi, że wymagany jest moduł pośredni. W odpowiedzi program Visual Studio kompiluje bibliotekę C# klas jako plik. winmdobj. Plik. winmdobj można następnie uzyskać za pomocą narzędzia eksportu <xref:Microsoft.Build.Tasks.WinMDExp>, aby utworzyć plik metadanych systemu Windows (WinMD). Plik. winmd zawiera zarówno kod z oryginalnej biblioteki, jak i metadane WinMD, które są używane przez skrypty JavaScript lub C++ środowisko wykonawcze systemu Windows.  
  
 Dane wyjściowe pliku, który jest kompilowany przy użyciu opcji **-target: winmdobj** kompilatora, jest przeznaczony do użycia tylko jako dane wejściowe dla narzędzia eksportu WimMDExp; sam plik. winmdobj nie jest bezpośrednio przywoływany.  
  
 O ile nie zostanie użyta opcja [-out](./out-compiler-option.md) , nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego. Metoda [Main](../../programming-guide/main-and-command-args/index.md) nie jest wymagana.  
  
 W przypadku określenia opcji-target: winmdobj w wierszu polecenia wszystkie pliki do momentu, w którym zostanie użyta opcja modułu "Następny **-out** " lub ["target: module"](./target-module-compiler-option.md) , są używane do tworzenia programu systemu Windows.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio IDE dla aplikacji magazynu systemu Windows  
  
1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Właściwości**.  
  
2. Wybierz kartę **aplikacja** .  
  
3. Na liście **Typ danych wyjściowych** wybierz pozycję **plik WinMD**.  
  
     Opcja **plik WinMD** jest dostępna tylko dla szablonów aplikacji ze sklepu Windows 8. x.  
  
 Aby uzyskać informacje o tym, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższe polecenie kompiluje `filename.cs` do pliku pośredniego. winmdobj.  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [-Target (C# opcje kompilatora)](./target-compiler-option.md)
- [Opcje kompilatora C#](./index.md)

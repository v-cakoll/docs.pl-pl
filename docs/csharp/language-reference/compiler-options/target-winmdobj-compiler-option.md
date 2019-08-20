---
title: '-target: winmdobj (C# opcje kompilatora)'
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: fe1332f9ed6de9c50c2509e29f22ed7c0e57ade9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606359"
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-target: winmdobj (C# opcje kompilatora)
W przypadku użycia opcji kompilatora **-target: winmdobj** kompilator tworzy plik pośredni. winmdobj, który można przekonwertować na środowisko wykonawcze systemu Windows plik binarny (. winmd). Plik. winmd może być następnie używany przez JavaScript i C++ programy, oprócz programów języka zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>Uwagi  
 Ustawienie **winmdobj** sygnalizuje kompilatorowi, że wymagany jest moduł pośredni. W odpowiedzi program Visual Studio kompiluje bibliotekę C# klas jako plik. winmdobj. Plik. winmdobj można następnie uzyskać za pomocą <xref:Microsoft.Build.Tasks.WinMDExp> narzędzia eksportu w celu utworzenia pliku metadanych systemu Windows (WinMD). Plik. winmd zawiera zarówno kod z oryginalnej biblioteki, jak i metadane WinMD, które są używane przez skrypty JavaScript lub C++ środowisko wykonawcze systemu Windows.  
  
 Dane wyjściowe pliku, który jest kompilowany przy użyciu opcji **-target: winmdobj** kompilatora, jest przeznaczony do użycia tylko jako dane wejściowe dla narzędzia eksportu WimMDExp; sam plik. winmdobj nie jest bezpośrednio przywoływany.  
  
 O ile nie zostanie użyta opcja [-out](./out-compiler-option.md) , nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego. Metoda [Main](../../programming-guide/main-and-command-args/index.md) nie jest wymagana.  
  
 W przypadku określenia opcji-target: winmdobj w wierszu polecenia wszystkie pliki do momentu, w którym zostanie użyta opcja modułu "Następny **-out** " lub ["target: module"](./target-module-compiler-option.md) , są używane do tworzenia programu systemu Windows.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio IDE dla aplikacji magazynu systemu Windows  
  
1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Właściwości**.  
  
2. Wybierz kartę **aplikacja** .  
  
3. Na liście **Typ danych wyjściowych** wybierz pozycję **plik WinMD**.  
  
     Opcja **plik WinMD** jest dostępna tylko dla [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] szablonów aplikacji.  
  
 Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.ProjectProperties3.OutputType%2A>tę opcję kompilatora, zobacz.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie kompiluje `filename.cs` do pośredniego pliku. winmdobj.  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [-Target (C# opcje kompilatora)](./target-compiler-option.md)
- [Opcje kompilatora C#](./index.md)

---
title: -target:winmdobj (Opcje kompilatora C#)
ms.date: 07/20/2015
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
ms.openlocfilehash: 85ae9a3f5e9b038c0c56935ec5af2b9b09d19f20
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204493"
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-target:winmdobj (Opcje kompilatora C#)
Jeśli używasz opcji **kompilatora -target:winmdobj,** kompilator tworzy pośredni plik .winmdobj, który można przekonwertować na plik binarny środowiska uruchomieniowego systemu Windows (winmd). Plik .winmd może być następnie używany przez programy JavaScript i C++, oprócz zarządzanych programów językowych.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>Uwagi  
 Ustawienie **winmdobj** sygnalizuje kompilator, że wymagany jest moduł pośredni. W odpowiedzi Visual Studio kompiluje biblioteki klas C# jako plik .winmdobj. Plik .winmdobj może być następnie <xref:Microsoft.Build.Tasks.WinMDExp> podawany za pomocą narzędzia eksportu w celu wygenerowania pliku metadanych systemu Windows (winmd). Plik .winmd zawiera zarówno kod z oryginalnej biblioteki, jak i metadane WinMD używane przez JavaScript lub C++ oraz przez środowisko uruchomieniowe systemu Windows.  
  
 Dane wyjściowe pliku, który jest kompilowany przy użyciu opcji kompilatora **-target:winmdobj** jest przeznaczony do użycia tylko jako dane wejściowe dla narzędzia eksportu WimMDExp; plik .winmdobj sam nie odwołuje się bezpośrednio.  
  
 Jeśli nie użyjesz opcji [-out,](./out-compiler-option.md) nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego. [Metoda główna](../../programming-guide/main-and-command-args/index.md) nie jest wymagana.  
  
 Jeśli określisz opcję -target:winmdobj w wierszu polecenia, wszystkie pliki do następnego **-out** lub [-target:module](./target-module-compiler-option.md) opcja są używane do tworzenia programu Windows.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio IDE dla aplikacji magazynu systemu Windows  
  
1. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu, a następnie wybierz pozycję **Właściwości**.  
  
2. Wybierz **kartę Aplikacja.**  
  
3. Na liście **Typ wyjściowy** wybierz pozycję **Plik WinMD**.  
  
     Opcja **Plik WinMD** jest dostępna tylko dla szablonów aplikacji ze Sklepu Windows 8.x.  
  
 Aby uzyskać informacje dotyczące programowego ustawiania tej <xref:VSLangProj80.ProjectProperties3.OutputType%2A>opcji kompilatora, zobacz .  
  
## <a name="example"></a>Przykład  
 Następujące polecenie kompiluje `filename.cs` się do pośredniego pliku .winmdobj.  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [-target (Opcje kompilatora C#)](./target-compiler-option.md)
- [Opcje kompilatora Języka C#](./index.md)

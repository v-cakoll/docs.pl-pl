---
title: '-docelowych: winmdobj (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1819a045-659d-498a-9457-c466e902986f
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 444fcd69db327ea9d9c3dc739b42520bb9472c4d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-targetwinmdobj-c-compiler-options"></a>-docelowych: winmdobj (opcje kompilatora C#)
Jeśli używasz **-docelowych: winmdobj** — opcja kompilatora, kompilator tworzy plik pośredni .winmdobj, który można przekonwertować na plik binarny (.winmd) środowiska wykonawczego systemu Windows. Plik winmd, następnie mogą być używane przez programy JavaScript i C++, oprócz programów zarządzanych języka.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:winmdobj  
```  
  
## <a name="remarks"></a>Uwagi  
 **Winmdobj** ustawienie sygnały kompilatora, że moduł pośredniego jest wymagana. Program Visual Studio kompiluje biblioteki klas C# jako plik .winmdobj. Plik .winmdobj można następnie przekazywani za pośrednictwem <xref:Microsoft.Build.Tasks.WinMDExp> wyeksportować narzędzie w celu utworzenia pliku metadanych (.winmd) systemu Windows. Plik winmd zawiera kod z oryginalnej biblioteki i metadanych WinMD, które jest używane przez JavaScript lub C++ i środowiska wykonawczego systemu Windows.  
  
 Dane wyjściowe pliku, który ma być kompilowana przy użyciu **-docelowych: winmdobj** — opcja kompilatora jest przeznaczony do użytku tylko jako dane wejściowe dla narzędzia eksportu WimMDExp; sam plik .winmdobj nie jest przywoływany bezpośrednio.  
  
 Jeśli nie używasz [— limit](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego. A [Main](../../../csharp/programming-guide/main-and-command-args/index.md) — metoda nie jest wymagane.  
  
 Jeśli określisz opcji - docelowych: winmdobj, w wierszu polecenia, wszystkie pliki do następnej **— limit** lub [— docelowych: moduł](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) opcji są używane do tworzenia programu systemu Windows.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-ide-for-a-windows-store-app"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio IDE dla aplikacji magazynu systemu Windows  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz **właściwości**.  
  
2.  Wybierz **aplikacji** kartę.  
  
3.  W **Output typu** wybierz **pliku WinMD**.  
  
     **Pliku WinMD** opcja jest dostępna tylko w przypadku [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] szablonów aplikacji.  
  
 Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie kompiluje `filename.cs` do pliku pośredniego .winmdobj.  
  
```console  
csc -target:winmdobj filename.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [-docelowego (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)

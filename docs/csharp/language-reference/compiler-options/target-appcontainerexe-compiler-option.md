---
title: '-target: appcontainerexe (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: b3819c0582c414e1f1e3b75ab5bfe517873a1eb3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311074"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-target: appcontainerexe (opcje kompilatora C#)
Jeśli używasz **-target: appcontainerexe** — opcja kompilatora, kompilator tworzy plik wykonywalny (.exe) Windows, który musi być uruchamiany w kontenerze aplikacji. Ta opcja jest równoznaczna z [-target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) , ale jest przeznaczona dla [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a>Uwagi  
 Aby wymagać uruchamiania aplikacji w pojemniku aplikacji, ta opcja ustawia bit w [przenośny plik wykonywalny](/windows/desktop/Debug/pe-format) (PE) pliku. Jeśli ten bit jest ustawiony, błąd występuje, gdy metoda funkcji CreateProcess próbuje uruchomić plik wykonywalny poza kontenerem aplikacji.  
  
 Chyba że używasz [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metody.  
  
 Po określeniu tej opcji w wierszu polecenia, wszystkie pliki, aż do następnej **-się** lub **-target** opcji są używane do tworzenia pliku wykonywalnego.  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>Aby ustawić tę opcję kompilatora w IDE  
  
1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.  
  
2. Na **aplikacji** na karcie **typ danych wyjściowych** wybierz **Windows Store App**.  
  
     Ta opcja jest dostępna tylko w przypadku [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] szablonów aplikacji.  
  
 Aby dowiedzieć się, jak programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie kompiluje `filename.cs` do Windows plik wykonywalny, który można uruchomić tylko w pojemniku aplikacji.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [-target (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [-target: winexe (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)
- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)

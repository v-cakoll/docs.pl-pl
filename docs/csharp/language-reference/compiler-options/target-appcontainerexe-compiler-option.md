---
title: '-target: appcontainerexe (C# opcje kompilatora)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 09ae01d95138b72a0012f294189d288fc71c74b2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606519"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-target: appcontainerexe (C# opcje kompilatora)
W przypadku użycia opcji kompilatora **-target: appcontainerexe** kompilator tworzy plik wykonywalny systemu Windows (exe), który musi być uruchamiany w kontenerze aplikacji. Ta opcja jest równoznaczna z parametrem [-target: winexe](./target-winexe-compiler-option.md) , [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] ale jest zaprojektowana dla aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a>Uwagi  
 Aby wymagać uruchamiania aplikacji w kontenerze aplikacji, ta opcja ustawia bit w przenośnym pliku [wykonywalnym](/windows/desktop/Debug/pe-format) (PE). Gdy ten bit jest ustawiony, występuje błąd, jeśli metoda CreateProcess podejmie próbę uruchomienia pliku wykonywalnego poza kontenerem aplikacji.  
  
 O ile nie zostanie użyta opcja [-out](./out-compiler-option.md) , nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera metodę [Main](../../programming-guide/main-and-command-args/index.md) .  
  
 Po określeniu tej opcji w wierszu polecenia wszystkie pliki do momentu użycia opcji dalej lub **-Target** są używane do tworzenia pliku wykonywalnego.  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>Aby ustawić tę opcję kompilatora w IDE  
  
1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Właściwości**.  
  
2. Na karcie **aplikacja** na liście **Typ danych wyjściowych** wybierz pozycję **aplikacja ze sklepu Windows**.  
  
     Ta opcja jest dostępna tylko dla [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] szablonów aplikacji.  
  
 Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.ProjectProperties3.OutputType%2A>tę opcję kompilatora, zobacz.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie kompiluje `filename.cs` do pliku wykonywalnego systemu Windows, który można uruchomić tylko w kontenerze aplikacji.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [-Target (C# opcje kompilatora)](./target-compiler-option.md)
- [-target: winexe (C# opcje kompilatora)](./target-winexe-compiler-option.md)
- [Opcje kompilatora C#](./index.md)

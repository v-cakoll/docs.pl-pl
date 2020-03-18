---
title: -target:appcontainerexe (Opcje kompilatora C#)
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 64661e72f9efe190606cadd93558678cb849e8cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74204524"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-target:appcontainerexe (Opcje kompilatora C#)
Jeśli używasz opcji **kompilatora -target:appcontainerexe,** kompilator tworzy plik wykonywalny systemu Windows (exe), który musi być uruchamiany w kontenerze aplikacji. Ta opcja jest odpowiednikiem [-target:winexe,](./target-winexe-compiler-option.md) ale jest przeznaczona dla aplikacji ze Sklepu Windows 8.x.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a>Uwagi  
 Aby wymagać uruchamiania aplikacji w kontenerze aplikacji, ta opcja ustawia nieco w pliku [Przenośny plik wykonywalny](/windows/desktop/Debug/pe-format) (PE). Gdy ten bit jest ustawiony, występuje błąd, jeśli CreateProcess metoda próbuje uruchomić plik wykonywalny poza kontenerem aplikacji.  
  
 Jeśli nie użyjesz opcji [-out,](./out-compiler-option.md) nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [Main](../../programming-guide/main-and-command-args/index.md) metody.  
  
 Po określeniu tej opcji w wierszu polecenia wszystkie pliki do następnego **-out** lub **-target** opcja są używane do tworzenia pliku wykonywalnego.  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>Aby ustawić tę opcję kompilatora w IDE  
  
1. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu, a następnie wybierz pozycję **Właściwości**.  
  
2. Na **karcie Aplikacja** na liście **Typ wyjściowy** wybierz pozycję Aplikacja **ze Sklepu Windows**.  
  
     Ta opcja jest dostępna tylko dla szablonów aplikacji ze Sklepu Windows 8.x.  
  
 Aby uzyskać informacje dotyczące programowego ustawiania tej <xref:VSLangProj80.ProjectProperties3.OutputType%2A>opcji kompilatora, zobacz .  
  
## <a name="example"></a>Przykład  
 Następujące polecenie kompiluje `filename.cs` się do pliku wykonywalnego systemu Windows, który można uruchomić tylko w kontenerze aplikacji.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [-target (Opcje kompilatora C#)](./target-compiler-option.md)
- [-target:winexe (Opcje kompilatora C#)](./target-winexe-compiler-option.md)
- [Opcje kompilatora Języka C#](./index.md)

---
title: '-docelowych: appcontainerexe (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9ab407f14483bbb5abaf3dc23b0cf204091b74ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="targetappcontainerexe-c-compiler-options"></a>/target:appcontainerexe (opcje kompilatora C#)
Jeśli używasz **/target: appcontainerexe** — opcja kompilatora, kompilator tworzy plik wykonywalny (.exe) systemu Windows, które muszą być uruchamiane w kontenerze aplikacji. Ta opcja jest równoważna [/target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) , ale jest przeznaczona dla [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/target:appcontainerexe  
```  
  
## <a name="remarks"></a>Uwagi  
 Aby wymagać aplikacji do uruchamiania w kontenerze aplikacji, ta opcja umożliwia ustawienie nieco [przenośny plik wykonywalny](http://go.microsoft.com/fwlink/p/?LinkId=236960) pliku (PE). Podczas tego bit jest ustawiony, jeśli metody CreateProcess podejmie próbę uruchomienia pliku wykonywalnego poza kontenerem aplikacji wystąpi błąd.  
  
 Jeśli nie używasz [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [Main](../../../csharp/programming-guide/main-and-command-args/index.md) — metoda.  
  
 Po określeniu tej opcji w wierszu polecenia, wszystkie pliki, aż do następnego **/out** lub **/target** opcji są używane do tworzenia pliku wykonywalnego.  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>Aby ustawić tę opcję kompilatora w IDE  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, a następnie wybierz **właściwości**.  
  
2.  Na **aplikacji** karcie **Output typu** wybierz **aplikacji ze Sklepu Windows**.  
  
     Ta opcja jest dostępna tylko w przypadku [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] szablonów aplikacji.  
  
 Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Przykład  
 Następujące polecenie kompiluje `filename.cs` do pliku wykonywalnego systemu Windows, która może działać tylko w kontenerze aplikacji.  
  
```console  
csc /target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [/ TARGET (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [/ target: winexe (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)

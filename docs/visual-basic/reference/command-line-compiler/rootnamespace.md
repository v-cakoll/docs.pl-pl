---
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: 4df4e74fc13c922f51f5b74c3c152bdea28b4431
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005211"
---
# <a name="-rootnamespace"></a>-rootnamespace
Określa przestrzeń nazw dla wszystkich deklaracji typu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`namespace`|Nazwa przestrzeni nazw, w której należy ująć wszystkie deklaracje typu dla bieżącego projektu.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używasz pliku wykonywalnego programu Visual Studio (devenv. exe) do kompilowania projektu utworzonego w zintegrowanym środowisku programistycznym programu Visual Studio, użyj `-rootnamespace`, aby określić wartość właściwości <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>. Zobacz [przełączniki wiersza polecenia devenv](/visualstudio/ide/reference/devenv-command-line-switches) , aby uzyskać więcej informacji.  
  
 Użyj Dezasembler MSIL (`Ildasm.exe`) środowiska uruchomieniowego języka wspólnego, aby wyświetlić nazwy przestrzeni nazw w pliku wyjściowym.  
  
|Aby ustawić-RootNamespace w zintegrowanym środowisku programistycznym programu Visual Studio|  
|---|  
|1. zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**. <br />2. Kliknij kartę **aplikacja** .<br />3. Zmodyfikuj wartość w polu **główna przestrzeń nazw** .|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i ujmuje wszystkie deklaracje typów w przestrzeni nazw `mynamespace`.  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Ildasm.exe (dezasembler IL)](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

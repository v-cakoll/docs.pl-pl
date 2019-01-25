---
title: -rootnamespace —
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: ff4b1729f1b9fb1d698b4b5b1e3711ce3d27b4db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655559"
---
# <a name="-rootnamespace"></a>-rootnamespace —
Określa obszar nazw dla wszystkich deklaracji typów.  
  
## <a name="syntax"></a>Składnia  
  
```  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`namespace`|Nazwa przestrzeni nazw, w której chcesz umieścić wszystkie deklaracje typu dla bieżącego projektu.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używasz pliku wykonywalnego w programie Visual Studio (Devenv.exe) aby skompilować projekt utworzony w programie Visual Studio zintegrowanego środowiska programistycznego, użyj `-rootnamespace` można określić wartość <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> właściwości. Zobacz [przełączników wiersza polecenia Devenv](/visualstudio/ide/reference/devenv-command-line-switches) Aby uzyskać więcej informacji.  
  
 Użyj środowiska uruchomieniowego języka wspólnego MSIL Disassembler (`Ildasm.exe`) aby wyświetlić nazwy przestrzeni nazw w pliku danych wyjściowych.  
  
|Aby ustawić - rootnamespace — w programie Visual Studio zintegrowane środowisko projektowe|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **aplikacji** kartę.<br />3.  Zmodyfikuj wartość w **Namespace głównego** pole.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i umieszcza wszystkie deklaracje typów w przestrzeni nazw `mynamespace`.  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Ildasm.exe (dezasembler IL)](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

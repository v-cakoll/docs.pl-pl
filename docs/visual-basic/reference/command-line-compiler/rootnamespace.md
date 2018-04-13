---
title: -rootnamespace
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45dce293549674e7e6aac2714e1a7a569719c597
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-rootnamespace"></a>-rootnamespace
Określa przestrzeń nazw dla wszystkich deklaracji typów.  
  
## <a name="syntax"></a>Składnia  
  
```  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`namespace`|Nazwa przestrzeni nazw, w którym należy ująć wszystkich deklaracji typów dla bieżącego projektu.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używasz pliku wykonywalnego programu Visual Studio (Devenv.exe) aby skompilować projekt utworzony w programie Visual Studio zintegrowane środowisko programistyczne, użyj `-rootnamespace` do określenia wartości <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> właściwości. Zobacz [przełączniki wiersza polecenia Devenv](/visualstudio/ide/reference/devenv-command-line-switches) Aby uzyskać więcej informacji.  
  
 Użyj środowiska CLR dezasembler MSIL (`Ildasm.exe`) do wyświetlenia nazwy przestrzeni nazw w pliku danych wyjściowych.  
  
|Aby ustawić - rootnamespace w programie Visual Studio zintegrowane środowisko deweloperskie|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **aplikacji** kartę.<br />3.  Zmodyfikuj wartość w **Namespace głównego** pole.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i umieszcza wszystkie deklaracje typu w przestrzeni nazw `mynamespace`.  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Ildasm.exe (dezasembler IL)](https://msdn.microsoft.com/library/f7dy01k1)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

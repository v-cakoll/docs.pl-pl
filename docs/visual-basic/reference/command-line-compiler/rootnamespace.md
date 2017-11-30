---
title: /rootnamespace
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6b5da8e5eacacde9de5bdc54ef2d5e4d7f0d2653
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="rootnamespace"></a>/rootnamespace
Określa przestrzeń nazw dla wszystkich deklaracji typów.  
  
## <a name="syntax"></a>Składnia  
  
```  
/rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`namespace`|Nazwa przestrzeni nazw, w którym należy ująć wszystkich deklaracji typów dla bieżącego projektu.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli używasz pliku wykonywalnego programu Visual Studio (Devenv.exe) aby skompilować projekt utworzony w programie Visual Studio zintegrowane środowisko programistyczne, użyj `/rootnamespace` do określenia wartości <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> właściwości. Zobacz [przełączniki wiersza polecenia Devenv](/visualstudio/ide/reference/devenv-command-line-switches) Aby uzyskać więcej informacji.  
  
 Użyj środowiska CLR dezasembler MSIL (`Ildasm.exe`) do wyświetlenia nazwy przestrzeni nazw w pliku danych wyjściowych.  
  
|Aby ustawić/rootnamespace w programie Visual Studio zintegrowane środowisko deweloperskie|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Kliknij przycisk **aplikacji** kartę.<br />3.  Zmodyfikuj wartość w **Namespace głównego** pole.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i umieszcza wszystkie deklaracje typu w przestrzeni nazw `mynamespace`.  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Ildasm.exe (dezasembler IL)](https://msdn.microsoft.com/library/f7dy01k1)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

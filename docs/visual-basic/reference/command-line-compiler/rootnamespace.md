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
ms.openlocfilehash: b02171b28034d676b7027e96c2c66e36be9ae604
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **aplikacji** kartę.<br />3.  Zmodyfikuj wartość w **Namespace głównego** pole.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i umieszcza wszystkie deklaracje typu w przestrzeni nazw `mynamespace`.  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Ildasm.exe (dezasembler IL)](https://msdn.microsoft.com/library/f7dy01k1)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

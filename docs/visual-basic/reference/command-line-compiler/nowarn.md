---
title: -nowarn
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d2f3f15ef12b24b8baedc9db59e772aa9eb073bc
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-nowarn"></a>-nowarn
Pomija możliwość generowania ostrzeżeń kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`numberList`|Opcjonalny. Rozdzielana przecinkami lista identyfikatorów ostrzeżenia kompilatora ma pomijać. Jeśli ostrzeżenie identyfikatory nie są określone, wszystkie ostrzeżenia będą pomijane.|  
  
## <a name="remarks"></a>Uwagi  
 `-nowarn` Opcja powoduje, że kompilator, aby nie generować ostrzeżenia. Aby pominąć poszczególnych ostrzeżenie, należy podać identyfikator ostrzeżenia, aby `-nowarn` opcji po dwukropkiem. Wiele numerów ostrzeżeń, które należy oddzielić przecinkami.  
  
 Należy określić numeryczna część identyfikatora ostrzeżenie. Na przykład, jeśli chcesz pominąć BC42024, ostrzeżenie dotyczące nieużywane zmienne lokalne, określ `-nowarn:42024`.  
  
 Aby uzyskać więcej informacji na numery identyfikatorów ostrzeżenia, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
|Aby ustawić - nowarn w programie Visual Studio zintegrowane środowisko deweloperskie|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Wybierz **Wyłącz wszystkie ostrzeżenia** pole wyboru, aby wyłączyć wszystkie ostrzeżenia.<br />     - lub -<br />     Aby wyłączyć ostrzeżenie, kliknij przycisk **Brak** z listy rozwijanej obok ostrzeżenia.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i nie są wyświetlane ostrzeżenia.  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i nie są wyświetlane ostrzeżenia dotyczące nieużywane zmienne lokalne (42024).  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Konfigurowanie ostrzeżeń w kodzie Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)

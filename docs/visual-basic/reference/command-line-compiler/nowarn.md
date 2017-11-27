---
title: /nowarn
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8da27ea2f9f0a4d370928d70cda1a796b822d97c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="nowarn"></a>/nowarn
Pomija możliwość generowania ostrzeżeń kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
/nowarn[:numberList]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`numberList`|Opcjonalny. Rozdzielana przecinkami lista identyfikatorów ostrzeżenia kompilatora ma pomijać. Jeśli ostrzeżenie identyfikatory nie są określone, wszystkie ostrzeżenia będą pomijane.|  
  
## <a name="remarks"></a>Uwagi  
 `/nowarn` Opcja powoduje, że kompilator, aby nie generować ostrzeżenia. Aby pominąć poszczególnych ostrzeżenie, należy podać identyfikator ostrzeżenia, aby `/nowarn` opcji po dwukropkiem. Wiele numerów ostrzeżeń, które należy oddzielić przecinkami.  
  
 Należy określić numeryczna część identyfikatora ostrzeżenie. Na przykład, jeśli chcesz pominąć BC42024, ostrzeżenie dotyczące nieużywane zmienne lokalne, określ `/nowarn:42024`.  
  
 Aby uzyskać więcej informacji na numery identyfikatorów ostrzeżenia, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
|Aby ustawić/nowarn w programie Visual Studio zintegrowane środowisko deweloperskie|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Wybierz **Wyłącz wszystkie ostrzeżenia** pole wyboru, aby wyłączyć wszystkie ostrzeżenia.<br />     - lub -<br />     Aby wyłączyć ostrzeżenie, kliknij przycisk **Brak** z listy rozwijanej obok ostrzeżenia.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i nie są wyświetlane ostrzeżenia.  
  
```  
vbc /nowarn t2.vb  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i nie są wyświetlane ostrzeżenia dotyczące nieużywane zmienne lokalne (42024).  
  
```  
vbc /nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Kompilacja przykładów — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)

---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 338b4672d215968275c30d37a2f8061e764aed8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653445"
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
|`numberList`|Opcjonalna. Rozdzielana przecinkami lista identyfikatorów ostrzeżenia kompilatora ma pomijać. Jeśli ostrzeżenie identyfikatory nie są określone, wszystkie ostrzeżenia będą pomijane.|  
  
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

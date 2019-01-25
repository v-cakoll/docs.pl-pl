---
title: -nowarn —
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: eff367fd6cc14c655f0c623731e334054233b0a0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744313"
---
# <a name="-nowarn"></a>-nowarn —
Pomija zdolność kompilatora do generowania ostrzeżeń.  
  
## <a name="syntax"></a>Składnia  
  
```  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`numberList`|Opcjonalna. Rozdzielana przecinkami lista numerów Identyfikacyjnych ostrzeżenia, które kompilator powinien pominąć. Jeśli nie określono ostrzeżenie identyfikatorów, wszystkie ostrzeżenia są pomijane.|  
  
## <a name="remarks"></a>Uwagi  
 `-nowarn` Opcji powoduje, że kompilator generuje ostrzeżenia. Aby pominąć to ostrzeżenie indywidualnych, należy podać identyfikator ostrzeżenie do `-nowarn` opcji zgodnie z dwukropkiem. Oddziel wiele numerów ostrzeżeń przecinkami.  
  
 Należy określić tylko część numeryczna identyfikatora ostrzeżenia. Na przykład, jeśli chcesz pominąć BC42024, ostrzeżenie dotyczące nieużywane zmienne lokalne, określ `-nowarn:42024`.  
  
 Aby uzyskać więcej informacji na temat identyfikatorów ostrzeżenie, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
|Aby ustawić - nowarn — w programie Visual Studio zintegrowane środowisko projektowe|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Wybierz **Wyłącz wszystkie ostrzeżenia** pole wyboru, aby wyłączyć wszystkie ostrzeżenia.<br />     - lub -<br />     Aby wyłączyć określonego ostrzeżenia, kliknij pozycję **Brak** z listy rozwijanej obok ostrzeżenia.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i nie zawiera żadnych ostrzeżeń.  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i nie są wyświetlane ostrzeżenia dotyczące nieużywane zmienne lokalne (42024).  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>Zobacz także
- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Konfigurowanie ostrzeżeń w kodzie Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)

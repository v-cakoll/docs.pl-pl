---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 880fdf4931dadea547d64d0506bd3e978956468e
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005402"
---
# <a name="-nowarn"></a>-nowarn
Pomija możliwość generowania ostrzeżeń przez kompilator.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`numberList`|Opcjonalny. Rozdzielana przecinkami lista numerów IDENTYFIKACYJNych ostrzeżeń, które kompilator powinien pominąć. Jeśli nie określono identyfikatorów ostrzeżeń, wszystkie ostrzeżenia są pomijane.|  
  
## <a name="remarks"></a>Uwagi  
 Opcja `-nowarn` powoduje, że kompilator nie generuje ostrzeżeń. Aby pominąć pojedyncze ostrzeżenie, należy podać identyfikator ostrzeżenia dla opcji `-nowarn` po dwukropku. Oddziel wiele numerów ostrzeżeń przecinkami.  
  
 Należy określić tylko część liczbową identyfikatora ostrzeżenia. Na przykład jeśli chcesz pominąć BC42024, Ostrzeżenie dla nieużywanych zmiennych lokalnych, określ `-nowarn:42024`.  
  
 Aby uzyskać więcej informacji na temat numerów IDENTYFIKACYJNych ostrzeżeń, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
|Aby ustawić-nowarn w zintegrowanym środowisku programistycznym programu Visual Studio|  
|---|  
|1. zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**. <br />2. Kliknij kartę **kompilacja** .<br />3. Zaznacz pole wyboru **Wyłącz wszystkie ostrzeżenia** , aby wyłączyć wszystkie ostrzeżenia.<br />     oraz<br />     Aby wyłączyć określone ostrzeżenie, kliknij **Brak** z listy rozwijanej obok ostrzeżenia.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i nie wyświetla żadnych ostrzeżeń.  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i nie wyświetla ostrzeżeń dla nieużywanych zmiennych lokalnych (42024).  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Konfigurowanie ostrzeżeń w kodzie Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)

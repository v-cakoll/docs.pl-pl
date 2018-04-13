---
title: -warnaserror (Visual Basic)
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ae8ed68045529e626f2788f854d8e6a6933e7e2
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-warnaserror-visual-basic"></a>-warnaserror (Visual Basic)
Umożliwia kompilatorowi na traktowanie pierwszego wystąpienia ostrzeżenie jako błąd.  
  
## <a name="syntax"></a>Składnia  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|+ &#124; -|Opcjonalny. Domyślnie `-warnaserror-` jest obowiązująca; ostrzeżenia nie uniemożliwiają kompilator Tworzenie pliku wyjściowego. `-warnaserror` Opcja, która jest taka sama jak `-warnaserror+`, powoduje, że ostrzeżenia, które będą traktowane jako błędy.|  
|`numberList`|Opcjonalny. Rozdzielana przecinkami lista Identyfikator ostrzeżenia numery, do którego `-warnaserror` opcja ma zastosowanie. Jeśli nie ostrzeżenie określono Identyfikatora, `-warnaserror` opcja ma zastosowanie do wszystkich ostrzeżeń.|  
  
## <a name="remarks"></a>Uwagi  
 `-warnaserror` Opcja traktuje wszystkie ostrzeżenia jako błędy. Komunikaty, które będą zgłaszane zwykle są natomiast zgłoszonej ostrzeżenia jako błędy. Kompilator zgłasza kolejne wystąpienia tej samej ostrzeżenie jako ostrzeżenia.  
  
 Domyślnie `-warnaserror-` obowiązują, co powoduje, że ostrzeżenia informacyjne tylko do. `-warnaserror` Opcja, która jest taka sama jak `-warnaserror+`, powoduje, że ostrzeżenia, które będą traktowane jako błędy.  
  
 Jeśli chcesz tylko kilka konkretne ostrzeżenia, które będą traktowane jako błędy, można określić rozdzielana przecinkami lista numerów ostrzeżeń, które mają być traktowane jako błędy.  
  
> [!NOTE]
>  `-warnaserror` Opcji nie kontroluje sposób wyświetlania ostrzeżeń. Użyj [- nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) opcję, aby wyłączyć ostrzeżenia.  
  
|Aby ustawić - warnaserror traktuje wszystkie ostrzeżenia jako błędy w środowisku IDE programu Visual Studio|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Upewnij się, że **Wyłącz wszystkie ostrzeżenia** pole wyboru jest zaznaczone.<br />4.  Sprawdź **traktuje wszystkie ostrzeżenia jako błędy** pole wyboru.|  
  
|Aby ustawić - warnaserror Traktuj konkretne ostrzeżenia jako błędy w środowisku IDE programu Visual Studio|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.<br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Upewnij się, że **Wyłącz wszystkie ostrzeżenia** pole wyboru jest zaznaczone.<br />4.  Upewnij się, że **traktuje wszystkie ostrzeżenia jako błędy** pole wyboru jest zaznaczone.<br />5.  Wybierz **błąd** z **powiadomień** kolumny sąsiadujące ostrzeżenia, które powinny być traktowane jako błąd.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i kieruje kompilator, aby wyświetlić błąd dla pierwszego wystąpienia każdego ostrzeżenia znajdzie.  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i traktuje ostrzeżenia dla nieużywane zmienne lokalne (42024) jako błąd.  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Konfigurowanie ostrzeżeń w kodzie Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)

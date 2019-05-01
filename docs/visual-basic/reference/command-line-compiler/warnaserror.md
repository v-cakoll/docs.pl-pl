---
title: -warnaserror — (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: c06326a250fba0de2f63e13672b4fffbfa8a07f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796178"
---
# <a name="-warnaserror-visual-basic"></a>-warnaserror — (Visual Basic)
Powoduje, że kompilator o konieczności potraktowania pierwsze wystąpienie ostrzeżenie jako błąd.  
  
## <a name="syntax"></a>Składnia  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|+ &#124; -|Opcjonalna. Domyślnie `-warnaserror-` jest obowiązywały; ostrzeżenia nie uniemożliwiają kompilator tworzenia pliku wyjściowego. `-warnaserror` Opcja, która jest taka sama jak `-warnaserror+`, powoduje, że ostrzeżenia są traktowane jako błędy.|  
|`numberList`|Opcjonalna. Rozdzielana przecinkami lista identyfikatora ostrzeżenie liczby, do którego `-warnaserror` opcja ma zastosowanie. Jeśli jest określony żaden identyfikator ostrzeżenia, `-warnaserror` opcja ma zastosowanie do wszystkich ostrzeżeń.|  
  
## <a name="remarks"></a>Uwagi  
 `-warnaserror` Opcja traktuje wszystkie ostrzeżenia jako błędy. Komunikaty, które zazwyczaj będzie zgłaszane jako ostrzeżenia zamiast tego są zgłaszane jako błędy. Kompilator raporty kolejnych wystąpień tego samego ostrzeżenie jako ostrzeżenia.  
  
 Domyślnie `-warnaserror-` obowiązują, co powoduje, że ostrzeżenia informacyjne tylko do. `-warnaserror` Opcja, która jest taka sama jak `-warnaserror+`, powoduje, że ostrzeżenia są traktowane jako błędy.  
  
 Jeśli chcesz tylko kilka określone ostrzeżenia są traktowane jako błędy, można określić przecinkami lista numerów ostrzeżeń do traktowania jako błędy.  
  
> [!NOTE]
>  `-warnaserror` Opcji nie kontroluje sposób wyświetlania ostrzeżenia. Użyj [- nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) opcję, aby wyłączyć ostrzeżenia.  
  
|Aby ustawić - warnaserror — na traktowanie wszystkich ostrzeżeń jako błędy w środowisku IDE programu Visual Studio|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Upewnij się, że **Wyłącz wszystkie ostrzeżenia** pole wyboru jest zaznaczone.<br />4.  Sprawdź **traktowanie wszystkich ostrzeżeń jako błędy** pole wyboru.|  
  
|Aby ustawić - warnaserror Traktuj szczególne ostrzeżenia jako błędy w środowisku IDE programu Visual Studio|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.<br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Upewnij się, że **Wyłącz wszystkie ostrzeżenia** pole wyboru jest zaznaczone.<br />4.  Upewnij się, że **traktowanie wszystkich ostrzeżeń jako błędy** pole wyboru jest zaznaczone.<br />5.  Wybierz **błąd** z **powiadomień** kolumny sąsiadujące ostrzeżenie, że powinny być traktowane jako błąd.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i instruuje kompilator, aby wyświetlić błąd dla pierwszego wystąpienia każde ostrzeżenie znajdzie.  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i traktuje ostrzeżenia dla nieużywane zmienne lokalne (42024) jako błąd.  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Konfigurowanie ostrzeżeń w kodzie Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)

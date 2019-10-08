---
title: -warnaserror — (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 8af6d3ef4efecd53dcf38c33d0aa2cf182f07d30
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004650"
---
# <a name="-warnaserror-visual-basic"></a>-warnaserror — (Visual Basic)
Powoduje, że kompilator traktuje pierwsze wystąpienie ostrzeżenia jako błąd.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|+ &#124; -|Opcjonalny. Domyślnie `-warnaserror-` jest w efekcie; ostrzeżenia nie uniemożliwiają kompilatorowi tworzenia pliku wyjściowego. Opcja `-warnaserror`, która jest taka sama jak `-warnaserror+`, powoduje, że ostrzeżenia są traktowane jako błędy.|  
|`numberList`|Opcjonalny. Rozdzielana przecinkami lista numerów IDENTYFIKACYJNych ostrzeżeń, do których jest stosowana opcja `-warnaserror`. Jeśli nie określono identyfikatora ostrzeżenia, opcja `-warnaserror` dotyczy wszystkich ostrzeżeń.|  
  
## <a name="remarks"></a>Uwagi  
 Opcja `-warnaserror` traktuje wszystkie ostrzeżenia jako błędy. Wszystkie komunikaty, które zwykle są raportowane jako ostrzeżenia, są raportowane jako błędy. Kompilator raportuje kolejne wystąpienia tego samego ostrzeżenia co ostrzeżenia.  
  
 Domyślnie `-warnaserror-` jest w efekcie, co powoduje, że ostrzeżenia są tylko informacyjne. Opcja `-warnaserror`, która jest taka sama jak `-warnaserror+`, powoduje, że ostrzeżenia są traktowane jako błędy.  
  
 Jeśli chcesz, aby tylko kilka określonych ostrzeżeń była traktowana jak błędy, możesz określić rozdzieloną przecinkami listę numerów ostrzeżeń, które mają być traktowane jako błędy.  
  
> [!NOTE]
> Opcja `-warnaserror` nie kontroluje sposobu wyświetlania ostrzeżeń. Użyj opcji [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) , aby wyłączyć ostrzeżenia.  
  
|Aby ustawić-warnaserror — wszystkie ostrzeżenia jako błędy w środowisku IDE programu Visual Studio|  
|---|  
|1. zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**. <br />2. Kliknij kartę **kompilacja** .<br />3. Upewnij się, że pole wyboru **Wyłącz wszystkie ostrzeżenia** nie jest zaznaczone.<br />4. Zaznacz pole wyboru **Traktuj wszystkie ostrzeżenia jako błędy** .|  
  
|Aby ustawić-warnaserror — do traktowania określonych ostrzeżeń jako błędów w środowisku IDE programu Visual Studio|  
|---|  
|1. zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**.<br />2. Kliknij kartę **kompilacja** .<br />3. Upewnij się, że pole wyboru **Wyłącz wszystkie ostrzeżenia** nie jest zaznaczone.<br />4. Upewnij się, że pole wyboru **Traktuj wszystkie ostrzeżenia jako błędy** nie jest zaznaczone.<br />5. Wybierz **błąd** z kolumny **powiadomień** sąsiadującej z ostrzeżeniem, które ma być traktowane jako błąd.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i instruuje kompilator, aby wyświetlał błąd pierwszego wystąpienia każdego ostrzeżenia, które znajdzie.  
  
```console
vbc -warnaserror in.vb  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i traktuje tylko Ostrzeżenie dla nieużywanych zmiennych lokalnych (42024) jako błąd.  
  
```console
vbc -warnaserror:42024 t2.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Konfigurowanie ostrzeżeń w kodzie Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)

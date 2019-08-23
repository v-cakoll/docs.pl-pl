---
title: -warnaserror — (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 4382ec8feda2df1e83fd2fdc509abb66984e501f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937255"
---
# <a name="-warnaserror-visual-basic"></a>-warnaserror — (Visual Basic)
Powoduje, że kompilator traktuje pierwsze wystąpienie ostrzeżenia jako błąd.  
  
## <a name="syntax"></a>Składnia  
  
```  
-warnaserror[+ | -][:numberList]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|+ &#124; -|Opcjonalny. Domyślnie program `-warnaserror-` jest w efekcie. ostrzeżenia nie uniemożliwiają kompilatorowi tworzenia pliku wyjściowego. Opcja, która jest taka sama jak `-warnaserror+`, powoduje, że ostrzeżenia są traktowane jako błędy. `-warnaserror`|  
|`numberList`|Opcjonalna. Rozdzielana przecinkami lista numerów identyfikacyjnych ostrzeżeń, do których zostanie `-warnaserror` zastosowana opcja. Jeśli nie określono identyfikatora ostrzeżenia, `-warnaserror` opcja ma zastosowanie do wszystkich ostrzeżeń.|  
  
## <a name="remarks"></a>Uwagi  
 `-warnaserror` Opcja traktuje wszystkie ostrzeżenia jako błędy. Wszystkie komunikaty, które zwykle są raportowane jako ostrzeżenia, są raportowane jako błędy. Kompilator raportuje kolejne wystąpienia tego samego ostrzeżenia co ostrzeżenia.  
  
 Domyślnie `-warnaserror-` obowiązuje, co powoduje, że ostrzeżenia są tylko informacyjne. Opcja, która jest taka sama jak `-warnaserror+`, powoduje, że ostrzeżenia są traktowane jako błędy. `-warnaserror`  
  
 Jeśli chcesz, aby tylko kilka określonych ostrzeżeń była traktowana jak błędy, możesz określić rozdzieloną przecinkami listę numerów ostrzeżeń, które mają być traktowane jako błędy.  
  
> [!NOTE]
> `-warnaserror` Opcja nie kontroluje sposobu wyświetlania ostrzeżeń. Użyj opcji [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md) , aby wyłączyć ostrzeżenia.  
  
|Aby ustawić-warnaserror — wszystkie ostrzeżenia jako błędy w środowisku IDE programu Visual Studio|  
|---|  
|1.  Zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**. <br />2.  Kliknij kartę **kompilacja** .<br />3.  Upewnij się, że pole wyboru **Wyłącz wszystkie ostrzeżenia** nie jest zaznaczone.<br />4.  Zaznacz pole wyboru **Traktuj wszystkie ostrzeżenia jako błędy** .|  
  
|Aby ustawić-warnaserror — do traktowania określonych ostrzeżeń jako błędów w środowisku IDE programu Visual Studio|  
|---|  
|1.  Zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**.<br />2.  Kliknij kartę **kompilacja** .<br />3.  Upewnij się, że pole wyboru **Wyłącz wszystkie ostrzeżenia** nie jest zaznaczone.<br />4.  Upewnij się, że pole wyboru **Traktuj wszystkie ostrzeżenia jako błędy** nie jest zaznaczone.<br />5.  Wybierz **błąd** z kolumny **powiadomień** sąsiadującej z ostrzeżeniem, które ma być traktowane jako błąd.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i kieruje kompilator w celu wyświetlenia błędu pierwszego wystąpienia każdego ostrzeżenia, które znajdzie.  
  
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

---
title: -warnaserror
ms.date: 03/13/2018
helpviewer_keywords:
- warnaserror compiler option [Visual Basic]
- /warnaserror compiler option [Visual Basic]
- -warnaserror compiler option [Visual Basic]
ms.assetid: 49819f1d-a1bd-4201-affe-5afe6d9712e1
ms.openlocfilehash: 94a8b43a891df9837925869e17fac4536a995264
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414275"
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
|+ &#124;-|Opcjonalny. Domyślnie program `-warnaserror-` jest w efekcie. ostrzeżenia nie uniemożliwiają kompilatorowi tworzenia pliku wyjściowego. `-warnaserror`Opcja, która jest taka sama jak `-warnaserror+` , powoduje, że ostrzeżenia są traktowane jako błędy.|  
|`numberList`|Opcjonalny. Rozdzielana przecinkami lista numerów IDENTYFIKACYJNych ostrzeżeń, do których zostanie `-warnaserror` zastosowana opcja. Jeśli nie określono identyfikatora ostrzeżenia, `-warnaserror` opcja ma zastosowanie do wszystkich ostrzeżeń.|  
  
## <a name="remarks"></a>Uwagi  
 `-warnaserror`Opcja traktuje wszystkie ostrzeżenia jako błędy. Wszystkie komunikaty, które zwykle są raportowane jako ostrzeżenia, są raportowane jako błędy. Kompilator raportuje kolejne wystąpienia tego samego ostrzeżenia co ostrzeżenia.  
  
 Domyślnie `-warnaserror-` obowiązuje, co powoduje, że ostrzeżenia są tylko informacyjne. `-warnaserror`Opcja, która jest taka sama jak `-warnaserror+` , powoduje, że ostrzeżenia są traktowane jako błędy.  
  
 Jeśli chcesz, aby tylko kilka określonych ostrzeżeń była traktowana jak błędy, możesz określić rozdzieloną przecinkami listę numerów ostrzeżeń, które mają być traktowane jako błędy.  
  
> [!NOTE]
> `-warnaserror`Opcja nie kontroluje sposobu wyświetlania ostrzeżeń. Użyj opcji [-nowarn](nowarn.md) , aby wyłączyć ostrzeżenia.  
  
|Aby ustawić-warnaserror — wszystkie ostrzeżenia jako błędy w środowisku IDE programu Visual Studio|  
|---|  
|1. zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**. <br />2. Kliknij kartę **kompilacja** .<br />3. Upewnij się, że pole wyboru **Wyłącz wszystkie ostrzeżenia** nie jest zaznaczone.<br />4. Zaznacz pole wyboru **Traktuj wszystkie ostrzeżenia jako błędy** .|  
  
|Aby ustawić-warnaserror — do traktowania określonych ostrzeżeń jako błędów w środowisku IDE programu Visual Studio|  
|---|  
|1. zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**.<br />2. Kliknij kartę **kompilacja** .<br />3. Upewnij się, że pole wyboru **Wyłącz wszystkie ostrzeżenia** nie jest zaznaczone.<br />4. Upewnij się, że pole wyboru **Traktuj wszystkie ostrzeżenia jako błędy** nie jest zaznaczone.<br />5. Wybierz **błąd** z kolumny **powiadomień** sąsiadującej z ostrzeżeniem, które ma być traktowane jako błąd.|  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
- [Konfigurowanie ostrzeżeń w kodzie Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)

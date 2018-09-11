---
title: Nieprawidłowa wartość sumy kontrolnej, cyfry nieszesnastkowe lub nieparzysta liczba cyfr szesnastkowych
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: e682c2c23dd6fe80aee87d2a86b3df2dae66b802
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276464"
---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a>Nieprawidłowa wartość sumy kontrolnej, cyfry nieszesnastkowe lub nieparzysta liczba cyfr szesnastkowych
Wartość sumy kontrolnej zawiera nieprawidłowy liczb szesnastkowych lub ma nieparzysta liczba cyfr.  
  
 Gdy program ASP.NET wygeneruje plik źródłowy języka Visual Basic (.vb rozszerzenie), oblicza sumy kontrolnej i umieszcza je w pliku źródłowym ukryte identyfikowane przez `#externalchecksum`. Istnieje możliwość, że użytkownik generowania pliku .vb, w tym również ten proces jest jednak najlepszym od lewej do użytku wewnętrznego.  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Uzyskać informacje o ukrywaniu ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42033  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Jeśli program ASP.NET generuje plik źródłowy języka Visual Basic, należy ponownie uruchomić kompilacji projektu.  
  
2.  Jeśli to ostrzeżenie będzie nadal występował po ponownym uruchomieniu komputera, ponownej instalacji programu ASP.NET, a następnie ponów próbę kompilacji.  
  
3.  Jeśli to ostrzeżenie będzie nadal występować lub jeśli nie używasz platformy ASP.NET, zebrać informacje dotyczące okoliczności i powiadom pomoc techniczna firmy Microsoft.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie programu ASP.NET](/aspnet/overview)  
- [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)

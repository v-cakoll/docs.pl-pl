---
title: Nieprawidłowa wartość sumy kontrolnej, cyfry nieszesnastkowe lub nieparzysta liczba cyfr szesnastkowych
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: 5c01e918e1f607febc10be89c3d27c50870c401a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589254"
---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a>Nieprawidłowa wartość sumy kontrolnej, cyfry nieszesnastkowe lub nieparzysta liczba cyfr szesnastkowych
Wartość sumy kontrolnej zawiera nieprawidłowe cyfry szesnastkowe lub ma nieparzystą liczbę cyfr.  
  
 Gdy program ASP.NET wygeneruje plik źródłowy języka Visual Basic (.vb rozszerzenia), oblicza sumę kontrolną i umieszcza je w pliku źródłowym ukryte identyfikowane przez `#externalchecksum`. Istnieje możliwość, że użytkownik Generowanie pliku .vb, w tym również, ale ten proces jest najlepszym od lewej do użytku wewnętrznego.  
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać informacje na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42033  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Jeśli program ASP.NET jest generowany plik źródłowy języka Visual Basic, uruchom ponownie kompilacji projektu.  
  
2.  Jeśli to ostrzeżenie będzie nadal występował po ponownym uruchomieniu, ponownej instalacji programu ASP.NET i spróbuj ponownie kompilacji.  
  
3.  Jeśli to ostrzeżenie będzie nadal występować lub jeśli nie używasz programu ASP.NET, zebrać informacje dotyczące okoliczności i powiadomić pomocy technicznej firmy Microsoft.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie programu ASP.NET](https://msdn.microsoft.com/library/4w3ex9c2.aspx)  
 [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)

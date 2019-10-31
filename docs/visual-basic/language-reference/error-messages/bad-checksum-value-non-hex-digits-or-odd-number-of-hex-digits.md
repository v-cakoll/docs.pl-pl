---
title: Nieprawidłowa wartość sumy kontrolnej, cyfry nieszesnastkowe lub nieparzysta liczba cyfr szesnastkowych
ms.date: 07/20/2015
f1_keywords:
- bc42033
- vbc42033
helpviewer_keywords:
- BC42033
ms.assetid: 4575554d-3615-46e4-9c6a-18e9c338e4ed
ms.openlocfilehash: 1ae4113505ca63df9b20e6e71aa0b418da4ef924
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197350"
---
# <a name="bad-checksum-value-non-hex-digits-or-odd-number-of-hex-digits"></a>Nieprawidłowa wartość sumy kontrolnej, cyfry nieszesnastkowe lub nieparzysta liczba cyfr szesnastkowych
Wartość sumy kontrolnej zawiera nieprawidłowe cyfry szesnastkowe lub ma nieparzystą liczbę cyfr.  
  
 Gdy ASP.NET generuje plik źródłowy Visual Basic (rozszerzenie. vb), oblicza sumę kontrolną i umieszcza ją w ukrytym pliku źródłowym identyfikowanym przez `#externalchecksum`. Istnieje możliwość, że użytkownik generuje plik. vb, aby to zrobić, ale ten proces jest najlepiej używany do użytku wewnętrznego.  
  
 Domyślnie ten komunikat jest ostrzeżeniem. Aby uzyskać informacje na temat ukrywania ostrzeżeń lub leczenia ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42033  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Jeśli ASP.NET generuje plik źródłowy Visual Basic, uruchom ponownie kompilację projektu.  
  
2. Jeśli to ostrzeżenie będzie nadal występować po ponownym uruchomieniu, zainstaluj ponownie ASP.NET i spróbuj ponownie wykonać kompilację.  
  
3. Jeśli ostrzeżenie nadal się utrzymuje lub jeśli nie korzystasz z programu ASP.NET, Zbierz informacje o okolicznościach i powiadom usługi pomocy technicznej firmy Microsoft.  
  
## <a name="see-also"></a>Zobacz także

- [ASP.NET — Omówienie](/aspnet/overview)
- [Porozmawiaj z nami](/visualstudio/ide/feedback-options)

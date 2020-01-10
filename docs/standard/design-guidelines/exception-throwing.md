---
title: Zgłaszanie wyjątku
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: 7d1b63e5fde57cbe37a1250d16b6bf74a2d5dc8e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709403"
---
# <a name="exception-throwing"></a>Zgłaszanie wyjątku
Zasady zgłaszania wyjątku opisane w tej sekcji wymagają odpowiedniej definicji znaczenia błędu wykonania. Niepowodzenie wykonywania występuje zawsze, gdy członek nie może wykonać czynności, do których został zaprojektowany (co oznacza nazwa elementu członkowskiego). Na przykład, jeśli metoda `OpenFile` nie może zwrócić otwartego dojścia do pliku wywołującego, będzie ona traktowana jako błąd wykonania.  
  
 Większość deweloperów była wygodna z użyciem wyjątków dla błędów użycia, takich jak dzielenie przez zero lub puste odwołania. W strukturze wyjątki są używane dla wszystkich warunków błędów, w tym błędów wykonania.  
  
 **X DO NOT** Zwróć kody błędów.  
  
 Wyjątkiem są podstawowe metody raportowania błędów w strukturach.  
  
 **✓ DO** Zgłoś błędy wykonania przez zgłaszanie wyjątków.  
  
 **✓ CONSIDER** Trwa kończenie procesu przez wywołanie metody `System.Environment.FailFast` (funkcja .NET Framework 2.0) zamiast generowania wyjątku, jeśli kod napotkał sytuacji, gdy jest niebezpieczny dla dalszego wykonywania.  
  
 **X DO NOT** Użyj wyjątki dla przepływu sterowania, jeśli to możliwe.  
  
 Z wyjątkiem awarii systemu i operacji z potencjalnymi warunkami wyścigu, projektanci struktury powinni projektować interfejsy API, aby użytkownicy mogli pisać kod, który nie zgłasza wyjątków. Na przykład można umożliwić sprawdzenie warunków wstępnych przed wywołaniem elementu członkowskiego, aby użytkownicy mogli pisać kod, który nie zgłasza wyjątków.  
  
 Element członkowski używany do sprawdzania warunków wstępnych innego elementu członkowskiego jest często nazywany testerem, a element członkowski, który faktycznie wykonuje prace, nosi nazwę DOER.  
  
 Istnieją przypadki, w których wzorzec testera DOER może mieć nieakceptowalne obciążenie wydajności. W takich przypadkach należy wziąć pod uwagę ten wzór try-Parse (zobacz [wyjątki i wydajność](../../../docs/standard/design-guidelines/exceptions-and-performance.md) , aby uzyskać więcej informacji).  
  
 **✓ CONSIDER** skutki wydajności zgłaszanie wyjątków. Stawki za 100 na sekundę mogą mieć zauważalny wpływ na wydajność większości aplikacji.  
  
 **✓ DO** dokumentu wszystkie wyjątki zgłaszane przez członków publicznie można wywołać z powodu naruszenia elementu członkowskiego kontraktu (zamiast awarii systemu) i je traktować jako część Umowy.  
  
 Wyjątki, które są częścią kontraktu, nie powinny się zmieniać z jednej wersji na następną (tj. nie należy zmieniać typu wyjątku, a nowe wyjątki nie powinny być dodawane).  
  
 **X DO NOT** ma publicznych członków, których można albo throw lub nie na podstawie niektórych opcji.  
  
 **X DO NOT** ma publicznych elementów członkowskich, które zwracają wyjątki jako wartości zwracane lub `out` parametru.  
  
 Zwracanie wyjątków z publicznych interfejsów API zamiast zgłaszania ich przez wiele zalet raportowania błędów opartych na wyjątkach.  
  
 **✓ CONSIDER** za pomocą metody konstruktora wyjątku.  
  
 Często należy zgłosić ten sam wyjątek z różnych miejsc. Aby uniknąć przeładowanie kodu, należy użyć metod pomocnika, które tworzą wyjątki i inicjują ich właściwości.  
  
 Ponadto elementy członkowskie, które generują wyjątki, nie są obsługiwane. Przeniesienie instrukcji throw wewnątrz konstruktora może pozwolić, aby element członkowski był wbudowany.  
  
 **X DO NOT** zgłaszanie wyjątków z bloki filtru wyjątków.  
  
 Gdy filtr wyjątku zgłasza wyjątek, wyjątek jest przechwytywany przez środowisko CLR, a filtr zwraca wartość false. Takie zachowanie jest odróżnienie od wykonywanych przez filtr i zwraca wartość false, dlatego trudno jest debugować.  
  
 **X AVOID** jawne zgłaszanie wyjątków z bloki finally. Niejawnie zgłoszone wyjątki powstałe w wyniku wywoływania metod wywołujących są akceptowalne.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Wyjątki — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/exceptions.md)

---
title: Wyrzucanie wyjątków
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a493e6591d90ce05a652e48807f63fa90764a91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573724"
---
# <a name="exception-throwing"></a>Wyrzucanie wyjątków
Wytyczne zgłaszanie wyjątków opisanych w tej sekcji wymaga dobrej definicji znaczenie błąd wykonania. Niepowodzenie wykonania występuje zawsze, gdy element członkowski nie może wykonać, co zostało zaprojektowane w celu (co nazwa elementu członkowskiego oznacza). Na przykład jeśli `OpenFile` nie może zwracać dojście otwartego pliku do obiektu wywołującego, jego mogą być uważane za błąd wykonania.  
  
 Większość deweloperów stały się doświadczenia w używaniu wyjątki użycia błędów, takich jak dzielenie przez zero lub puste odwołania. W ramach wyjątki są używane dla wszystkich warunków błędu, w tym błędy wykonania.  
  
 **X nie** Zwróć kody błędów.  
  
 Wyjątki są podstawowy sposób raportowanie błędów w struktury.  
  
 **CZY ✓** Zgłoś błędy wykonania przez zgłaszanie wyjątków.  
  
 **ROZWAŻ ✓** Trwa kończenie procesu przez wywołanie metody `System.Environment.FailFast` (funkcja .NET Framework 2.0) zamiast generowania wyjątku, jeśli kod napotkał sytuacji, gdy jest niebezpieczny dla dalszego wykonywania.  
  
 **X nie** Użyj wyjątki dla przepływu sterowania, jeśli to możliwe.  
  
 Z wyjątkiem operacji o potencjalnych sytuacji wyścigu i awarie systemu framework Designer należy projektować interfejsów API tak użytkowników można napisać kod, który nie zgłaszają wyjątki. Można na przykład można podać sposób sprawdzania warunków wstępnych przed wywołaniem członka, więc użytkowników można napisać kod, który nie zgłaszają wyjątki.  
  
 Element członkowski używany do sprawdzania warunków wstępnych dla innego elementu członkowskiego jest często określany jako tester, a element członkowski, który wykonuje rzeczywistą pracę nosi nazwę doer.  
  
 Istnieją przypadki, gdy wzorzec Tester Doer może mieć zmniejszenie wydajności nie do przyjęcia. W takiej sytuacji należy rozważyć tak zwane wzorzec spróbuj analizy (zobacz [wyjątki i wydajności](../../../docs/standard/design-guidelines/exceptions-and-performance.md) Aby uzyskać więcej informacji).  
  
 **ROZWAŻ ✓** skutki wydajności zgłaszanie wyjątków. Stawki throw powyżej 100 na sekundę mogą znacznie wpłynąć na wydajność większości aplikacji.  
  
 **CZY ✓** dokumentu wszystkie wyjątki zgłaszane przez członków publicznie można wywołać z powodu naruszenia elementu członkowskiego kontraktu (zamiast awarii systemu) i je traktować jako część Umowy.  
  
 Wyjątki, które są częścią kontraktu nie należy zmieniać z jedną wersję do następnego (tj. typ wyjątku nie należy zmieniać i nie należy dodawać nowych wyjątków).  
  
 **X nie** ma publicznych członków, których można albo throw lub nie na podstawie niektórych opcji.  
  
 **X nie** ma publicznych elementów członkowskich, które zwracają wyjątki jako wartości zwracane lub `out` parametru.  
  
 Zwracanie wyjątki z publiczne interfejsy API, zamiast je zgłaszanie pozbawia wiele zalet raportowanie błędów na podstawie wyjątku.  
  
 **ROZWAŻ ✓** za pomocą metody konstruktora wyjątku.  
  
 Są często, aby zgłosić ten sam wyjątek w różnych miejscach. Aby uniknąć rozrostu kodu, należy użyć metody pomocnicze, które Tworzenie wyjątków i zainicjuj ich właściwości.  
  
 Ponadto nie otrzymują elementów członkowskich, które zgłaszają wyjątki śródwierszowych. Przenoszenie instrukcję throw do konstruktora mogą zezwalać elementu członkowskiego był śródwierszowy.  
  
 **X nie** zgłaszanie wyjątków z bloki filtru wyjątków.  
  
 Gdy filtru wyjątków zgłasza wyjątek, wyjątek zostanie przechwycony przez środowisko CLR, a filtr zwraca wartość false. To zachowanie jest można odróżnić od filtru wykonywania i zwrócenie wartości false w sposób jawny i dlatego jest bardzo trudne do debugowania.  
  
 **X należy UNIKAĆ** jawne zgłaszanie wyjątków z bloki finally. Niejawnie zgłoszenia wyjątku będącym wynikiem wywołania metody, które zgłaszają są dozwolone.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Wyjątki — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/exceptions.md)

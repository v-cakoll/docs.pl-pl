---
title: Zgłaszanie wyjątku
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fbbe84811e3fa096b9e13c459143311bb75a198
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44132645"
---
# <a name="exception-throwing"></a>Zgłaszanie wyjątku
Zgłaszanie wyjątku wytyczne opisane w tej sekcji wymaga dobrych definicji znaczenie błąd wykonania. Niepowodzenie wykonywania występuje zawsze, gdy członek nie, co zostało zaprojektowane w celu (co nazwa elementu członkowskiego oznacza). Na przykład jeśli `OpenFile` nie może zwracać dojście otwartego pliku do obiektu wywołującego, jego mogłoby być uważane za wystąpił błąd wykonania.  
  
 Większość programistów stały się komfortowo, jednocześnie używania wyjątków do użycia błędy, takie jak dzielenie przez zero lub odwołania o wartości null. W ramach wyjątki są używane dla wszystkich warunków błędu, w tym błędy wykonania.  
  
 **X DO NOT** Zwróć kody błędów.  
  
 Wyjątki są podstawowym sposobem raportowania błędów w struktur.  
  
 **✓ DO** Zgłoś błędy wykonania przez zgłaszanie wyjątków.  
  
 **✓ CONSIDER** Trwa kończenie procesu przez wywołanie metody `System.Environment.FailFast` (funkcja .NET Framework 2.0) zamiast generowania wyjątku, jeśli kod napotkał sytuacji, gdy jest niebezpieczny dla dalszego wykonywania.  
  
 **X DO NOT** Użyj wyjątki dla przepływu sterowania, jeśli to możliwe.  
  
 Z wyjątkiem awarie systemu i operacji o potencjalnych sytuacji wyścigu projektantów framework należy projektować interfejsy API, dzięki czemu użytkownicy można napisać kod, który nie generuje wyjątków. Na przykład można podać sposób, aby sprawdzić warunki wstępne, przed wywołaniem członka, dzięki czemu użytkownicy można napisać kod, który nie generuje wyjątków.  
  
 Należy używać do sprawdzania warunków wstępnych innego członka jest często nazywany tester i nosi nazwę składowej, która faktycznie działa doer.  
  
 Istnieją przypadki, gdy wzorzec Tester Doer może mieć zmniejszenie wydajności nie do przyjęcia. W takiej sytuacji należy rozważyć tak zwane wzorzec analizy spróbuj (zobacz [wyjątki i wydajność](../../../docs/standard/design-guidelines/exceptions-and-performance.md) Aby uzyskać więcej informacji).  
  
 **✓ CONSIDER** skutki wydajności zgłaszanie wyjątków. Stawki throw powyżej 100 na sekundę mogą znacznie wpłynąć na wydajność większości aplikacji.  
  
 **✓ DO** dokumentu wszystkie wyjątki zgłaszane przez członków publicznie można wywołać z powodu naruszenia elementu członkowskiego kontraktu (zamiast awarii systemu) i je traktować jako część Umowy.  
  
 Wyjątki, które są częścią kontraktu nie należy zmieniać z jednej wersji do następnego (czyli nie należy zmieniać typ wyjątku i nie należy dodawać nowych wyjątków).  
  
 **X DO NOT** ma publicznych członków, których można albo throw lub nie na podstawie niektórych opcji.  
  
 **X DO NOT** ma publicznych elementów członkowskich, które zwracają wyjątki jako wartości zwracane lub `out` parametru.  
  
 Zwracanie wyjątków z publicznych interfejsów API, zamiast zgłaszać ich unieważnia wiele korzyści zapewnianych przez raportowanie błędów opartą na wyjątkach.  
  
 **✓ CONSIDER** za pomocą metody konstruktora wyjątku.  
  
 Jest wspólne dla tego samego wyjątku z różnych miejsc. Aby uniknąć rozrostu kodu, należy używać metod pomocników, tworzyć wyjątki, które inicjuje ich właściwości.  
  
 Ponadto nie pojawiają się elementy członkowskie, które zgłaszają wyjątki śródwierszowych. Przenoszenie instrukcji "throw" w Konstruktorze może umożliwić elementu członkowskiego był śródwierszowy.  
  
 **X DO NOT** zgłaszanie wyjątków z bloki filtru wyjątków.  
  
 Gdy filtra wyjątku zgłasza wyjątek, wyjątek przez środowisko CLR i filtr zwraca wartość false. To zachowanie jest nie do odróżnienia od filtrowania, wykonywanie i zwrócenie wartości false jawnie i dlatego jest bardzo trudno debugować.  
  
 **X AVOID** jawne zgłaszanie wyjątków z bloki finally. Akceptowane są niejawnie zgłoszenia wyjątku, wynikające z wywołania metody, które generują.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
- [Wyjątki — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/exceptions.md)

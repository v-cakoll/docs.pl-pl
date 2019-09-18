---
title: loaderLock MDA
ms.date: 03/30/2017
helpviewer_keywords:
- deadlocks [.NET Framework]
- LoaderLock MDA
- MDAs (managed debugging assistants), loader locks
- managed debugging assistants (MDAs), loader locks
- operating system loader locks
- loader locks
- locks, threads
ms.assetid: 8c10fa02-1b9c-4be5-ab03-451d943ac1ee
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3e8769ec972ec76d04d2f22368fdde99de9c6de
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052544"
---
# <a name="loaderlock-mda"></a>loaderLock MDA
Asystent `loaderLock` debugowania zarządzanego (MDA) wykrywa próby wykonania kodu zarządzanego w wątku, który zawiera blokadę modułu ładującego systemu operacyjnego Microsoft Windows.  Wszelkie takie wykonywanie jest niedozwolone, ponieważ może prowadzić do zakleszczenia i korzystania z bibliotek DLL przed ich zainicjowaniem przez moduł ładujący systemu operacyjnego.  
  
## <a name="symptoms"></a>Symptomy  
 Najbardziej typowym błędem podczas wykonywania kodu wewnątrz blokady modułu ładującego systemu operacyjnego jest to, że wątki będą zakleszczony podczas próby wywołania innych funkcji Win32, które również wymagają blokady modułu ładującego.  Przykładami takich funkcji są `LoadLibrary` `FreeLibrary`, `GetProcAddress`,, i `GetModuleHandle`.  Aplikacja może nie wywoływać bezpośrednio tych funkcji; środowisko uruchomieniowe języka wspólnego (CLR) może wywoływać te funkcje w wyniku wywołania wyższego poziomu, <xref:System.Reflection.Assembly.Load%2A> takiego jak lub pierwszego wywołania metody wywołania platformy.  
  
 Zakleszczenie mogą również wystąpić, jeśli wątek oczekuje na uruchomienie lub zakończenie innego wątku.  Gdy wątek zostanie uruchomiony lub zakończy wykonywanie, musi uzyskać blokadę modułu ładującego systemu operacyjnego, aby dostarczyć zdarzenia do bibliotek DLL, których to dotyczy.  
  
 Na koniec istnieją przypadki, w których mogą wystąpić wywołania bibliotek DLL, zanim te biblioteki DLL zostały prawidłowo zainicjowane przez program ładujący systemu operacyjnego.  W przeciwieństwie do błędów zakleszczenia, które można zdiagnozować, sprawdzając stosy wszystkich wątków związanych z zakleszczeniem, trudno jest zdiagnozować użycie niezainicjowanych bibliotek DLL bez użycia tego MDA.  
  
## <a name="cause"></a>Przyczyna  
 Mieszane zestawy zarządzane/ C++ niezarządzane skompilowane dla .NET Framework wersji 1,0 lub 1,1 zazwyczaj próbują wykonać kod zarządzany wewnątrz blokady modułu ładującego, chyba że zostanie podjęta specjalna opieka, na przykład łączenie z **/NOENTRY**.
  
 Mieszane zestawy zarządzane/ C++ niezarządzane skompilowane dla .NET Framework w wersji 2,0 są mniej podatne na te problemy, co zmniejsza ryzyko związane z aplikacjami korzystającymi z niezarządzanych bibliotek DLL, które naruszają reguły systemu operacyjnego.  Na przykład, jeśli niezarządzany punkt `DllMain` wejścia biblioteki DLL `CoCreateInstance` wywołuje obiekt zarządzany, który został ujawniony w modelu COM, wynikiem jest próba wykonania kodu zarządzanego wewnątrz blokady modułu ładującego. Aby uzyskać więcej informacji na temat problemów z blokadą modułu ładującego w .NET Framework w wersji 2,0 lub nowszej, zobacz [Inicjowanie zestawów mieszanych](/cpp/dotnet/initialization-of-mixed-assemblies).  
  
## <a name="resolution"></a>Rozwiązanie  
 W programie C++ Visual .NET 2002 i C++ Visual .NET 2003 biblioteki DLL `/clr` skompilowane z opcją kompilatora mogły być niezadeterministyczne zakleszczenie po załadowaniu; ten problem został wywołany przez mieszany plik DLL ładowania lub blokady modułu ładującego. W programie C++ Visual 2005 i nowszych prawie wszystkie inne niż jej ustalenia zostały usunięte z procesu ładowania mieszanej biblioteki DLL. Istnieje jednak kilka pozostałych scenariuszy, dla których zablokowanie modułu ładującego może być (deterministycznie). Aby zapoznać się ze szczegółowymi informacjami na temat przyczyn i rozwiązań dla pozostałych problemów z blokadą modułu ładującego, zobacz [Inicjowanie zestawów mieszanych](/cpp/dotnet/initialization-of-mixed-assemblies). Jeśli ten temat nie identyfikuje problemu blokady modułu ładującego, należy sprawdzić stos wątku, aby określić, dlaczego występuje blokada modułu ładującego i jak rozwiązać problem. Przyjrzyj się śladowi stosu dla wątku, który aktywuje to MDA.  Wątek podejmuje próbę niedozwolonego wywołania kodu zarządzanego podczas utrzymywania blokady modułu ładującego systemu operacyjnego.  Prawdopodobnie na stosie zobaczysz `DllMain` lub równoważny punkt wejścia biblioteki DLL.  Reguły systemu operacyjnego, dla których można legalnie wykonywać w tym punkcie wejścia, są dość ograniczone.  Te reguły nie wykluczają żadnego zarządzanego wykonania.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Zazwyczaj kilka wątków w procesie zostanie zakleszczenie.  Jeden z tych wątków prawdopodobnie jest wątkiem odpowiedzialnym za wykonywanie wyrzucania elementów bezużytecznych, więc to zakleszczenie może mieć istotny wpływ na cały proces.  Ponadto uniemożliwią one wykonywanie dodatkowych operacji wymagających blokady modułu ładującego systemu operacyjnego, takich jak ładowanie i zwalnianie zestawów lub bibliotek DLL oraz uruchamianie lub zatrzymywanie wątków.  
  
 W niektórych nietypowych przypadkach możliwe jest również naruszenie zasad dostępu lub podobne problemy, które mogą zostać wyzwolone w bibliotekach DLL, które są wywoływane przed zainicjowaniem.  
  
## <a name="output"></a>Dane wyjściowe  
 To zdarzenie MDA zgłasza, że podjęto próbę wykonania niedozwolonego zarządzanego wykonania.  Należy sprawdzić stos wątku, aby określić, dlaczego występuje blokada modułu ładującego i jak rozwiązać problem.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loaderLock/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)

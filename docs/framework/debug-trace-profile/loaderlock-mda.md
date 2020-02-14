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
ms.openlocfilehash: cd77640a6566f3fd94631dac184ae5bc3ffab5d1
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217351"
---
# <a name="loaderlock-mda"></a>loaderLock MDA
Asystent debugowania zarządzanego `loaderLock` (MDA) wykrywa próby wykonania kodu zarządzanego w wątku, który zawiera blokadę modułu ładującego systemu operacyjnego Microsoft Windows.  Wszelkie takie wykonywanie jest niedozwolone, ponieważ może prowadzić do zakleszczenia i korzystania z bibliotek DLL przed ich zainicjowaniem przez moduł ładujący systemu operacyjnego.  
  
## <a name="symptoms"></a>Objawy  
 Najbardziej typowym błędem podczas wykonywania kodu wewnątrz blokady modułu ładującego systemu operacyjnego jest to, że wątki będą zakleszczony podczas próby wywołania innych funkcji Win32, które również wymagają blokady modułu ładującego.  Przykłady takich funkcji to `LoadLibrary`, `GetProcAddress`, `FreeLibrary`i `GetModuleHandle`.  Aplikacja może nie wywoływać bezpośrednio tych funkcji; środowisko uruchomieniowe języka wspólnego (CLR) może wywoływać te funkcje w wyniku wywołania wyższego poziomu, takiego jak <xref:System.Reflection.Assembly.Load%2A> lub pierwszego wywołania metody wywołania platformy.  
  
 Zakleszczenie mogą również wystąpić, jeśli wątek oczekuje na uruchomienie lub zakończenie innego wątku.  Gdy wątek zostanie uruchomiony lub zakończy wykonywanie, musi uzyskać blokadę modułu ładującego systemu operacyjnego, aby dostarczyć zdarzenia do bibliotek DLL, których to dotyczy.  
  
 Na koniec istnieją przypadki, w których mogą wystąpić wywołania bibliotek DLL, zanim te biblioteki DLL zostały prawidłowo zainicjowane przez program ładujący systemu operacyjnego.  W przeciwieństwie do błędów zakleszczenia, które można zdiagnozować, sprawdzając stosy wszystkich wątków związanych z zakleszczeniem, trudno jest zdiagnozować użycie niezainicjowanych bibliotek DLL bez użycia tego MDA.  
  
## <a name="cause"></a>Przyczyna  
 Mieszane zestawy zarządzane/ C++ niezarządzane skompilowane dla .NET Framework wersji 1,0 lub 1,1 zazwyczaj próbują wykonać kod zarządzany wewnątrz blokady modułu ładującego, chyba że zostanie podjęta specjalna opieka, na przykład łączenie z **/NOENTRY**.
  
 Mieszane zestawy zarządzane/ C++ niezarządzane skompilowane dla .NET Framework w wersji 2,0 są mniej podatne na te problemy, co zmniejsza ryzyko związane z aplikacjami korzystającymi z niezarządzanych bibliotek DLL, które naruszają reguły systemu operacyjnego.  Na przykład, jeśli niezarządzana biblioteka DLL `DllMain` wywołań punktu wejścia `CoCreateInstance`, aby uzyskać zarządzany obiekt, który został uwidoczniony w modelu COM, wynikiem jest próba wykonania kodu zarządzanego wewnątrz blokady modułu ładującego. Aby uzyskać więcej informacji na temat problemów z blokadą modułu ładującego w .NET Framework w wersji 2,0 lub nowszej, zobacz [Inicjowanie zestawów mieszanych](/cpp/dotnet/initialization-of-mixed-assemblies).  
  
## <a name="resolution"></a>Rozwiązanie  
 W programie C++ visual .NET 2002 i C++ Visual .NET 2003 biblioteki DLL skompilowane z opcją kompilatora `/clr` mogą być niedeterministyczne zakleszczenie po załadowaniu; Ten problem został wywołany przez błąd ładowania lub blokady programu ładującego biblioteki DLL. W programie C++ Visual 2005 i nowszych prawie wszystkie inne niż jej ustalenia zostały usunięte z procesu ładowania mieszanej biblioteki DLL. Istnieje jednak kilka pozostałych scenariuszy, dla których zablokowanie modułu ładującego może być (deterministycznie). Aby zapoznać się ze szczegółowymi informacjami na temat przyczyn i rozwiązań dla pozostałych problemów z blokadą modułu ładującego, zobacz [Inicjowanie zestawów mieszanych](/cpp/dotnet/initialization-of-mixed-assemblies). Jeśli ten temat nie identyfikuje problemu blokady modułu ładującego, należy sprawdzić stos wątku, aby określić, dlaczego występuje blokada modułu ładującego i jak rozwiązać problem. Przyjrzyj się śladowi stosu dla wątku, który aktywuje to MDA.  Wątek podejmuje próbę niedozwolonego wywołania kodu zarządzanego podczas utrzymywania blokady modułu ładującego systemu operacyjnego.  Prawdopodobnie na stosie zostanie wyświetlony `DllMain` lub odpowiedni punkt wejścia biblioteki DLL.  Reguły systemu operacyjnego, dla których można legalnie wykonywać w tym punkcie wejścia, są dość ograniczone.  Te reguły nie wykluczają żadnego zarządzanego wykonania.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)

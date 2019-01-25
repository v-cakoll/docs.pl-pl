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
ms.openlocfilehash: 1001777f00524f3a183e1641718b9d3121c94e66
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637940"
---
# <a name="loaderlock-mda"></a>loaderLock MDA
`loaderLock` Zarządzanego Asystenta debugowania (MDA) wykrywa próby wykonania kodu zarządzanego w wątku, który posiada blokady modułu ładującego systemu operacyjnego Microsoft Windows.  Takiego wykonania jest niedozwolona, ponieważ może to prowadzić do zakleszczenia i korzystanie z biblioteki dll, zanim zostały zainicjowane przez program ładujący systemu operacyjnego.  
  
## <a name="symptoms"></a>Symptomy  
 Najbardziej typowych błędów podczas wykonywania kodu wewnątrz blokady modułu ładującego systemu operacyjnego jest, że wątki będą zakleszczenie podczas próby wywołania innych funkcji Win32, które wymagają również blokady modułu ładującego.  Przykłady takich funkcji `LoadLibrary`, `GetProcAddress`, `FreeLibrary`, i `GetModuleHandle`.  Aplikacja nie może bezpośrednio wywołać te funkcje; środowisko uruchomieniowe języka wspólnego (CLR) może wywołać te funkcje, w wyniku wyższe wywołania poziomu, takie jak <xref:System.Reflection.Assembly.Load%2A> lub pierwsze wywołanie platformę wywołania metody.  
  
 Zakleszczenie może również wystąpić, jeśli wątek oczekuje na inny wątek rozpoczęcia lub zakończenia.  Gdy wątku rozpoczyna się lub kończy wykonywanie, go uzyskać blokady modułu ładującego systemu operacyjnego do dostarczenia zdarzeń, do których to dotyczy bibliotek DLL.  
  
 Ponadto istnieją przypadki, w których może wystąpić wywołania do biblioteki dll, zanim tych bibliotek DLL zostały poprawnie zainicjowane przez program ładujący systemu operacyjnego.  Inaczej niż w przypadku awarii zakleszczenia, których można zdiagnozować, sprawdzając stosów wszystkich wątków, związane z zakleszczaniem, jest bardzo trudne do zdiagnozowania użycie niezainicjowanej bibliotek DLL, bez korzystania z tego MDA.  
  
## <a name="cause"></a>Przyczyna  
 Zarządzanych/niezarządzanych C++ zestawy mieszane stworzona z myślą o wersji programu .NET Framework 1.0 i 1.1, zazwyczaj próba wykonania kodu zarządzanego wewnątrz blokady modułu ładującego, chyba że specjalne jest zajęty, na przykład, łączenie za pomocą **/noentry**.
  
 Zarządzanych/niezarządzanych C++ zestawów mieszanych stworzona z myślą o .NET Framework w wersji 2.0 są mniej podatne na te problemy mające zmniejszenie ryzyka, podobnie jak aplikacje przy użyciu niezarządzanych bibliotek DLL, które naruszają reguły systemu operacyjnego.  Na przykład, jeśli niezarządzane DLL `DllMain` wywołania punktu wejścia `CoCreateInstance` można uzyskać obiektu zarządzanego, która została udostępniona modelowi COM, wynik jest próba wykonania kodu zarządzanego wewnątrz blokady modułu ładującego. Aby uzyskać więcej informacji na temat problemów blokady modułu ładującego .NET Framework w wersji 2.0 lub nowszej, zobacz [inicjowanie zestawów mieszanych](/cpp/dotnet/initialization-of-mixed-assemblies).  
  
## <a name="resolution"></a>Rozwiązanie  
 W Visual C++ .NET 2002 i Visual C++ .NET 2003 biblioteki DLL skompilowany przy użyciu `/clr` — opcja kompilatora niejednoznaczny można zakleszczenie podczas ładowania; ten problem został wywołany mieszane problem DLL ładowania lub modułu ładującego blokady. W programie Visual C++ 2005 i nowszych prawie wszystkie niedeterminizmu został usunięty z mieszanych bibliotek DLL, proces ładowania. Istnieje jednak kilka pozostałe scenariusze, dla których moduł ładujący blokady (sposób deterministyczny) jest możliwe. Aby uzyskać szczegółowe zestawienie przyczynami i rozwiązaniami w przypadku pozostałych problemów blokady modułu ładującego, zobacz [inicjowanie zestawów mieszanych](/cpp/dotnet/initialization-of-mixed-assemblies). Ten temat nie wskazuje na problem blokady modułu ładującego, należy zbadać stosu wątku w celu ustalenia, dlaczego występuje blokady modułu ładującego i jak rozwiązać ten problem. Przyjrzyj się ślad stosu dla wątku, który uaktywnił to zdarzenie MDA.  Wątek podejmuje próbę nielegalnego mogą wywoływać kodu zarządzanego podczas utrzymywania blokady modułu ładującego systemu operacyjnego.  Widoczne będą prawdopodobnie bibliotekę DLL `DllMain` lub równoważne wpis punktu na stosie.  Zasady systemu operacyjnego zgodnie z prawem jak od wewnątrz punkt wejścia są bardzo ograniczona.  Te zasady uniemożliwiają dowolnego zarządzanego wykonania.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Zazwyczaj będzie zakleszczenie kilku wątków wewnątrz procesu.  Jeden z tych wątków prawdopodobnie będzie odpowiedzialny za wykonanie wyrzucania elementów bezużytecznych, więc ten zakleszczeń może mieć istotny wpływ na cały proces wątku.  Ponadto uniemożliwi dodatkowych operacji, które wymagają blokady modułu ładującego systemu operacyjnego, takich jak ładowanie i zwalnianie zestawów i bibliotek DLL i uruchamianie lub zatrzymywanie wątków.  
  
 W niektórych przypadkach nietypowe użytkownik może również dla naruszenia zasad dostępu lub podobne problemy w bibliotekach DLL, które są wywoływane przed zostały zainicjowane.  
  
## <a name="output"></a>Dane wyjściowe  
 To zdarzenie MDA zgłasza, że niedozwolony zarządzanego wykonania podjęto próbę.  Należy sprawdzić stosu wątku w celu ustalenia, dlaczego występuje blokady modułu ładującego i jak rozwiązać ten problem.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loaderLock/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

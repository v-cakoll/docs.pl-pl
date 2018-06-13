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
ms.openlocfilehash: dbc6cc814d23923f01eceea70bd2fe45b9cbff8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388202"
---
# <a name="loaderlock-mda"></a>loaderLock MDA
`loaderLock` Zarządzany Asystent debugowania (MDA) wykrywa próby wykonania kodu zarządzanego w wątku, który posiada blokady modułu ładującego systemu operacyjnego Microsoft Windows.  Takie wykonanie jest niedozwolona, ponieważ może to prowadzić do zakleszczenia i korzystanie z bibliotek DLL, zanim zostały zainicjowane przez modułu ładującego systemu operacyjnego.  
  
## <a name="symptoms"></a>Symptomy  
 Najczęściej błędu podczas wykonywania kodu wewnątrz blokady modułu ładującego systemu operacyjnego jest, że wątki będą zakleszczenie podczas próby wywołania innych funkcji Win32, wymagających blokady modułu ładującego.  Przykłady takich funkcji `LoadLibrary`, `GetProcAddress`, `FreeLibrary`, i `GetModuleHandle`.  Aplikacja nie może bezpośrednio wywoływać te funkcje; środowisko uruchomieniowe języka wspólnego (CLR) może wywoływać te funkcje w wyniku wyższy poziom wywołania jak <xref:System.Reflection.Assembly.Load%2A> lub w pierwszym wywołaniu platformy wywołania metody.  
  
 Zakleszczenie może również wystąpić, jeśli wątek oczekuje na inny wątek rozpoczęcia lub zakończenia.  Gdy wątek rozpoczyna się lub kończy wykonywanie, jego muszą uzyskać blokady modułu ładującego systemu operacyjnego na potrzeby dostarczania zdarzeń do odpowiednich bibliotek DLL.  
  
 Na koniec istnieją przypadki, w którym mogą wystąpić wywołania do biblioteki dll, zanim te biblioteki DLL została poprawnie zainicjowana przez moduł ładujący systemu operacyjnego.  W przeciwieństwie do błędów zakleszczenia, które można zdiagnozować, sprawdzając stosy wątków objętego zakleszczenia, jest bardzo trudne do diagnozowania Użyj niezainicjowanego dll bez użycia tego MDA.  
  
## <a name="cause"></a>Przyczyna  
 Mieszane zarządzanych/niezarządzanych C++ zestawy przeznaczony dla wersji systemu .NET Framework w wersji 1.0 lub 1.1 zazwyczaj próba wykonania kodu zarządzanego wewnątrz blokady modułu ładującego, chyba że szczególną zostanie podjęta, na przykład łączenie z **/noentry**.
  
 Zarządzanych/niezarządzanych C++ zestawów mieszanych skompilowany dla platformy .NET Framework w wersji 2.0 są mniej podatny na te problemy o zmniejszenie ryzyka, podobnie jak aplikacje przy użyciu niezarządzanych bibliotek DLL, które naruszają zasady systemu operacyjnego.  Na przykład, jeśli niezarządzanej DLL `DllMain` wywołania punktu wejścia `CoCreateInstance` uzyskać zarządzanego obiektu, który został ujawniony dla modelu COM, wynikiem jest próba wykonania kodu zarządzanego wewnątrz blokady modułu ładującego. Aby uzyskać więcej informacji dotyczących problemów blokady modułu ładującego w programie .NET Framework w wersji 2.0 lub nowszej, zobacz [inicjowanie zestawów mieszanych](/cpp/dotnet/initialization-of-mixed-assemblies).  
  
## <a name="resolution"></a>Rozwiązanie  
 W programie Visual C++ .NET 2002 i Visual C++ .NET 2003 biblioteki DLL są kompilowane przy użyciu `/clr` — opcja kompilatora można w sposób niejednoznaczny zakleszczenie po załadowaniu; ten problem został wywołany mieszanych problem DLL ładowania lub modułu ładującego blokady. W programie Visual C++ 2005 lub nowszego oraz prawie wszystkie z systemem innym niż determinizm została usunięta z mieszanym proces ładowania biblioteki DLL. Istnieje jednak kilka pozostałych scenariusze, dla których moduł ładujący (sposób niejednoznaczny) może wystąpić blokady. Aby uzyskać szczegóły konta z przyczynami i rozwiązaniami w przypadku pozostałych problemów blokady modułu ładującego, zobacz [inicjowanie zestawów mieszanych](/cpp/dotnet/initialization-of-mixed-assemblies). Ten temat nie wskazuje na problem blokady modułu ładującego, należy zbadać stosu wątku w celu ustalenia, dlaczego występuje blokady modułu ładującego i sposobu rozwiązania problemu. Sprawdź ślad stosu wątku, który został aktywowany to zdarzenie MDA.  Wątek próbuje nielegalnego wywołania wewnątrz kodu zarządzanego podczas utrzymywania blokady modułu ładującego systemu operacyjnego.  Prawdopodobnie zobaczysz bibliotekę DLL `DllMain` lub równoważne wpisu punktu na stosie.  Zasady systemu operacyjnego legalnie jak z wewnątrz punkt wejścia są bardzo ograniczone.  Te zasady uniemożliwiają wszelkie wykonania kodu zarządzanego.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Zazwyczaj kilka wątków wewnątrz procesu zostanie zakleszczenie.  Jeden z tych wątków prawdopodobnie będzie odpowiedzialny za wykonywanie wyrzucania elementów bezużytecznych, więc tego zakleszczenia może mieć istotny wpływ na cały proces wątku.  Ponadto uniemożliwi dodatkowe operacje, które wymagają blokady modułu ładującego systemu operacyjnego, takich jak ładowanie i zwalnianie zestawów lub biblioteki dll i uruchamianie lub zatrzymywanie wątków.  
  
 W niektórych przypadkach nietypowe istnieje również możliwość naruszenia zasad dostępu lub podobnych problemów w bibliotek DLL, które są nazywane przed zostały zainicjowane.  
  
## <a name="output"></a>Dane wyjściowe  
 To zdarzenie MDA zgłasza, że niedozwolony zarządzanego wykonania podjęto próbę.  Należy zbadać stosu wątku w celu ustalenia, dlaczego występuje blokady modułu ładującego i sposobu rozwiązania problemu.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loaderLock/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)

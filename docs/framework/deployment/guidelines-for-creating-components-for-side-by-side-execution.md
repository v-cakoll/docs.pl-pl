---
title: Wytyczne dotyczące tworzenia składników pod kątem wykonywania równoczesnego
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf7e1b0c3ef3c1e1c26e4dd308ae2326777b38da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625860"
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a>Wytyczne dotyczące tworzenia składników pod kątem wykonywania równoczesnego
Wykonaj te ogólne wytyczne do tworzenia aplikacji zarządzanych lub składników przeznaczonych do wykonywania side-by-side:  
  
-   Typ tożsamości należy powiązać z określoną wersję pliku.  
  
     Środowisko uruchomieniowe języka wspólnego wiąże tożsamość typ wersji danego pliku przy użyciu zestawów o silnych nazwach. Aby utworzyć aplikację lub składnik do wykonania side-by-side, musisz udzielić wszystkich zestawów silną nazwą. Umożliwia utworzenie tożsamości typu dokładne i zapewnia, że wszystkie rozwiązania typu jest kierowane do prawidłowego pliku. Zestawu z silną nazwą zawiera wersji, kultury i informacje o wydawcy, że środowisko wykonawcze używa do zlokalizowania odpowiedniego pliku do spełnienia żądania powiązania.  
  
-   Usługa storage rozpoznający wersje.  
  
     Środowisko wykonawcze używa globalnej pamięci podręcznej, aby zapewnić rozpoznający wersje magazynu. Global assembly cache to struktura katalogu rozpoznający wersje zainstalowane na każdym komputerze, który używa programu .NET Framework. Po zainstalowaniu nowej wersji tego zestawu, nie są zastępowane zainstalowanych w globalnej pamięci podręcznej zestawów.  
  
-   Utwórz aplikację lub składnik, który działa w izolacji.  
  
     Aplikacja lub składnik, który działa w izolacji muszą zarządzać zasobami w celu uniknięcia konfliktów, jeśli jednocześnie jest uruchomionych dwa wystąpienia aplikacji lub składnika. Aplikacja lub składnik należy również użyć struktury specyficzny dla wersji plików.  
  
## <a name="application-and-component-isolation"></a>Aplikacji i składników izolacji  
 Jeden klucz do pomyślnie projektowania aplikacji lub składnika do wykonania side-by-side jest izolacji. Aplikacja lub składnik musi zarządzanie wszystkimi zasobami, szczególnie plików we/wy, w sposób izolowany. Należy przestrzegać następujących wytycznych, aby upewnić się, że Twoja aplikacja lub składnik działa w izolacji:  
  
-   Wpisywanie do rejestru, w sposób specyficzny dla wersji. Store wartości w gałęzi lub klucze, które wskazują wersji i nie należy udostępniać informacje lub stan różnych wersji składnika. Zapobiega to dwie aplikacje lub składniki działające w tym samym czasie, informacje o zastępowaniu.  
  
-   Wprowadź nazwany jądra obiektów specyficznych dla wersji, tak aby sytuacji wyścigu, która nie występuje. Na przykład sytuacja wyścigu występuje, gdy dwa semaforów z dwie wersje tej samej aplikacji czekać na siebie nawzajem.  
  
-   Wprowadź nazwy plików i katalogów rozpoznający wersje. Oznacza to, że struktury pliku należy polegać na informacje o wersji.  
  
-   Tworzenie kont użytkowników i grup w sposób specyficzny dla wersji. Konta użytkowników i grup utworzonych przez aplikację, powinny być określone przez wersję. Nie należy udostępniać konta użytkowników i grupy między wersjami aplikacji.  
  
## <a name="installing-and-uninstalling-versions"></a>Instalowanie i odinstalowywanie wersji  
 Podczas projektowania aplikacji do wykonywania side-by-side, wykonaj te wytyczne dotyczące instalowania i odinstalowywania wersji:  
  
-   Nie należy usuwać informacji z rejestru, który może być wymagany przez inne aplikacje uruchomione w innej wersji programu .NET Framework.  
  
-   Nie należy wymieniać informacje w rejestrze, który może być wymagany przez inne aplikacje uruchomione w innej wersji programu .NET Framework.  
  
-   Nie wyrejestrować składników COM, które mogą być potrzebne przez inne aplikacje uruchomione w innej wersji programu .NET Framework.  
  
-   Nie zmieniaj **InprocServer32** lub inne wpisy rejestru dotyczące serwera COM, który został już zarejestrowany.  
  
-   Nie należy usuwać konta użytkowników lub grupy, które mogą być potrzebne przez inne aplikacje uruchomione w innej wersji programu .NET Framework.  
  
-   Nie należy dodawać żadnych w rejestrze, który zawiera ścieżkę wycofanie.  
  
## <a name="file-version-number-and-assembly-version-number"></a>Numer wersji pliku i numer wersji zestawu  
 Wersja pliku jest zasób wersji Win32, który nie jest używany w czasie wykonywania. Ogólnie rzecz biorąc należy zaktualizować wersję pliku, nawet w przypadku aktualizację w miejscu. Dwie identyczne pliki mogą zawierać informacje o wersji inny plik i dwóch różnych plikach może mieć te same informacje o wersji pliku.  
  
 Wersja zestawu jest używana przez środowisko uruchomieniowe dla powiązań zestawów. Dwa identyczne zestawy za pomocą różnych numerów wersji, są traktowane jako dwa różne zestawy w czasie wykonywania.  
  
 [Narzędzia Globalna pamięć podręczna zestawów (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) pozwala zastąpić zestawu, jeśli numer wersji pliku jest nowsza. Instalator ogólnie nie można zainstalować za pośrednictwem zestawu, chyba że numer wersji zestawu jest większa.  
  
## <a name="see-also"></a>Zobacz także
- [Wykonywanie równoczesne](../../../docs/framework/deployment/side-by-side-execution.md)
- [Instrukcje: Włączanie i wyłączanie automatycznego przekierowania powiązań](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)

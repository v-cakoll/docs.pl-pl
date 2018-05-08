---
title: Wytyczne dotyczące tworzenia składników pod kątem wykonywania równoczesnego
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f45e68d9d340d857bc25b3848bd687e46fd73c52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a>Wytyczne dotyczące tworzenia składników pod kątem wykonywania równoczesnego
Wykonaj te ogólne wytyczne, aby utworzyć aplikacje zarządzane lub składniki przeznaczone do wykonywania side-by-side:  
  
-   Typ tożsamości należy powiązać określonej wersji pliku.  
  
     Środowisko uruchomieniowe języka wspólnego wiąże tożsamość typu wersja określonego pliku przy użyciu zestawów o silnych nazwach. Aby utworzyć aplikację lub składnik do wykonania side-by-side, należy podać wszystkie zestawy silnej nazwy. Tworzy tożsamość dokładny typ oraz zapewnia, że wszelkie rozpoznawania typu jest kierowane do poprawnego pliku. Zestaw o silnej nazwie zawiera wersję, kulturę i informacje o wydawcy używający środowiska uruchomieniowego można znaleźć poprawnego pliku do spełnienia żądania powiązania.  
  
-   Użyj obsługujący wersji magazynu.  
  
     Środowisko uruchomieniowe używa globalnej pamięci podręcznej zestawów, aby zapewnić obsługujący wersji magazynu. Globalna pamięć podręczna zestawów to struktura obsługująca wersji katalogu zainstalowane na każdym komputerze, który używa programu .NET Framework. Zestawy zainstalowany w globalnej pamięci podręcznej zestawów nie zostaną zastąpione po zainstalowaniu nowej wersji tego zestawu.  
  
-   Utwórz aplikację lub składnik, który jest uruchamiany w izolacji.  
  
     Aplikacja lub składnik, który jest uruchamiany w izolacji muszą zarządzać zasobów, aby uniknąć konfliktów, jeśli dwa wystąpienia aplikacji lub składnika jest uruchomionych jednocześnie. Aplikacja lub składnik również użyć struktury określonej wersji pliku.  
  
## <a name="application-and-component-isolation"></a>Aplikacji i izolacji składnika  
 Jeden klucz pomyślnie projektowania aplikacji lub składnika w celu wykonywania side-by-side jest izolacji. Aplikacja lub składnik musi zarządzać wszystkie zasoby, we/wy, szczególnie dla plików w sposób izolowany. Skorzystaj z następujących wskazówek, aby upewnić się, że aplikacja lub składnik jest uruchamiany w izolacji:  
  
-   Zapisywanie w rejestrze w sposób określonej wersji. Przechowywanie wartości w gałęzi lub klucze, które wskazują wersji i nie udostępniaj informacje lub stan między wersjami składnika. Zapobiega to dwie aplikacje lub składniki działające w tym samym czasie zastępowaniu informacji.  
  
-   Wprowadź obiektów o nazwie jądra określonej wersji, tak aby nie występuje sytuacja wyścigu. Na przykład sytuacja wyścigu występuje, gdy dwie semaforów z dwie wersje tej samej aplikacji, poczekaj na siebie.  
  
-   Należy obsługujący wersji nazw plików i katalogów. Oznacza to, że plik struktury polegać na informacje o wersji.  
  
-   Utworzenie kont użytkowników i grup w sposób określonej wersji. Konta użytkowników i grup utworzonych przez aplikację powinny zostać zidentyfikowane na podstawie wersji. Nie udostępniaj kont użytkowników i grup między wersjami aplikacji.  
  
## <a name="installing-and-uninstalling-versions"></a>Instalowanie i odinstalowywanie wersji  
 Podczas projektowania aplikacji do wykonania side-by-side, skorzystaj z następujących wskazówek dotyczących instalowania i odinstalowywania wersji:  
  
-   Nie należy usuwać informacji z rejestru, który może być wymagany przez inne aplikacje uruchomione w innej wersji programu .NET Framework.  
  
-   Nie zastępuj informacje w rejestrze, który może być wymagany przez inne aplikacje uruchomione w innej wersji programu .NET Framework.  
  
-   Nie wyrejestrować składników COM, które mogą być wymagane przez inne aplikacje uruchomione w innej wersji programu .NET Framework.  
  
-   Nie zmieniaj **InprocServer32** lub inne wpisy rejestru dotyczące serwera COM, który został już zarejestrowany.  
  
-   Nie należy usuwać konta użytkowników lub grupy, które mogą być wymagane przez inne aplikacje uruchomione w innej wersji programu .NET Framework.  
  
-   Nie dodawaj żadnych czynności w rejestrze, który zawiera ścieżkę wycofanie.  
  
## <a name="file-version-number-and-assembly-version-number"></a>Numer wersji pliku i numer wersji zestawu  
 Wersja pliku jest zasób wersji Win32, który nie jest używany w czasie wykonywania. Ogólnie rzecz biorąc należy zaktualizować wersję pliku, nawet w przypadku aktualizacji w miejscu. Dwie identyczne pliki mogą mieć inny plik informacji o wersji, a dwóch różnych plików mogą mieć tej samej informacji o wersji pliku.  
  
 Wersja zestawu jest używana przez środowisko uruchomieniowe dla powiązań zestawów. Dwa identyczne zestawy za pomocą różnych numerów wersji są traktowane jako dwa różne zestawy w czasie wykonywania.  
  
 [Narzędzie Global Assembly Cache (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) pozwala zastąpić zestawu, gdy numer wersji pliku jest nowsza. Instalator zazwyczaj nie są instalowane za pośrednictwem zestawu chyba, że numer wersji zestawu jest większa.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykonywanie równoczesne](../../../docs/framework/deployment/side-by-side-execution.md)  
 [Instrukcje: włączanie i wyłączanie automatycznego przekierowania powiązań](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)

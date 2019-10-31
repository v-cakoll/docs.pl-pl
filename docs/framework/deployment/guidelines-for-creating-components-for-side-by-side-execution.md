---
title: Wytyczne dotyczące tworzenia składników pod kątem wykonywania równoczesnego
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
ms.openlocfilehash: 42d0e2d85517d4a8fb443db9b63e6b893267caca
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121589"
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a>Wytyczne dotyczące tworzenia składników pod kątem wykonywania równoczesnego
Postępuj zgodnie z tymi ogólnymi wskazówkami, aby utworzyć zarządzane aplikacje lub składniki przeznaczone do wykonywania równoczesnego:  
  
- Powiąż tożsamość typu z określoną wersją pliku.  
  
     Środowisko uruchomieniowe języka wspólnego wiąże tożsamość typu z określoną wersją pliku przy użyciu zestawów o silnych nazwach. Aby utworzyć aplikację lub składnik do wykonywania równoczesnego, należy nadać wszystkie zestawy silną nazwą. Spowoduje to utworzenie precyzyjnej tożsamości typu i gwarantuje, że wszystkie typy rozpoznawania są kierowane do właściwego pliku. Zestaw o silnej nazwie zawiera informacje o wersji, kulturze i wydawcy, które są używane przez środowisko uruchomieniowe do lokalizowania właściwego pliku w celu spełnienia żądania powiązania.  
  
- Użyj magazynu z obsługą wersji.  
  
     Środowisko uruchomieniowe używa globalnej pamięci podręcznej zestawów, aby zapewnić magazyn z obsługą wersji. Globalna pamięć podręczna zestawów to struktura katalogów oparta na wersji zainstalowana na każdym komputerze, który używa .NET Framework. Zestawy zainstalowane w globalnej pamięci podręcznej zestawów nie są zastępowane w przypadku zainstalowania nowej wersji tego zestawu.  
  
- Tworzenie aplikacji lub składnika, który działa w izolacji.  
  
     Aplikacja lub składnik działający w izolacji musi zarządzać zasobami, aby uniknąć konfliktów, gdy dwa wystąpienia aplikacji lub składnika działają jednocześnie. Aplikacja lub składnik musi również używać struktury plików specyficznej dla wersji.  
  
## <a name="application-and-component-isolation"></a>Izolacja aplikacji i składników  
 Jednym kluczem do pomyślnego zaprojektowania aplikacji lub składnika do wykonywania równoczesnego jest izolacja. Aplikacja lub składnik musi zarządzać wszystkimi zasobami, w szczególności we/wy plików, w sposób izolowany. Postępuj zgodnie z poniższymi wskazówkami, aby upewnić się, że aplikacja lub składnik działa w izolacji:  
  
- Zapisz w rejestrze w sposób specyficzny dla wersji. Przechowuj wartości w gałęziach lub kluczach, które wskazują wersję, i nie udostępniaj informacji lub stanu w różnych wersjach składnika. Zapobiega to zastępowaniu informacji przez dwie aplikacje lub składniki w tym samym czasie.  
  
- Ustaw nazwane obiekty jądra jako specyficzne dla konkretnej wersji, aby nie nastąpiła sytuacja wyścigu. Na przykład sytuacja wyścigu występuje, gdy dwa semafory z dwóch wersji tej samej aplikacji zaczekają na siebie.  
  
- Wprowadź nazwy plików i katalogów. Oznacza to, że struktury plików powinny opierać się na informacjach o wersji.  
  
- Tworzenie kont użytkowników i grup w sposób specyficzny dla danej wersji. Konta użytkowników i grupy utworzone przez aplikację powinny być identyfikowane według wersji. Nie należy udostępniać kont użytkowników i grup między wersjami aplikacji.  
  
## <a name="installing-and-uninstalling-versions"></a>Instalowanie i odinstalowywanie wersji  
 Podczas projektowania aplikacji do wykonywania równoczesnego postępuj zgodnie z poniższymi wskazówkami dotyczącymi instalowania i odinstalowywania wersji:  
  
- Nie usuwaj informacji z rejestru, które mogą być potrzebne innym aplikacjom działającym w innej wersji .NET Framework.  
  
- Nie zamieniaj informacji w rejestrze, które mogą być niewymagane przez inne aplikacje działające w ramach innej wersji .NET Framework.  
  
- Nie należy wyrejestrować składników modelu COM, które mogą być niewymagane przez inne aplikacje działające w ramach innej wersji .NET Framework.  
  
- Nie należy zmieniać **InprocServer32** ani innych wpisów rejestru dla serwera com, który został już zarejestrowany.  
  
- Nie należy usuwać kont użytkowników ani grup, które mogą być potrzebne innym aplikacjom działającym w innej wersji .NET Framework.  
  
- Nie dodawaj niczego do rejestru, który zawiera ścieżkę bez wersji.  
  
## <a name="file-version-number-and-assembly-version-number"></a>Numer wersji pliku i numer wersji zestawu  
 Wersja pliku jest zasobem wersji Win32, który nie jest używany przez środowisko uruchomieniowe. Ogólnie rzecz biorąc należy zaktualizować wersję pliku nawet dla aktualizacji w miejscu. Dwa identyczne pliki mogą mieć różne informacje o wersji pliku, a dwa różne pliki mogą mieć te same informacje o wersji pliku.  
  
 Wersja zestawu jest używana przez środowisko uruchomieniowe dla powiązania zestawu. Dwa identyczne zestawy o różnych numerach wersji są traktowane jak dwa różne zestawy w środowisku uruchomieniowym.  
  
 [Globalne narzędzie pamięci podręcznej zestawów (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) umożliwia zastąpienie zestawu, gdy tylko numer wersji pliku jest nowszy. Instalator zazwyczaj nie instaluje zestawu, chyba że numer wersji zestawu jest większy.  
  
## <a name="see-also"></a>Zobacz także

- [Wykonywanie równoczesne](side-by-side-execution.md)
- [Instrukcje: włączanie i wyłączanie automatycznego przekierowania powiązań](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)

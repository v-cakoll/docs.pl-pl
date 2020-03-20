---
title: Wytyczne dotyczące tworzenia składników pod kątem wykonywania równoczesnego
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, multiple application versions
- side-by-side execution, multiple component versions
ms.assetid: 5c540161-6e40-42e9-be92-6175aee2c46a
ms.openlocfilehash: 42d0e2d85517d4a8fb443db9b63e6b893267caca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121589"
---
# <a name="guidelines-for-creating-components-for-side-by-side-execution"></a>Wytyczne dotyczące tworzenia składników pod kątem wykonywania równoczesnego
Postępuj zgodnie z tymi ogólnymi wytycznymi, aby utworzyć aplikacje zarządzane lub składniki przeznaczone do wykonywania obok siebie:  
  
- Powiązanie tożsamości typu z określoną wersją pliku.  
  
     Środowisko wykonawcze języka wspólnego wiąże tożsamość typu z określoną wersją pliku przy użyciu zestawów o silnej nazwie. Aby utworzyć aplikację lub składnik do wykonywania obok siebie, należy nadać wszystkim zestawom silną nazwę. Tworzy to dokładną tożsamość typu i zapewnia, że wszelkie rozwiązania typu jest kierowany do prawidłowego pliku. Zestaw o silnej nazwie zawiera informacje o wersji, kulturze i wydawcy używane przez środowisko wykonawcze do lokalizowania poprawnego pliku w celu spełnienia żądania powiązania.  
  
- Użyj magazynu obsługującego wersję.  
  
     Środowisko wykonawcze używa globalnej pamięci podręcznej zestawu, aby zapewnić magazyn obsługujący wersję. Globalna pamięć podręczna zestawów jest strukturą katalogów z uwzględnieniem wersji zainstalowaną na każdym komputerze, który używa programu .NET Framework. Zestawy zainstalowane w globalnej pamięci podręcznej zestawów nie są zastępowane po zainstalowaniu nowej wersji tego zestawu.  
  
- Utwórz aplikację lub składnik, który działa w izolacji.  
  
     Aplikacja lub składnik, który działa w izolacji musi zarządzać zasobami, aby uniknąć konfliktów, gdy dwa wystąpienia aplikacji lub składnika są uruchomione jednocześnie. Aplikacja lub składnik musi również używać struktury plików specyficzne dla wersji.  
  
## <a name="application-and-component-isolation"></a>Izolacja aplikacji i komponentów  
 Jednym z kluczy do pomyślnego projektowania aplikacji lub składnika do wykonywania side-by-side jest izolacja. Aplikacja lub składnik musi zarządzać wszystkimi zasobami, w szczególności we/wy pliku, w sposób odosobniony. Postępuj zgodnie z tymi wskazówkami, aby upewnić się, że aplikacja lub składnik działa w izolacji:  
  
- Zapisz do rejestru w sposób specyficzny dla wersji. Przechowuj wartości w gałęzi lub klucze, które wskazują wersję i nie udostępniają informacji ani stanu w różnych wersjach składnika. Zapobiega to dwóch aplikacji lub składników uruchomionych w tym samym czasie z nadpisywania informacji.  
  
- Aby nazwane obiekty jądra specyficzne dla wersji, tak aby nie wystąpiła rasa. Na przykład sytuacji wyścigu występuje, gdy dwa semafory z dwóch wersji tej samej aplikacji czekać na siebie.  
  
- Uaświadknikj nazw plików i katalogów. Oznacza to, że struktury plików powinny opierać się na informacjach o wersji.  
  
- Tworzenie kont użytkowników i grup w sposób specyficzny dla wersji. Konta użytkowników i grupy utworzone przez aplikację powinny być identyfikowane przez wersję. Nie należy udostępniać kont użytkowników i grup między wersjami aplikacji.  
  
## <a name="installing-and-uninstalling-versions"></a>Instalowanie i odinstalowywanie wersji  
 Podczas projektowania aplikacji do wykonywania side-by-side, postępuj zgodnie z tymi wytycznymi dotyczącymi instalowania i odinstalowywania wersji:  
  
- Nie należy usuwać informacji z rejestru, które mogą być potrzebne innym aplikacjom działającym w innej wersji programu .NET Framework.  
  
- Nie należy zastępować informacji w rejestrze, które mogą być potrzebne innym aplikacjom działającym w innej wersji programu .NET Framework.  
  
- Nie należy wyrejestrowywać składników COM, które mogą być potrzebne innym aplikacjom działającym w innej wersji programu .NET Framework.  
  
- Nie należy zmieniać **inprocServer32** ani innych wpisów rejestru dla serwera COM, który był już zarejestrowany.  
  
- Nie należy usuwać kont użytkowników lub grup, które mogą być potrzebne innym aplikacjom działającym w innej wersji programu .NET Framework.  
  
- Nie należy dodawać niczego do rejestru, który zawiera ścieżkę niewersyjną.  
  
## <a name="file-version-number-and-assembly-version-number"></a>Numer wersji pliku i numer wersji zestawu  
 Wersja pliku jest zasobem wersji Win32, który nie jest używany przez środowisko wykonawcze. Ogólnie rzecz biorąc, można zaktualizować wersję pliku nawet dla aktualizacji w miejscu. Dwa identyczne pliki mogą mieć różne informacje o wersji pliku, a dwa różne pliki mogą mieć te same informacje o wersji pliku.  
  
 Wersja zestawu jest używana przez środowisko wykonawcze dla powiązania zestawu. Dwa identyczne zestawy z różnymi numerami wersji są traktowane jako dwa różne zestawy przez środowisko wykonawcze.  
  
 [Narzędzie Globalna pamięć podręczna zestawów (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) umożliwia zastąpienie złożenia, gdy tylko numer wersji pliku jest nowszy. Instalator zazwyczaj nie instaluje się za cały zestaw, chyba że numer wersji zestawu jest większy.  
  
## <a name="see-also"></a>Zobacz też

- [Wykonywanie równoczesne](side-by-side-execution.md)
- [Porady: włączanie i wyłączanie automatycznego przekierowania powiązań](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)

---
title: Praca z zestawami i globalną pamięcią podręczną zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, benefits
- ACLs [.NET Framework]
- GAC (global assembly cache), benefits
- access control lists [.NET Framework]
ms.assetid: 8a18e5c2-d41d-49ef-abcb-7c27e2469433
ms.openlocfilehash: 330555f907a5ee2ef9cfc11b0b5659a392c0dec7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119718"
---
# <a name="working-with-assemblies-and-the-global-assembly-cache"></a>Praca z zestawami i globalną pamięcią podręczną zestawów

Jeśli zestaw ma być współużytkowany przez kilka aplikacji, można go zainstalować w globalnej pamięci podręcznej zestawów. Każdy komputer z zainstalowanym środowiskiem uruchomieniowym języka wspólnego posiada tę pamięć podręczną kodu dla całego komputera. Globalna pamięć podręczna zestawów przechowuje zestawy specjalnie wyznaczonych do współużytkowania przez kilka aplikacji na komputerze. Aby zestaw można było zainstalować w globalnej pamięci podręcznej zestawów, musi mieć silną nazwę.  
  
> [!NOTE]
> Zestawy umieszczone w globalnej pamięci podręcznej zestawów muszą mieć taką samą nazwę zestawu i pliku (bez rozszerzenia pliku). Na przykład zestaw o nazwie myAssembly musi mieć nazwę pliku myAssembly.exe lub myAssembly.dll.  
  
Udostępnianie zestawów poprzez instalowanie ich w globalnej pamięci podręcznej zestawów należy stosować tylko w razie potrzeby. Ogólna wytyczna stanowi, iż zależności zestawów powinny pozostawać poufne, a zestawy należy umieszczać w katalogu aplikacji, chyba że współużytkowanie zestawu jest wyraźnie wymagane. Ponadto nie trzeba instalować zestawów w globalnej pamięci podręcznej zestawów, aby je udostępnić usłudze międzyoperacyjnej modelu COM lub kodowi niezarządzanemu.  
  
Istnieje kilka powodów, dla których instalowanie zestawu w globalnej pamięci podręcznej zestawów może się okazać konieczne:  
  
- Udostępniona lokalizacja.  
  
     Zestawy, które powinny być używane przez aplikacje, można umieścić w globalnej pamięci podręcznej zestawów. Jeśli na przykład wszystkie aplikacje powinny używać zestawu znajdującego się w globalnej pamięci podręcznej zestawów, do pliku Machine.config można dodać instrukcje zasad dotyczących wersji, które przekierowują odwołania do zestawu.  
  
- Bezpieczeństwo plików.  
  
     Administratorzy często chronią główny katalog systemowy przy użyciu listy kontroli dostępu (ACL), która decyduje o uprawnieniach zapisu i wykonywania. Ponieważ globalna pamięć podręczna zestawów jest instalowana w głównym katalogu systemowym, dziedziczy listę kontroli dostępu tego katalogu. Zaleca się, aby tylko użytkownicy z uprawnieniami administratora mogli usuwać pliki z globalnej pamięci podręcznej zestawów.  
  
- Przechowywanie wersji równoległych.  
  
     W globalnej pamięci podręcznej zestawów można przechowywać wiele kopii zestawów o takiej samej nazwie, ale różnych informacjach o wersji.  
  
- Dodatkowa lokalizacja wyszukiwania.  
  
     Środowisko uruchomieniowe języka wspólnego najpierw sprawdza globalną pamięć podręczną zestawów w poszukiwaniu zestawu, który pasuje do żądania o zestaw, a dopiero potem wykonuje sondowanie lub używa informacji o bazie kodu w pliku konfiguracji.  
  
 Istnieją też scenariusze, w których nie należy jawnie instalować zestawów w globalnej pamięci podręcznej zestawów. Umieszczenie w tej pamięci jednego z zestawów tworzących aplikację sprawi, że nie będzie już można zreplikować ani zainstalować aplikacji przy użyciu polecenia XCOPY kopiującego katalog aplikacji. W takim przypadku należy również przenieść zestaw do globalnej pamięci podręcznej zestawów.  
  
## <a name="in-this-section"></a>W tej sekcji  
[Instrukcje: instalowanie zestawu w pamięci Global Assembly Cache](install-assembly-into-gac.md)  
Opis sposobów instalowania zestawu w globalnej pamięci podręcznej zestawów.  
  
[Instrukcje: wyświetlanie zawartości pamięci Global Assembly Cache](how-to-view-the-contents-of-the-gac.md)  
Wyjaśnia, jak używać programu [Gacutil. exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) do wyświetlania zawartości globalnej pamięci podręcznej zestawów.  
  
[Instrukcje: usuwanie zestawu z pamięci Global Assembly Cache](how-to-remove-an-assembly-from-the-gac.md)  
Wyjaśnia, jak używać programu [Gacutil. exe (Global Assembly Cache Tool)](../tools/gacutil-exe-gac-tool.md) do usuwania zestawu z globalnej pamięci podręcznej zestawów.  
  
[Używanie obsługiwanych składników z pamięcią Global Assembly Cache](use-serviced-components-with-the-gac.md)  
Wyjaśnienie, dlaczego obsługiwane składniki (zarządzanie składniki modelu COM+) należy umieszczać w globalnej pamięci podręcznej zestawów.  
  
## <a name="related-sections"></a>Sekcje pokrewne  

[Tworzenie zestawów](../../standard/assembly/create.md)  
Omówienie procesu tworzenia zestawów.  
  
[Global Assembly Cache](gac.md)  
Opis globalnej pamięci podręcznej zestawów.  
  
[Instrukcje: wyświetlanie zawartości zestawu](../../standard/assembly/view-contents.md)  
Wyjaśnia, jak używać programu [Ildasm. exe (Il dezasembler)](../tools/ildasm-exe-il-disassembler.md) do wyświetlania informacji o języku pośrednim (MSIL) firmy Microsoft w zestawie.  
  
[Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../deployment/how-the-runtime-locates-assemblies.md)  
Wyjaśnienie, jak środowisko uruchomieniowe języka wspólnego lokalizuje i ładuje zestawy składające się na aplikację.  
  
[Programowanie za pomocą zestawów](../../standard/assembly/program.md)  
Opis koncepcji zestawów jako bloków konstrukcyjnych zarządzanych aplikacji.

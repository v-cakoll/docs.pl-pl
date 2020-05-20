---
title: Modernizacja aplikacji klasycznych w systemie Windows 10 z platformą .NET Core 3,1
description: Dowiedz się, jak przeprowadzić modernizację istniejących aplikacji klasycznych za pomocą programu .NET Core 3,1
ms.date: 05/12/2020
ms.openlocfilehash: 5861f806a9158ef761c47bc23e51327d4e2d0480
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423237"
---
# <a name="modernizing-desktop-apps-on-windows-10-with-net-core-31"></a>Modernizacja aplikacji klasycznych w systemie Windows 10 z platformą .NET Core 3,1

![Zrzut ekranu pokazujący modernizację książki elektronicznej aplikacji klasycznych.](./media/modernizing-existing-desktop-apps-ebook-cover.png)

OPUBLIKOWANA PRZEZ

Zespoły deweloperów firmy Microsoft, .NET i Visual Studio

Dział firmy Microsoft Corporation

One Microsoft Way

Redmond, Waszyngton 98052-6399

Prawa autorskie © 2020 przez firmę Microsoft Corporation

Wszelkie prawa zastrzeżone. Żadna część zawartości tej księgi nie może być odtwarzana ani przekazywana w żadnej formie ani za pomocą jakichkolwiek środków bez zgody na wydawcę.

Ta książka jest świadczona w postaci "AS-IS" i zawiera widoki i opinie autora. Widoki, opinie i informacje wyrażone w tej książce, w tym adresy URL i inne odwołania do witryn internetowych, mogą ulec zmianie bez powiadomienia.

Niektóre z przykładów przedstawiono wyłącznie do celów informacyjnych i są one fikcyjne. Żadne rzeczywiste skojarzenia lub związki nie są zamierzone ani wnioskowane.

Firma Microsoft i znaki towarowe wymienione na <https://www.microsoft.com> stronie "znaki towarowe" są znakami towarowymi grupy firm Microsoft.

Komputery Mac i macOS są znakami towarowymi firmy Apple Inc.

Wszystkie inne znaczniki i logo są własnością odpowiednich właścicieli.

Współautorzy:

> **Olia Gavrysh**, Menedżer programów, .NET Team, Microsoft

> **Miguel Angel Castejón Dominguez**, architekt innowacji, kabel

Uczestnicy i recenzenci:

> **Maira Wenzel**, starszy kierownik ds. programów, .NET Team, Microsoft

> **Adam de Gorge**, starszy dla deweloperów zawartości, zespół ds. dokumentacji platformy .NET, firma Microsoft

> **Miguel Ramos**, starszy kierownik ds. programu, zespół platformy dla deweloperów systemu Windows, Microsoft

> **Adam Braden**, główny Menedżer programu, zespół platformy deweloperów systemu Windows, Microsoft

> **Ricardo Minguez Pablos**, starszy Menedżer programów, Azure IoT Team, Microsoft

> **Nish Anil**, starszy kierownik ds. programów, .NET Team, Microsoft

> **Beth Massi**, starszy kierownik ds. marketingu produktu, Microsoft

> **Scott myśliwy**, kierownik ds. programów dyrektora

> **Marta Fuentes Lara**, kabel

> **Raúl Fernández de Córdoba**, kabel

> **Antonio Manuel Fernández Cantos**, kabel

## <a name="introduction"></a>Wprowadzenie

Ta książka zawiera informacje o strategiach, które można podjąć w celu przeniesienia istniejących aplikacji klasycznych za pomocą ścieżki modernizacji i uwzględnienia najnowszych funkcji środowiska uruchomieniowego, języka i platformy. Zobaczysz, że nie ma żadnych unikatowych przepisów, ponieważ każda aplikacja jest inna, a więc wymagania i preferencje. Dobrym sposobem jest to, że istnieją typowe podejścia do dodawania nowych funkcji i możliwości do aplikacji. Niektóre z nich nie będą nawet wymagały poważnych modyfikacji kodu. W tej książce będziemy odkrywać, jak wszystkie funkcje działają w tle, i wyjaśnić Mechanics ich implementacji. Ponadto znajdziesz typowe scenariusze dotyczące modernizacji istniejących aplikacji klasycznych, aby znaleźć inspirację do rozwoju projektów.

Podejście firmy Microsoft do modernizacji istniejących aplikacji ma na celu elastyczność tworzenia własnej dostosowanej ścieżki. Wszystkie strategie modernizacji opisane w tej książce są głównie niezależne. Możesz wybrać odpowiednie dla aplikacji i pominąć inne, które nie są dla Ciebie ważne. Innymi słowy, można mieszać i dopasowywać strategie, aby najlepiej rozwiązać wymagania aplikacji.

## <a name="who-should-use-the-book"></a>Kto powinien korzystać z książki

Ta książka została zapisana dla deweloperów i architektów rozwiązań, którzy chcą przeprowadzić modernizację istniejących Windows Forms i aplikacji klasycznych WPF, aby wykorzystać zalety platformy .NET Core i systemu Windows 10.

Ta książka może być również przydatna, jeśli jesteś specjalistą ds. pomocy technicznej, na przykład z architektem przedsiębiorstwa lub liderem programistycznym lub dyrektorem, który chce zapoznać się z zaletami aktualizacji istniejących aplikacji klasycznych.

## <a name="how-to-use-the-book"></a>Jak korzystać z książki

Ta książka dotyczy "Dlaczego" — Dlaczego warto przeprowadzić modernizację istniejących aplikacji oraz konkretne korzyści wynikające z używania NET Core 3,1 i MSIX do modernizacji aplikacji klasycznych. Zawartość książki jest przeznaczona dla architektów i osób podejmujących decyzje techniczne, którzy chcą zapoznać się z omówieniem, ale którzy nie muszą skupić się na implementacji i technicznych krokach krok po kroku.

Wraz z różnymi rozdziałami są udostępniane przykładowe fragmenty kodu implementacji i zrzuty ekranu z rozdziałem 5 w celu zaprezentowania kompletnego procesu migracji dla przykładowych aplikacji.

## <a name="what-this-book-doesnt-cover"></a>Czym nie obejmuje ta książka

Ta książka obejmuje określony podzbiór scenariuszy, które koncentrują się na scenariuszach podnoszenia i przesunięcia, i podkreślają sposób uzyskania korzyści z modernizacji bez wysiłku ponownego pisania kodu.

Ta książka nie dotyczy tworzenia nowoczesnych aplikacji z użyciem platformy .NET Core od podstaw lub od rozpoczęcia korzystania z Windows Forms i WPF. Koncentruje się na sposobach aktualizowania istniejących aplikacji klasycznych przy użyciu najnowszych technologii tworzenia oprogramowania dla komputerów stacjonarnych.

## <a name="samples-used-in-this-book"></a>Przykłady używane w tej książce

Aby wyróżnić kroki niezbędne do wykonania modernizacji, użyjemy przykładowej aplikacji o nazwie `eShopModernizing` . Ta aplikacja ma dwa wersje, Windows Forms i WPF, a następnie pokazuje proces krok po kroku dotyczący sposobu przeprowadzania modernizacji na obu tych platformach w programie .NET Core.

Ponadto w repozytorium GitHub dla tej książki znajdziesz wyniki procesu, z którym możesz się zapoznać, jeśli zdecydujesz się wykonać instrukcje krok po kroku.

## <a name="send-your-feedback"></a>Wyślij opinię

Ta książka i powiązane przykłady są ciągle zmieniane, dzięki czemu Twoje opinie są gotowe! Jeśli masz komentarze dotyczące sposobu, w jaki można ulepszyć tę książkę, Skorzystaj z sekcji opinia w dolnej części strony utworzonej w witrynie [GitHub](https://github.com/dotnet/docs/issues).

>[!div class="step-by-step"]
>[Dalej](why-modern-applications.md)

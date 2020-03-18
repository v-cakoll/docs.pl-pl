---
title: Analizatory oparte na Roslyn - .NET
description: Dowiedz się więcej o analizatorach opartych na Roslyn, które znajdują problemy i sugerują poprawki dla tych problemów.
author: billwagner
ms.author: wiwagn
ms.date: 01/24/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 436cfb3904f0891f8c18bb5890563a13d65e2d1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "62003057"
---
# <a name="the-roslyn-based-analyzers"></a>Analizatory oparte na Roslyn

Analizatory oparte na Roslyn używają sdk kompilatora .NET (Roslyn) do analizowania kodu źródłowego projektu, aby znaleźć problemy i zaproponować poprawki. Różne analizatory szukać różnych klas problemów, począwszy od praktyk, które mogą powodować błędy do problemów z zabezpieczeniami do zgodności interfejsu API.

Analizatory oparte na Roslyn działają zarówno interaktywnie, jak i podczas kompilacji. Analizator zawiera różne wskazówki, gdy w programie Visual Studio lub w kompilacjach wiersza polecenia.

Podczas edytowania kodu w programie Visual Studio analizatory są uruchamiane podczas wprowadzania zmian, przechwytując możliwe problemy natychmiast po utworzeniu kodu, który wywołuje problemy. Wszelkie problemy są podświetlone squiggles w każdym problemie. Visual Studio wyświetla żarówkę, a po kliknięciu na nią analizator zasugeruje możliwe poprawki dla tego problemu. Podczas tworzenia projektu, albo w programie Visual Studio lub z wiersza polecenia, cały kod źródłowy jest analizowany i analizator zawiera pełną listę potencjalnych problemów. Na poniższej ilustracji przedstawiono jeden przykład.

![problemy zgłaszane przez analizator ram](./media/framework-analyzers-2.png)

Analizatory oparte na Roslyn zgłaszają potencjalne problemy jako błędy, ostrzeżenia lub informacje na podstawie wagi problemu.

W projekcie można zainstalować analizatory oparte na Roslyn jako pakiety NuGet. Skonfigurowane analizatory i wszelkie ustawienia dla każdego analizatora są przywracane i uruchamiane na dowolnym komputerze dewelopera dla tego projektu.

> [!NOTE]
> Środowisko użytkownika dla analizatorów opartych na Roslyn różni się od bibliotek analizy kodu, takich jak starsze wersje FxCop i narzędzia do analizy zabezpieczeń.  Nie musisz jawnie uruchamiać analizatorów opartych na Roslyn. Nie ma potrzeby używania elementów menu "Uruchom analizę kodu" w menu "Analizuj" w programie Visual Studio. Analizatory oparte na Roslyn działają asynchronicznie podczas pracy.

## <a name="more-information-on-specific-analyzers"></a>Więcej informacji na temat konkretnych analizatorów

W tej sekcji omówiono następujące analizatory:

* [Analizator interfejsu API:](api-analyzer.md)Ten analizator sprawdza kod pod kątem potencjalnych zagrożeń ze zgodnością lub zastosowań przestarzałych interfejsów API.
* [Analizator framework:](framework-analyzer.md)Ten analizator sprawdza kod, aby upewnić się, że jest zgodny z wytycznymi dla aplikacji .NET Framework. Reguły te obejmują kilka zaleceń opartych na zabezpieczeniach.
* [Analizator przenośności .NET:](portability-analyzer.md)Ten analizator sprawdza kod, aby zobaczyć, ile pracy jest wymagane do zapewnienia zgodności aplikacji z innymi implementacjami i profilami .NET, w tym .NET Core, .NET Standard, UWP i Xamarin dla systemów iOS, Android i Mac.

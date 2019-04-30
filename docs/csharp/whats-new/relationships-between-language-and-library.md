---
title: Relacja między funkcje języka i typy biblioteki | Dokumentacja firmy Microsoft
description: Funkcje języka często zależy od biblioteki typów dla implementacji. Informacje o tej relacji.
ms.date: 07/20/2017
ms.openlocfilehash: dfae7972af0a251a92700d7d33bd6f971eb1870e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706029"
---
# <a name="relationships-between-language-features-and-library-types"></a>Relacje między funkcjami języka i biblioteki typów

C# Definicji języka wymaga biblioteki standardowej mieć pewne typy i niektóre dostępne elementy członkowskie dla tych typów. Kompilator generuje kod, który używa tych wymaganych typów i elementów członkowskich dla wielu funkcji językowych. Gdy jest to konieczne, istnieją pakiety NuGet, które zawierają typy służące do nowszych wersji języka podczas pisania kodu, dla których te typy lub elementy członkowskie nie wdrożono jeszcze środowisk.

Ta zależność od funkcji biblioteki standardowej było częścią C# języka od swojej pierwszej wersji. Przykłady w tej wersji, dostępne:

* <xref:System.Exception> — używany dla wszystkich wyjątków wygenerowanego przez kompilator.
* <xref:System.String> - C# `string` typ jest synonimem dla <xref:System.String>.
* <xref:System.Int32> -synonim `int`.

Tym pierwsza wersja została proste: kompilator i standardową bibliotekę dostarczane razem i była tylko jedną wersja każdego z nich.

Kolejne wersje C# od czasu do czasu zostały dodane nowe typy lub elementy członkowskie do zależności. Przykłady: <xref:System.Runtime.CompilerServices.INotifyCompletion>, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> i <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>. C#7.0 kontynuuje, to dodanie zależności na <xref:System.ValueTuple> do zaimplementowania [krotek](../tuples.md) funkcji języka.

Zespół projektowy języka działa, aby zminimalizować obszar powierzchni typów i elementów członkowskich, wymagane w zgodne biblioteki standardowej. Ten cel jest równoważone względem przejrzysty, w którym nowe funkcje biblioteki są bezproblemowo włączone do języka. Nastąpi nowe funkcje w przyszłych wersjach C# wymagające nowych typów i elementów członkowskich w bibliotece standardowych. Należy zrozumieć, jak zarządzać tych zależności w pracy.

## <a name="managing-your-dependencies"></a>Zarządzanie zależnościami

C#narzędzia kompilatora są teraz całkowicie niezależni od cyklu tworzenia wydań bibliotek .NET na obsługiwanych platformach. W rzeczywistości różnych bibliotek .NET mają cykle wydania różne: .NET Framework na Windows jest wydana jako aktualizacja Windows, platformy .NET Core jest dostarczana w oddzielnym harmonogramem i Xamarin wersje biblioteki dostarczanie aktualizacji za pomocą narzędzi platformy Xamarin dla każdej platformy docelowej.

Większość czasu nie będą zauważyć te zmiany. Jednak podczas pracy z nowszą wersją języka, który nie wymaga funkcji, ale w bibliotekach .NET na tej platformie, będziesz odwoływać się do pakietów NuGet, aby zapewnić te nowe typy.
Jako platformy obsługiwanej przez aplikację zostaną zaktualizowane o nowe instalacje framework można usunąć odwołania dodatkowych.

Ta separacja oznacza, że można użyć nowych funkcji języków, nawet wtedy, gdy są przeznaczone dla maszyn, które mogą nie mieć odpowiednich framework.

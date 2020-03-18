---
title: Relacja między funkcjami językowym a typami bibliotek | Dokumenty firmy Microsoft
description: Funkcje języka często opierają się na typach bibliotek w celu wykonania. Zrozum tę relację.
ms.date: 07/20/2017
ms.openlocfilehash: dfae7972af0a251a92700d7d33bd6f971eb1870e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61706029"
---
# <a name="relationships-between-language-features-and-library-types"></a>Relacje między funkcjami języka a typami bibliotek

Definicja języka Języka C# wymaga standardowej biblioteki mieć pewne typy i niektórych dostępnych elementów członkowskich na tych typów. Kompilator generuje kod, który używa tych wymaganych typów i elementów członkowskich dla wielu różnych funkcji języka. W razie potrzeby istnieją pakiety NuGet, które zawierają typy potrzebne dla nowszych wersji języka podczas pisania kodu dla środowisk, w których te typy lub elementy członkowskie nie zostały jeszcze wdrożone.

Ta zależność od funkcji biblioteki standardowej jest częścią języka C# od jego pierwszej wersji. W tej wersji przykłady obejmowały:

* <xref:System.Exception>- używany dla wszystkich kompilator generowane wyjątki.
* <xref:System.String>- Typ `string` C# jest synonimem <xref:System.String>.
* <xref:System.Int32>- synonim `int`.

Ta pierwsza wersja była prosta: kompilator i standardowa biblioteka dostarczane razem i była tylko jedna wersja każdego.

Kolejne wersje języka C# od czasu do czasu dodaje nowe typy lub elementy członkowskie do zależności. Przykłady obejmują: <xref:System.Runtime.CompilerServices.INotifyCompletion> <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> , <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>i . C# 7.0 kontynuuje to przez <xref:System.ValueTuple> dodanie zależności na zaimplementować funkcję języka [krotek.](../tuples.md)

Zespół projektu języka działa, aby zminimalizować powierzchnię typów i elementów członkowskich wymaganych w zgodnej standardowej bibliotece. Cel ten jest równoważony z czystym projektem, w którym nowe funkcje biblioteki są bezproblemowo włączane do języka. Pojawią się nowe funkcje w przyszłych wersjach języka C#, które wymagają nowych typów i elementów członkowskich w standardowej bibliotece. Ważne jest, aby zrozumieć, jak zarządzać tymi zależnościami w swojej pracy.

## <a name="managing-your-dependencies"></a>Zarządzanie zależnościami

Narzędzia kompilatora Języka C# są teraz oddzielone od cyklu wydawniczy bibliotek .NET na obsługiwanych platformach. W rzeczywistości różne biblioteki .NET mają różne cykle wydania: .NET Framework w systemie Windows jest wydawana jako windows update, .NET Core jest dostarczany według oddzielnego harmonogramu, a wersje biblioteki Xamarin są dostarczane z narzędziami platformy Xamarin dla każdej platformy docelowej.

Przez większość czasu, nie zauważysz tych zmian. Jednak podczas pracy z nowszą wersją języka, który wymaga funkcji jeszcze w bibliotekach .NET na tej platformie, będzie odwoływać się do pakietów NuGet, aby zapewnić te nowe typy.
Ponieważ platformy, które obsługuje aplikacja, są aktualizowane za pomocą nowych instalacji framework, można usunąć dodatkowe odwołanie.

Ta separacja oznacza, że można używać nowych funkcji języka, nawet jeśli są przeznaczone dla komputerów, które mogą nie mieć odpowiednich ramach.

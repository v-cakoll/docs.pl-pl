---
title: Relacja między — funkcje językowe i biblioteki typów | Dokumentacja firmy Microsoft
description: Funkcje języka często korzystają z biblioteki typów dla implementacji. Dowiedz się, że relacji.
ms.date: 07/20/2017
ms.openlocfilehash: dfae7972af0a251a92700d7d33bd6f971eb1870e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360086"
---
# <a name="relationships-between-language-features-and-library-types"></a>Relacje między — funkcje językowe i biblioteki typów

Definicja języka C# wymaga biblioteki standardowej mają określone typy i niektórych dostępnych elementów członkowskich na tych typów. Kompilator generuje kod, który używa tych wymagane typy i składniki wiele funkcji innego języka. Jeśli to konieczne, istnieją pakietów NuGet, które zawierają typy potrzebne do nowszych wersji języka podczas pisania kodu dla środowisk, w którym tych typów albo elementów członkowskich nie wdrożono jeszcze.

Tę zależność od funkcji biblioteki standardowej została część języka C# od momentu jego pierwszej wersji. W tej wersji z protokołem przykładami:

* <xref:System.Exception> — używany dla wszystkich wyjątków wygenerowanego przez kompilator.
* <xref:System.String> -C# `string` typu jest synonimem <xref:System.String>.
* <xref:System.Int32> -synonim `int`.

Tego pierwszej wersji był prosty: kompilator i biblioteki standardowej dostarczane ze sobą, i nie tylko jedna wersja każdego z nich.

Kolejne wersje języka C# czasami dodano nowych typów albo elementów członkowskich do zależności. Przykłady obejmują: <xref:System.Runtime.CompilerServices.INotifyCompletion>, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> i <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>. C# 7.0 nadal to przez dodanie zależności na <xref:System.ValueTuple> do zaimplementowania [krotek](../tuples.md) funkcji języka.

Zespół projektowy języka działa, aby zminimalizować powierzchni typy i składniki wymagane w zgodne biblioteki standardowe. Ten cel jest rozmieszczana przed czystą projektowania, gdzie nowych funkcji biblioteki są włączone bezproblemowo do języka. Będzie nowych funkcji w przyszłych wersjach języka C#, które wymagają nowych typów i członków w standardowej bibliotece. Należy zrozumieć, jak zarządzać tych zależności w pracy.

## <a name="managing-your-dependencies"></a>Zarządzanie zależności

Narzędzia kompilatora C# są teraz całkowicie niezależna od wersji cyklu bibliotek .NET na obsługiwanych platformach. W rzeczywistości różnych bibliotek .NET mają różne cykle: wydaniu programu .NET Framework w systemie Windows jako usługi Windows Update, .NET Core jest dostarczany na oddzielnym harmonogramem i wersje Xamarin biblioteki dostarczać aktualizacje przy użyciu narzędzi platformy Xamarin dla każdej platformy docelowej.

Większość czasu nie będzie można zauważyć tych zmian. Jednak podczas pracy przy użyciu nowszej wersji języka, który nie wymaga funkcji jeszcze podłączone do bibliotek .NET na tej platformie, będziesz odwoływać pakietów NuGet, aby zapewnić tych nowych typów.
Jako platformy obsługuje Twojej aplikacji są zaktualizowane o nowe instalacje framework należy usunąć dodatkowe odwołania.

Ta separacja oznacza, że można użyć nowych funkcji języka, nawet wtedy, gdy ma być przeznaczona dla komputerów, które może nie mieć odpowiednich framework.

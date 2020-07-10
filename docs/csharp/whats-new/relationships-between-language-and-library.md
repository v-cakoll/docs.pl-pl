---
title: Relacja między funkcjami językowymi i typami bibliotek | Microsoft Docs
description: Funkcje języka często polegają na typach bibliotek do wdrożenia. Zapoznaj się z tą relacją.
ms.date: 07/20/2017
ms.openlocfilehash: abf15385da3756c35db2df822cc2e11e9edf5758
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174104"
---
# <a name="relationships-between-language-features-and-library-types"></a>Relacje między funkcjami językowymi i typami bibliotek

Definicja języka C# wymaga, aby w bibliotece standardowej były określone typy i niektóre dostępne elementy członkowskie dla tych typów. Kompilator generuje kod, który używa tych wymaganych typów i elementów członkowskich dla wielu różnych funkcji języka. W razie potrzeby istnieją pakiety NuGet, które zawierają typy potrzebne do nowszych wersji języka podczas pisania kodu dla środowisk, w których te typy lub elementy członkowskie nie zostały jeszcze wdrożone.

Ta zależność od funkcji biblioteki standardowej była częścią języka C# od momentu jego pierwszej wersji. W tej wersji uwzględniono przykłady:

* <xref:System.Exception>-używane dla wszystkich wyjątków generowanych przez kompilator.
* <xref:System.String>— Typ C# `string` jest synonimem dla <xref:System.String> .
* <xref:System.Int32>-synonim `int` .

Ta pierwsza wersja była prosta: kompilator i Standardowa biblioteka została dostarczona ze sobą i istniała tylko jedna wersja każdej z nich.

Kolejne wersje języka C# czasami Dodaliśmy nowe typy lub elementy członkowskie do zależności. Przykłady obejmują: <xref:System.Runtime.CompilerServices.INotifyCompletion> , <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> i <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute> . C# 7,0 kontynuuje to przez dodanie zależności <xref:System.ValueTuple> do implementacji funkcji języka [krotek](../language-reference/builtin-types/value-tuples.md) .

Zespół projektowy języka działa w celu zminimalizowania powierzchni typów i elementów członkowskich wymaganych w standardowej bibliotece zgodnej. Ten cel jest zrównoważony w odniesieniu do czystego projektu, w którym nowe funkcje biblioteki są bezproblemowo dodawane do języka. W przyszłych wersjach języka C# będą dostępne nowe funkcje, które wymagają nowych typów i elementów członkowskich w standardowej bibliotece. Ważne jest, aby zrozumieć, jak zarządzać tymi zależnościami w pracy.

## <a name="managing-your-dependencies"></a>Zarządzanie zależnościami

Narzędzia kompilatora języka C# są teraz oddzielone od cyklu wydania bibliotek .NET na obsługiwanych platformach. W rzeczywistości różne biblioteki .NET mają różne cykle wydania: .NET Framework w systemie Windows jest wydawany jako Windows Update, program .NET Core jest dostarczany zgodnie z oddzielnym harmonogramem, a wersje programu Xamarin w bibliotece są dostarczane z narzędziami Xamarin Tools for each platformą docelową.

Większość czasu nie zanotuje tych zmian. Jednak podczas pracy z nowszą wersją języka, który wymaga funkcji jeszcze nie w bibliotekach .NET na tej platformie, należy odwołać się do pakietów NuGet, aby udostępnić te nowe typy.
Ponieważ platformy obsługiwane przez aplikację są aktualizowane przy użyciu nowych instalacji platformy, można usunąć dodatkowe informacje.

Ta separacja oznacza, że można korzystać z nowych funkcji języka nawet w przypadku maszyn docelowych, które mogą nie mieć odpowiedniej struktury.

---
title: Zrozumienie AssemblyLoadContext — .NET Core
description: Najważniejsze koncepcje dotyczące przeznaczenia i zachowania AssemblyLoadContext w programie .NET Core.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 8a73a432bf8cc72cced77cf6c62a785b72032913
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291260"
---
# <a name="understanding-systemruntimeloaderassemblyloadcontext"></a>Informacje o system. Runtime. Loader. AssemblyLoadContext

Klasa <xref:System.Runtime.Loader.AssemblyLoadContext> jest unikatowa dla platformy .NET Core. Ten artykuł próbuje uzupełnić dokumentację interfejsu API <xref:System.Runtime.Loader.AssemblyLoadContext> z informacjami koncepcyjnymi.

Ten artykuł ma zastosowanie w przypadku deweloperów implementujących dynamiczne ładowanie, szczególnie dla deweloperów platformy ładującej dynamicznie.

## <a name="what-is-the-assemblyloadcontext"></a>Co to jest AssemblyLoadContext?

Każda aplikacja .NET Core niejawnie używa <xref:System.Runtime.Loader.AssemblyLoadContext>.
Jest to dostawca środowiska uruchomieniowego służący do lokalizowania i ładowania zależności. Za każdym razem, gdy zostanie załadowana zależność, wystąpienie <xref:System.Runtime.Loader.AssemblyLoadContext> jest wywoływane, aby je zlokalizować.

- Zapewnia ona usługę lokalizowania, ładowania i buforowania zestawów zarządzanych i innych zależności.

- Aby zapewnić obsługę dynamicznego ładowania i zwalniania kodu, tworzy on izolowany kontekst do ładowania kodu i jego zależności we własnym wystąpieniu <xref:System.Runtime.Loader.AssemblyLoadContext>.

## <a name="when-do-you-need-multiple-assemblyloadcontext-instances"></a>Kiedy potrzebujesz wielu wystąpień AssemblyLoadContext?

Pojedyncze wystąpienie <xref:System.Runtime.Loader.AssemblyLoadContext> jest ograniczone do załadowania dokładnie jednej wersji <xref:System.Reflection.Assembly> na prostą nazwę zestawu, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>.

To ograniczenie może stać się problemem podczas dynamicznego ładowania modułów kodu. Każdy moduł jest kompilowany niezależnie i może zależeć od różnych wersji <xref:System.Reflection.Assembly>. Ten problem występuje często, gdy różne moduły zależą od różnych wersji często używanej biblioteki.

Aby zapewnić obsługę dynamicznego ładowania kodu, interfejs API <xref:System.Runtime.Loader.AssemblyLoadContext> umożliwia ładowanie wersji <xref:System.Reflection.Assembly> w tej samej aplikacji. Każde wystąpienie <xref:System.Runtime.Loader.AssemblyLoadContext> zawiera unikatowe mapowanie słownika każdej <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> do określonego wystąpienia <xref:System.Reflection.Assembly>.

Zapewnia również wygodny mechanizm grupowania zależności związanych z modułem kodu w celu późniejszego zwolnienia.

## <a name="what-is-special-about-the-assemblyloadcontextdefault-instance"></a>Co to jest specjalne wystąpienie AssemblyLoadContext. default?

Wystąpienie <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> jest automatycznie wypełniane przez środowisko uruchomieniowe przy uruchamianiu.  Używa [domyślnej sondy](default-probing.md) do lokalizowania i znajdowania wszystkich zależności statycznych.

Rozwiązuje najczęstsze scenariusze ładowania zależności.

## <a name="how-does-assemblyloadcontext-support-dynamic-dependencies"></a>Jak usługa AssemblyLoadContext obsługuje zależności dynamiczne?

<xref:System.Runtime.Loader.AssemblyLoadContext> zawiera różne zdarzenia i funkcje wirtualne, które można przesłonić.

Wystąpienie <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> obsługuje tylko przesłanianie zdarzeń.

Algorytmy ładowania [zestawów zarządzanego](loading-managed.md), [algorytm ładowania zestawu satelitarnego](loading-resources.md)i [niezarządzany (natywny) algorytm ładowania](loading-unmanaged.md) odnoszą się do wszystkich dostępnych zdarzeń i funkcji wirtualnych.  W artykułach są wyświetlane poszczególne zdarzenia i względne pozycje funkcji w algorytmach ładowania. Ten artykuł nie odtwarza tych informacji.

Ta sekcja obejmuje ogólne zasady dotyczące odpowiednich zdarzeń i funkcji.

- **Można powtarzać**. Zapytanie dla określonej zależności musi zawsze prowadzić do tej samej odpowiedzi. Należy zwrócić to samo załadowane wystąpienie zależności. To wymaganie ma podstawowe znaczenie dla spójności pamięci podręcznej. W przypadku zestawów zarządzanych w szczególności tworzymy pamięć podręczną <xref:System.Reflection.Assembly>. Klucz pamięci podręcznej jest prostą nazwą zestawu, <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>.
- **Zazwyczaj nie**zgłaszaj.  Oczekuje się, że te funkcje zwracają `null`, a nie throw, gdy nie można znaleźć żądanej zależności. Przerzucanie spowoduje przedwcześnie zakończenie wyszukiwania i propagowanie wyjątku do obiektu wywołującego. Przerzucanie powinno być ograniczone do nieoczekiwanych błędów, takich jak uszkodzony zestaw lub stan braku pamięci.
- **Unikaj rekursji**. Należy pamiętać, że te funkcje i programy obsługi implementują reguły ładowania dla lokalizowania zależności. Implementacja nie powinna wywoływać interfejsów API wyzwalających rekursję. Kod powinien zwykle wywoływać funkcje ładowania **AssemblyLoadContext** , które wymagają określonej ścieżki lub argumentu odwołania do pamięci.
- **Załaduj do poprawnej AssemblyLoadContext**. Wybór miejsca, w którym mają zostać załadowane zależności, to specyficzne dla aplikacji.  Wybór jest implementowany przez te zdarzenia i funkcje. Gdy kod wywołuje funkcje ładowania po ścieżce **AssemblyLoadContext** , wywołuje je w wystąpieniu, w którym ma zostać załadowany kod. Nie zwracają `null` i umożliwiają obsługę <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> może to być najprostsza opcja.
- **Należy pamiętać o Races wątków**. Ładowanie może być wyzwalane przez wiele wątków. AssemblyLoadContext obsługuje wątki Races przez niepodzielne Dodawanie zestawów do swojej pamięci podręcznej. Wystąpienie Loser wyścigu jest odrzucane. W logice implementacji nie należy dodawać dodatkowej logiki, która nie obsługuje prawidłowo wielu wątków.

## <a name="how-are-dynamic-dependencies-isolated"></a>Jak są izolowane zależności dynamiczne?

Każde wystąpienie <xref:System.Runtime.Loader.AssemblyLoadContext> reprezentuje unikatowy zakres dla wystąpień <xref:System.Reflection.Assembly> i definicje <xref:System.Type>.

Między tymi zależnościami nie istnieje izolacja binarna. Są one izolowane tylko przez nieznalezienie siebie według nazwy.

W każdym <xref:System.Runtime.Loader.AssemblyLoadContext>:

- <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> może odwoływać się do innego wystąpienia <xref:System.Reflection.Assembly>.
- <xref:System.Type.GetType%2A?displayProperty=nameWithType> może zwrócić wystąpienie innego typu dla tego samego typu `name`.

## <a name="how-are-dependencies-shared"></a>Jak są udostępniane zależności?

Zależności można łatwo udostępniać między wystąpieniami <xref:System.Runtime.Loader.AssemblyLoadContext>. Model ogólny jest przeznaczony dla jednego <xref:System.Runtime.Loader.AssemblyLoadContext>, aby załadować zależność.  Druga współużytkuje zależność przy użyciu odwołania do załadowanego zestawu.

To udostępnianie jest wymagane przez zestawy środowiska uruchomieniowego. Te zestawy można ładować tylko do <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>. Taka sama jest wymagana dla platform, takich jak `ASP.NET`, `WPF` lub `WinForms`.

Zaleca się, aby współużytkowane zależności zostały załadowane do <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>. To udostępnianie jest typowym wzorcem projektu.

Udostępnianie jest implementowane w kodowaniu wystąpienia niestandardowego <xref:System.Runtime.Loader.AssemblyLoadContext>. <xref:System.Runtime.Loader.AssemblyLoadContext> zawiera różne zdarzenia i funkcje wirtualne, które można przesłonić. Gdy którakolwiek z tych funkcji zwróci odwołanie do wystąpienia <xref:System.Reflection.Assembly>, które zostało załadowane w innym wystąpieniu <xref:System.Runtime.Loader.AssemblyLoadContext>, wystąpienie <xref:System.Reflection.Assembly> jest udostępniane. Standardowy algorytm obciążenia to <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> do załadowania, aby uprościć wspólny wzorzec udostępniania.  Zobacz [algorytm ładowania zestawu zarządzanego](loading-managed.md).

## <a name="complications"></a>Komplikacj

### <a name="type-conversion-issues"></a>Błędy konwersji typów

Gdy dwa wystąpienia <xref:System.Runtime.Loader.AssemblyLoadContext> zawierają definicje typu o tej samej `name`, nie są tego samego typu. Są tego samego typu, jeśli i tylko wtedy, gdy pochodzą z tego samego wystąpienia <xref:System.Reflection.Assembly>.

W celu zaskomplikowania spraw komunikaty o wyjątkach dotyczące tych niezgodnych typów mogą być mylące. Typy są określane w komunikatach o wyjątku według ich nazw typów prostych. Typowy komunikat o wyjątku w tym przypadku powinien mieć postać:

> Nie można przekonwertować obiektu typu "izolowany" na typ "izolowany".

### <a name="debugging-type-conversion-issues"></a>Błędy konwersji typu debugowania

Uwzględniając parę niezgodnych typów, należy również znać:

- @No__t każdego typu-0
- Każdy typ <xref:System.Runtime.Loader.AssemblyLoadContext>, który można uzyskać za pośrednictwem funkcji <xref:System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(System.Reflection.Assembly)?displayProperty=nameWithType>.

Podajemy dwa obiekty `a` i `b`, które oceniają następujące elementy w debugerze:

```csharp
// In debugger look at each assembly's instance, Location, and FullName
a.GetType().Assembly
b.GetType().Assembly
// In debugger look at each AssemblyLoadContext's instance and name
System.Runtime.AssemblyLoadContext.GetLoadContext(a.GetType().Assembly)
System.Runtime.AssemblyLoadContext.GetLoadContext(b.GetType().Assembly)
```

### <a name="resolving-type-conversion-issues"></a>Rozwiązywanie problemów z konwersją typów

Istnieją dwa wzorce projektowe umożliwiające rozwiązanie tych problemów z konwersją typów.

1. Używaj wspólnych typów udostępnionych. Ten typ współużytkowany może być typem pierwotnego środowiska uruchomieniowego lub może polegać na utworzeniu nowego typu udostępnionego w zestawie udostępnionym.  Często udostępniony typ jest [interfejsem](../../csharp/language-reference/keywords/interface.md) zdefiniowanym w zestawie aplikacji. Zobacz również: w [jaki sposób są udostępniane zależności?](#how-are-dependencies-shared)

2. Używaj technik kierujących do konwersji z jednego typu na drugi.

---
title: Opis AssemblyLoadContext — .NET Core
description: Kluczowe pojęcia, aby zrozumieć cel i zachowanie AssemblyLoadContext w .NET Core.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 8a73a432bf8cc72cced77cf6c62a785b72032913
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72291260"
---
# <a name="understanding-systemruntimeloaderassemblyloadcontext"></a>Opis System.Runtime.Loader.AssemblyLoadContext

Klasa <xref:System.Runtime.Loader.AssemblyLoadContext> jest unikatowa dla .NET Core. W tym artykule <xref:System.Runtime.Loader.AssemblyLoadContext> próbuje uzupełnić dokumentację interfejsu API o informacje o pojęciach.

Ten artykuł jest odpowiedni dla deweloperów implementujących dynamiczne ładowanie, szczególnie deweloperzy dynamicznej struktury ładowania.

## <a name="what-is-the-assemblyloadcontext"></a>Co to jest AssemblyLoadContext?

Każda aplikacja .NET Core <xref:System.Runtime.Loader.AssemblyLoadContext>niejawnie używa pliku .
Jest dostawcą czasu wykonywania do lokalizowania i ładowania zależności. Za każdym razem, gdy <xref:System.Runtime.Loader.AssemblyLoadContext> zależność jest ładowany, wystąpienie jest wywoływana, aby go zlokalizować.

- Zapewnia usługę lokalizowania, ładowania i buforowania zarządzanych zestawów i innych zależności.

- Aby obsługiwać dynamiczne ładowanie kodu i zwalniania, tworzy izolowany kontekst do <xref:System.Runtime.Loader.AssemblyLoadContext> ładowania kodu i jego zależności w ich własnym wystąpieniu.

## <a name="when-do-you-need-multiple-assemblyloadcontext-instances"></a>Kiedy potrzebujesz wielu wystąpień AssemblyLoadContext?

Pojedyncze <xref:System.Runtime.Loader.AssemblyLoadContext> wystąpienie jest ograniczone do ładowania <xref:System.Reflection.Assembly> dokładnie jednej wersji <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>na prostą nazwę zestawu.

To ograniczenie może stać się problemem podczas dynamicznego ładowania modułów kodu. Każdy moduł jest niezależnie skompilowany i może <xref:System.Reflection.Assembly>zależeć od różnych wersji pliku . Ten problem często występuje, gdy różne moduły zależą od różnych wersji powszechnie używanej biblioteki.

Aby obsługiwać dynamicznie ładowania <xref:System.Runtime.Loader.AssemblyLoadContext> kodu, interfejs API przewiduje <xref:System.Reflection.Assembly> ładowanie wersji powodujące konflikt w tej samej aplikacji. Każde <xref:System.Runtime.Loader.AssemblyLoadContext> wystąpienie zawiera unikatowy słownik mapowanie każdego <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> do określonego <xref:System.Reflection.Assembly> wystąpienia.

Zapewnia również wygodny mechanizm grupowania zależności związanych z modułem kodu do późniejszego rozładowania.

## <a name="what-is-special-about-the-assemblyloadcontextdefault-instance"></a>Co jest specjalnego w AssemblyLoadContext.Default wystąpienie?

Wystąpienie <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> jest automatycznie wypełniane przez czas wykonywania podczas uruchamiania.  Używa [domyślnego sondowania,](default-probing.md) aby zlokalizować i znaleźć wszystkie zależności statyczne.

Rozwiązuje najbardziej typowe scenariusze ładowania zależności.

## <a name="how-does-assemblyloadcontext-support-dynamic-dependencies"></a>Jak AssemblyLoadContext obsługuje zależności dynamiczne?

<xref:System.Runtime.Loader.AssemblyLoadContext>ma różne zdarzenia i funkcje wirtualne, które mogą być zastąpione.

Wystąpienie <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> obsługuje tylko zastępowanie zdarzeń.

Artykuły [Algorytm ładowania zestawu zarządzanego,](loading-managed.md) [algorytm ładowania zestawu satelitarnego](loading-resources.md)i [algorytm ładowania biblioteki niezarządzanej (natywnej)](loading-unmanaged.md) odnoszą się do wszystkich dostępnych zdarzeń i funkcji wirtualnych.  Artykuły pokazują każde zdarzenie i względną pozycję funkcji w algorytmach ładowania. Ten artykuł nie odtwarza tych informacji.

Niniejsza sekcja obejmuje ogólne zasady dotyczące istotnych zdarzeń i funkcji.

- **Być powtarzalnym**. Kwerenda dla określonej zależności zawsze musi spowodować taką samą odpowiedź. Należy zwrócić to samo załadowane wystąpienie zależności. To wymaganie ma podstawowe znaczenie dla spójności pamięci podręcznej. W szczególności w przypadku zestawów zarządzanych <xref:System.Reflection.Assembly> tworzymy pamięć podręczną. Klucz pamięci podręcznej jest <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>prostą nazwą zestawu.
- **Zazwyczaj nie rzucać**.  Oczekuje się, że te `null` funkcje powrócić, a nie throw, gdy nie można znaleźć żądaną zależność. Zgłaszanie przedwcześnie zakończy wyszukiwanie i będzie propagować wyjątek do obiektu wywołującego. Zgłaszanie powinno być ograniczone do nieoczekiwanych błędów, takich jak uszkodzony zestaw lub warunek braku pamięci.
- **Unikać rekursji**. Należy pamiętać, że te funkcje i programy obsługi implementują reguły ładowania do lokalizowania zależności. Implementacja nie powinna wywoływać interfejsów API, które wyzwalają rekursję. Kod powinien zazwyczaj wywołać **AssemblyLoadContext** funkcji ładowania, które wymagają określonej ścieżki lub argument odwołania do pamięci.
- **Załaduj do prawidłowego AssemblyLoadContext**. Wybór, gdzie załadować zależności jest specyficzne dla aplikacji.  Wybór jest realizowany przez te zdarzenia i funkcje. Gdy kod wywołuje **AssemblyLoadContext** funkcji obciążenia po ścieżce wywołać je w wystąpieniu, w którym chcesz załadowany kod. Kiedyś powrót `null` i pozwalając <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> uchwyt obciążenia może być najprostszą opcją.
- **Należy pamiętać o wyścigach wątków**. Ładowanie może być wyzwalane przez wiele wątków. AssemblyLoadContext obsługuje wyścigi wątków przez atomowe dodawanie zestawów do pamięci podręcznej. Instancja przegranego wyścigu zostaje odrzucona. W logice implementacji nie należy dodawać dodatkowe logiki, która nie obsługuje poprawnie wiele wątków.

## <a name="how-are-dynamic-dependencies-isolated"></a>Jak są izolowane zależności dynamiczne?

Każde <xref:System.Runtime.Loader.AssemblyLoadContext> wystąpienie reprezentuje unikatowy zakres dla <xref:System.Reflection.Assembly> wystąpień i <xref:System.Type> definicji.

Nie ma binarnej izolacji między tymi zależnościami. Są one izolowane tylko przez nie znalezienie siebie po imieniu.

W <xref:System.Runtime.Loader.AssemblyLoadContext>każdym z nich:

- <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>może odnosić <xref:System.Reflection.Assembly> się do innego wystąpienia.
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>może zwrócić wystąpienie innego typu `name`dla tego samego typu .

## <a name="how-are-dependencies-shared"></a>W jaki sposób współużytkowane są zależności?

Zależności można łatwo współużytkować między <xref:System.Runtime.Loader.AssemblyLoadContext> wystąpieniami. Model ogólny jest <xref:System.Runtime.Loader.AssemblyLoadContext> dla jednego, aby załadować zależność.  Inne współudziałzależności przy użyciu odwołania do załadowanego zestawu.

To udostępnianie jest wymagane zestawów w czasie wykonywania. Zestawy te mogą być <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>ładowane tylko do pliku . To samo jest wymagane dla `ASP.NET` `WPF`ram, `WinForms`takich jak , lub .

Zaleca się, że współużytkowane zależności <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>powinny być ładowane do . To udostępnianie jest typowy wzór projektu.

Udostępnianie jest implementowane w kodowaniu wystąpienia niestandardowego. <xref:System.Runtime.Loader.AssemblyLoadContext> <xref:System.Runtime.Loader.AssemblyLoadContext>ma różne zdarzenia i funkcje wirtualne, które mogą być zastąpione. Gdy którakolwiek z tych funkcji <xref:System.Reflection.Assembly> zwraca odwołanie do <xref:System.Runtime.Loader.AssemblyLoadContext> wystąpienia, <xref:System.Reflection.Assembly> który został załadowany w innym wystąpieniu, wystąpienie jest współużytkowane. Standardowy algorytm ładowania odracza do <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> ładowania w celu uproszczenia wspólnego wzorca udostępniania.  Zobacz [Algorytm ładowania zestawu zarządzanego](loading-managed.md).

## <a name="complications"></a>Komplikacje

### <a name="type-conversion-issues"></a>Problemy z konwersją typów

Gdy <xref:System.Runtime.Loader.AssemblyLoadContext> dwa wystąpienia zawierają definicje `name`typów z tym samym , nie są one tego samego typu. Są one tego samego typu, jeśli i <xref:System.Reflection.Assembly> tylko wtedy, gdy pochodzą z tego samego wystąpienia.

Aby skomplikować sprawy, komunikaty o wyjątkach dotyczące tych niedopasowanych typów mogą być mylące. Typy są określane w komunikatach o wyjątkach przez ich proste nazwy typów. Typowy komunikat o wyjątku w tym przypadku będzie w formie:

> Obiekt typu "IsolatedType" nie może zostać przekonwertowany na typ "IsolatedType".

### <a name="debugging-type-conversion-issues"></a>Problemy z konwersją typu debugowania

Biorąc pod uwagę parę niedopasowanych typów, ważne jest również, aby wiedzieć:

- Każdy typ jest<xref:System.Type.Assembly?displayProperty=nameWithType>
- Każdy typ <xref:System.Runtime.Loader.AssemblyLoadContext>, które można uzyskać <xref:System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(System.Reflection.Assembly)?displayProperty=nameWithType> za pomocą funkcji.

Biorąc pod `a` `b`uwagę dwa obiekty i , oceny następujących w debugerze będą pomocne:

```csharp
// In debugger look at each assembly's instance, Location, and FullName
a.GetType().Assembly
b.GetType().Assembly
// In debugger look at each AssemblyLoadContext's instance and name
System.Runtime.AssemblyLoadContext.GetLoadContext(a.GetType().Assembly)
System.Runtime.AssemblyLoadContext.GetLoadContext(b.GetType().Assembly)
```

### <a name="resolving-type-conversion-issues"></a>Rozwiązywanie problemów z konwersją typów

Istnieją dwa wzorce projektowe do rozwiązywania tych problemów z konwersją typu.

1. Użyj typowych typów udostępnionych. Ten typ udostępniony może być pierwotnym typem czasu wykonywania lub może obejmować utworzenie nowego typu udostępnionego w zestawie udostępnionym.  Często typ udostępniony jest [interfejsem](../../csharp/language-reference/keywords/interface.md) zdefiniowanym w zestawie aplikacji. Zobacz też: [Jak współużytkowane są zależności?](#how-are-dependencies-shared).

2. Użyj technik organizowania do konwersji z jednego typu na inny.

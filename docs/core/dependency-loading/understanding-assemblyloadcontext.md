---
title: Opis ZestawuLoadContext - .NET Core
description: Kluczowe pojęcia, aby zrozumieć cel i zachowanie AssemblyLoadContext w .NET Core.
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 43fb0d792ddeb20b8a141af452a86dd50f37ba43
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523613"
---
# <a name="understanding-systemruntimeloaderassemblyloadcontext"></a>Opis System.Runtime.Loader.AssemblyLoadContext

Klasa <xref:System.Runtime.Loader.AssemblyLoadContext> jest unikatowa dla .NET Core. W tym artykule <xref:System.Runtime.Loader.AssemblyLoadContext> próbuje uzupełnić dokumentację interfejsu API z informacjami koncepcyjnymi.

Ten artykuł jest odpowiedni dla deweloperów implementujących ładowanie dynamiczne, szczególnie dynamicznych deweloperów platformy ładowania.

## <a name="what-is-the-assemblyloadcontext"></a>Co to jest AssemblyLoadContext?

Każda aplikacja .NET Core niejawnie używa pliku <xref:System.Runtime.Loader.AssemblyLoadContext>.
Jest dostawcą środowiska wykonawczego do lokalizowania i ładowania zależności. Za każdym razem, gdy <xref:System.Runtime.Loader.AssemblyLoadContext> zależność jest ładowana, wystąpienie jest wywoływane, aby ją zlokalizować.

- Zapewnia usługę lokalizowania, ładowania i buforowania zarządzanych zestawów i innych zależności.

- Do obsługi dynamicznego ładowania kodu i zwalniania, tworzy izolowany kontekst <xref:System.Runtime.Loader.AssemblyLoadContext> do ładowania kodu i jego zależności w ich własnym wystąpieniu.

## <a name="when-do-you-need-multiple-assemblyloadcontext-instances"></a>Kiedy potrzebujesz wielu wystąpień AssemblyLoadContext?

Pojedyncze <xref:System.Runtime.Loader.AssemblyLoadContext> wystąpienie jest ograniczone do ładowania <xref:System.Reflection.Assembly> dokładnie jednej <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>wersji nazwy zestawu prostego.

To ograniczenie może stać się problemem podczas dynamicznego ładowania modułów kodu. Każdy moduł jest kompilowany niezależnie i może <xref:System.Reflection.Assembly>zależeć od różnych wersji . Ten problem występuje często, gdy różne moduły zależą od różnych wersji powszechnie używanej biblioteki.

Aby obsługiwać dynamicznie <xref:System.Runtime.Loader.AssemblyLoadContext> ładowania kodu, interfejs API <xref:System.Reflection.Assembly> zapewnia ładowanie sprzecznych wersji w tej samej aplikacji. Każde <xref:System.Runtime.Loader.AssemblyLoadContext> wystąpienie zawiera unikatowy <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType> słownik <xref:System.Reflection.Assembly> mapowanie każdego do określonego wystąpienia.

Zapewnia również wygodny mechanizm grupowania zależności związanych z modułem kodu do późniejszego zwalniania.

## <a name="what-is-special-about-the-assemblyloadcontextdefault-instance"></a>Co jest specjalnego w przypadku wystąpienia AssemblyLoadContext.Default?

Wystąpienie <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> jest automatycznie wypełniane przez środowisko wykonawcze podczas uruchamiania.  Używa [domyślnego sondowania,](default-probing.md) aby zlokalizować i znaleźć wszystkie zależności statyczne.

Rozwiązuje najbardziej typowe scenariusze ładowania zależności.

## <a name="how-does-assemblyloadcontext-support-dynamic-dependencies"></a>W jaki sposób AssemblyLoadContext obsługuje zależności dynamiczne?

<xref:System.Runtime.Loader.AssemblyLoadContext>ma różne zdarzenia i funkcje wirtualne, które mogą być zastąpione.

Wystąpienie <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> obsługuje tylko zastępowanie zdarzeń.

Artykuły [Algorytm ładowania zestawu zarządzanego,](loading-managed.md) [Algorytm ładowania zestawu satelitarnego](loading-resources.md)i [Algorytm ładowania biblioteki niezarządzanej (natywnej)](loading-unmanaged.md) odnoszą się do wszystkich dostępnych zdarzeń i funkcji wirtualnych.  Artykuły pokazują względną pozycję każdego zdarzenia i funkcji w algorytmach ładowania. Ten artykuł nie powiela tych informacji.

Niniejsza sekcja obejmuje ogólne zasady dotyczące odpowiednich zdarzeń i funkcji.

- **Być powtarzalne**. Kwerenda dla określonej zależności musi zawsze spowodować taką samą odpowiedź. To samo załadowane wystąpienie zależności musi zostać zwrócone. To wymaganie ma podstawowe znaczenie dla spójności pamięci podręcznej. W szczególności dla zestawów zarządzanych tworzymy pamięć podręczną. <xref:System.Reflection.Assembly> Klucz pamięci podręcznej jest <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>prostą nazwą zestawu, .
- **Zazwyczaj nie rzucać**.  Oczekuje się, że te `null` funkcje zwracają, a nie zgłaszać, gdy nie można znaleźć żądanej zależności. Zgłaszanie przedwcześnie zakończy wyszukiwanie i będzie propagować wyjątek od wywołującego. Zgłaszanie powinno być ograniczone do nieoczekiwanych błędów, takich jak uszkodzony zestaw lub stan braku pamięci.
- **Unikać rekursji**. Należy pamiętać, że te funkcje i programy obsługi implementują reguły ładowania do lokalizowania zależności. Implementacja nie powinna wywoływać interfejsów API, które wyzwalają rekursję. Kod powinien zazwyczaj wywoływać **AssemblyLoadContext** funkcji ładowania, które wymagają określonej ścieżki lub argumentu odwołania do pamięci.
- **Załaduj do właściwego zestawuLoadContext**. Wybór miejsca ładowania zależności jest specyficzne dla aplikacji.  Wybór jest realizowany przez te zdarzenia i funkcje. Gdy kod wywołuje **AssemblyLoadContext** load-by-path funkcje wywołać je w wystąpieniu, w którym chcesz załadowany kod. Kiedyś powrót `null` i <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> umożliwienie uchwytowi obciążenia może być najprostszą opcją.
- **Należy pamiętać o wyścigach wątków**. Ładowanie może być wyzwalane przez wiele wątków. AssemblyLoadContext obsługuje wyścigi wątków przez atomowe dodawanie zestawów do jego pamięci podręcznej. Wystąpienie przegranego wyścigu zostaje odrzucone. W logice implementacji nie należy dodawać dodatkowej logiki, która nie obsługuje poprawnie wielu wątków.

## <a name="how-are-dynamic-dependencies-isolated"></a>Jak są izolowane zależności dynamiczne?

Każde <xref:System.Runtime.Loader.AssemblyLoadContext> wystąpienie reprezentuje <xref:System.Reflection.Assembly> unikatowy <xref:System.Type> zakres dla wystąpień i definicji.

Nie ma izolacji binarnej między tymi zależnościami. Są one tylko odizolowane, nie znajdując siebie po imieniu.

W <xref:System.Runtime.Loader.AssemblyLoadContext>każdym z nich:

- <xref:System.Reflection.AssemblyName.Name?displayProperty=nameWithType>może odnosić <xref:System.Reflection.Assembly> się do innego wystąpienia.
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>może zwrócić wystąpienie innego typu `name`dla tego samego typu .

## <a name="how-are-dependencies-shared"></a>Jak współużytkują zależności?

Zależności mogą być łatwo <xref:System.Runtime.Loader.AssemblyLoadContext> współużytkowane między wystąpieniami. Ogólny model jest <xref:System.Runtime.Loader.AssemblyLoadContext> dla jednego, aby załadować zależność.  Inne udziały zależności przy użyciu odwołania do załadowanego zestawu.

Ten udostępnianie jest wymagane z zestawów środowiska wykonawczego. Te zestawy można załadować <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>tylko do pliku . To samo jest wymagane dla `ASP.NET` `WPF`ram, `WinForms`takich jak , lub .

Zaleca się załadowanie współdzielonych zależności <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType>do . Ten udział jest wspólny wzorzec projektowania.

Udostępnianie jest implementowane w kodowaniu <xref:System.Runtime.Loader.AssemblyLoadContext> wystąpienia niestandardowego. <xref:System.Runtime.Loader.AssemblyLoadContext>ma różne zdarzenia i funkcje wirtualne, które mogą być zastąpione. Gdy którakolwiek z tych funkcji <xref:System.Reflection.Assembly> zwraca odwołanie do <xref:System.Runtime.Loader.AssemblyLoadContext> wystąpienia, <xref:System.Reflection.Assembly> które zostało załadowane w innym wystąpieniu, wystąpienie jest współużytkowane. Standardowy algorytm obciążenia <xref:System.Runtime.Loader.AssemblyLoadContext.Default?displayProperty=nameWithType> odracza się do ładowania, aby uprościć wspólny wzorzec udostępniania.  Zobacz [Algorytm ładowania zestawu zarządzanego](loading-managed.md).

## <a name="complications"></a>Komplikacje

### <a name="type-conversion-issues"></a>Problemy z konwersją typów

Gdy <xref:System.Runtime.Loader.AssemblyLoadContext> dwa wystąpienia zawierają definicje `name`typów o tej samej, nie są tego samego typu. Są tego samego typu, jeśli i tylko <xref:System.Reflection.Assembly> wtedy, gdy pochodzą z tego samego wystąpienia.

Aby skomplikować sprawy, komunikaty o wyjątkach dotyczące tych niezgodnych typów mogą być mylące. Typy są określane w komunikatach wyjątków przez ich nazwy typów prostych. Typowy komunikat wyjątek w tym przypadku będzie formularza:

> Obiekt typu "IsolatedType" nie może być konwertowany na typ "IsolatedType".

### <a name="debugging-type-conversion-issues"></a>Problemy z konwersją typu debugowania

Biorąc pod uwagę parę niedopasowanych typów, ważne jest, aby również wiedzieć:

- Każdy typ<xref:System.Type.Assembly?displayProperty=nameWithType>
- Każdy <xref:System.Runtime.Loader.AssemblyLoadContext>typ, który można uzyskać <xref:System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(System.Reflection.Assembly)?displayProperty=nameWithType> za pomocą funkcji.

Biorąc pod `a` `b`uwagę dwa obiekty i , oceny następujące w debugera będzie pomocne:

```csharp
// In debugger look at each assembly's instance, Location, and FullName
a.GetType().Assembly
b.GetType().Assembly
// In debugger look at each AssemblyLoadContext's instance and name
System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(a.GetType().Assembly)
System.Runtime.Loader.AssemblyLoadContext.GetLoadContext(b.GetType().Assembly)
```

### <a name="resolving-type-conversion-issues"></a>Rozwiązywanie problemów z konwersją typów

Istnieją dwa wzorce projektowe do rozwiązywania tych problemów konwersji typu.

1. Użyj typowych typów udostępnionych. Ten typ udostępniony może być typem pierwotnego środowiska uruchomieniowego lub może obejmować tworzenie nowego typu udostępnionego w zestawie udostępnionym.  Często typ udostępniony jest [interfejs](../../csharp/language-reference/keywords/interface.md) zdefiniowany w zestawie aplikacji. Zobacz też: [Jak współdzielone są zależności?](#how-are-dependencies-shared).

2. Użyj technik organizowania do konwersji z jednego typu do drugiego.

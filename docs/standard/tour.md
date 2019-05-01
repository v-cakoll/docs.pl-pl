---
title: Przewodnik po środowisku .NET
description: Przewodnik po przez niektóre z widocznym funkcje platformy .NET.
author: cartermp
ms.author: wiwagn
ms.date: 05/22/2017
ms.technology: dotnet-standard
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
ms.openlocfilehash: acd8e14e1d000f55f03017a4fee43347f50df3a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936308"
---
# <a name="tour-of-net"></a>Przewodnik po środowisku .NET

.NET to platforma deweloperska ogólnego przeznaczenia. Posiada kilka kluczowych funkcji, takich jak obsługa wielu języków programowania, asynchroniczne i współbieżne modele programowania i interoperacyjności macierzystej umożliwiających szerokiej gamy scenariuszy na wielu platformach.

Ten artykuł zawiera samouczek przez niektóre kluczowe funkcje programu .NET. Zobacz [składniki architektury .NET](components.md) tematu, aby dowiedzieć się więcej o części architektury .NET i ich używania.

## <a name="how-to-run-the-code-samples"></a>Sposób uruchamiania przykładów kodu

Aby dowiedzieć się, jak skonfigurować środowisko deweloperskie do uruchamiania przykładów kodu, zobacz [wprowadzenie](get-started.md) tematu. Skopiuj i Wklej przykłady kodu z tej strony w środowisku do ich wykonania. 

## <a name="programming-languages"></a>Języki programowania

.NET obsługuje wiele języków programowania. Implementowanie implementacji .NET [Common Language Infrastructure (CLI)](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/), między innymi określający niezależny od języka środowiska uruchomieniowego i interoperacyjności języka. Oznacza to, że wybierasz dowolnego języka platformy .NET do tworzenia aplikacji i usług na platformie .NET.

Firma Microsoft aktywnie opracowuje i obsługuje trzy języków .NET: C#, F#i Visual Basic (VB). 

* C# to prosta, wydajna, bezpieczne i zorientowane obiektowo, przy zachowaniu wyrazistości i elegancji stylów języka c. Każdego kto zna C i podobne języki znajduje kilka problemów w dostosowanie do języka C#. Zapoznaj się z [przewodnik C#](../csharp/index.md) Aby dowiedzieć się więcej na temat języka C#.

* F#jest międzyplatformowa, skoncentrowane na funkcjonalności język programowania, który obsługuje również tradycyjne programowanie zorientowane obiektowo i bezwzględne. Zapoznaj się z [ F# przewodnik](../fsharp/index.md) Aby dowiedzieć się więcej na temat F#.

* Visual Basic to łatwe języka, aby dowiedzieć się, że umożliwia tworzenie różnych aplikacji uruchamianych na platformie .NET. Między językami .NET składnia VB jest najbardziej zbliżony do zwykłych języka ludzi, często ułatwiając dla osób nowych do tworzenia oprogramowania.

## <a name="automatic-memory-management"></a>Automatyczne zarządzanie pamięcią

Używa .NET [wyrzucania elementów bezużytecznych (GC)](garbagecollection/index.md) umożliwia automatyczne zarządzanie pamięcią programów. GC działa z opóźnieniem podejścia do zarządzania pamięcią preferowanie przepływność aplikacji do natychmiastowego kolekcji w pamięci. Aby dowiedzieć się więcej na temat odzyskiwania pamięci platformy .NET, zapoznaj się z [podstawowe informacje na temat wyrzucania elementów bezużytecznych (GC)](garbagecollection/fundamentals.md).

Następujące dwa wiersze zarówno przydzielić pamięci:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

Istnieje nie analogiczne słowo kluczowe, aby usunąć przydział pamięci, cofnięcia przydziału jest wykonywane automatycznie, gdy moduł zbierający elementy bezużyteczne odzyskuje ilość pamięci, za pośrednictwem jego zaplanowane uruchomienie.

Moduł odśmiecania pamięci jest jednym z usług, które zapewnią *bezpieczeństwo pamięci*. Program jest bezpieczne, jeśli uzyskuje dostęp do pamięci tylko przydzielonej pamięci. Na przykład środowisko uruchomieniowe gwarantuje, że aplikacja nie mają dostęp do pamięci nieprzydzielone poza granice tablicy.

W poniższym przykładzie, środowisko wykonawcze zgłasza `InvalidIndexException` wyjątek, aby wymusić bezpieczeństwo pamięci:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="working-with-unmanaged-resources"></a>Praca z niezarządzanych zasobów

Niektóre obiekty odwołanie *niezarządzane zasoby*. Zasoby niezarządzane są zasoby, które nie są automatycznie zachowywane przez środowisko uruchomieniowe platformy .NET. Na przykład dojście do pliku jest niezarządzany zasób. A <xref:System.IO.FileStream> obiekt jest obiektem zarządzanym, lecz przywołuje dojście do pliku, który jest niezarządzany. Po zakończeniu przy użyciu <xref:System.IO.FileStream>, musisz zwolnić obsługę pliku.

Na platformie .NET, zaimplementować obiekty odwołujące się do niezarządzanych zasobów <xref:System.IDisposable> interfejsu. Po zakończeniu korzystania z obiektu, należy wywołać obiektu <xref:System.IDisposable.Dispose> metody, która odpowiada za zwolnienie niezarządzanych zasobów. Języki .NET zapewniają wygodny sposób `using` składnię obiektów, jak pokazano w poniższym przykładzie:

[!code-csharp[UnmanagedResources](../../samples/csharp/snippets/tour/UnmanagedResources.csx#L1-L6)]

Gdy `using` bloku zakończeniu środowiska uruchomieniowego .NET automatycznie wywołuje `stream` obiektu <xref:System.IDisposable.Dispose> metody, która uwalnia dojście do pliku. Środowisko uruchomieniowe wykonuje to również jeśli wyjątek powoduje, że formant pozostaw blok.

Aby uzyskać więcej informacji zobacz następujące tematy:

* Dla języka C#, zobacz [using — instrukcja (odwołanie w C#)](../csharp/language-reference/keywords/using-statement.md) tematu.
* Aby uzyskać F#, zobacz [zarządzanie zasobami: Use — słowo kluczowe](../fsharp/language-reference/resource-management-the-use-keyword.md).
* Dla języka VB, zobacz [przy użyciu — instrukcja (Visual Basic)](../visual-basic/language-reference/statements/using-statement.md) tematu.

## <a name="type-safety"></a>Bezpieczeństwo typów

Obiekt to wystąpienie określonego typu. Jedyne operacje, które są dozwolone w przypadku danego obiektu są zależne od jego typu. A `Dog` typ może mieć `Jump` i `WagTail` metody, ale nie `SumTotal` metody. Program tylko wywołuje metody należących do danego typu. Inne wywołania powoduje błąd kompilacji lub wyjątek czasu wykonywania (w przypadku używania funkcji dynamicznego lub `object`).

Języków .NET są zorientowane obiektowo z hierarchii klas podstawowych i pochodnych. Środowisko uruchomieniowe platformy .NET umożliwia tylko rzutowania obiektu i wywołania zharmonizowanych z hierarchii obiektów. Należy pamiętać, że każdy typ zdefiniowany w dowolnym języku .NET pochodzi od podstawy <xref:System.Object> typu.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L19-L23)]

Bezpieczeństwo typów umożliwia również egzekwują przestrzeganie hermetyzacji gwarantując wierności słowa kluczowe dostępu. Słowa kluczowe dostępu są artefaktów, które kontrolują dostęp do elementów członkowskich danego typu przez inny kod. Są one zazwyczaj używane dla różnych rodzajów danych w ramach danego typu, które są używane do zarządzania jego zachowanie.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#, VB i F# lokalnej pomocy technicznej *wnioskowanie o typie*. Wnioskowanie o typie oznacza, że kompilator określi typ wyrażenia po lewej stronie wyrażenia po prawej stronie. Nie oznacza to, że bezpieczeństwa typu jest uszkodzony lub unikać. Wynikowy typ ma silnego typu wszystko kojarzący się. W poprzednim przykładzie `dog` jest przepisane, aby wprowadzić wnioskowanie o typie, i ulega w pozostałej części przykładu:

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F#ma nawet dodatkowe możliwości wnioskowania typu niż wnioskowanie o typie metody lokalnej znaleziony w C# i VB. Aby dowiedzieć się więcej, zobacz [wnioskowanie o typie](../fsharp/language-reference/type-inference.md).

## <a name="delegates-and-lambdas"></a>Delegaci i wyrażenia lambda

Obiekt delegowany jest reprezentowany przez podpis metody. Dowolną metodą mającą ten podpis delegata można przypisać i jest wykonywany, gdy obiekt delegowany jest wywoływany.

Delegaty są podobne do wskaźników funkcji języka C++, z tą różnicą, że są one bezpieczne dla typów. Są one rodzaj odłączonego metody w ramach systemu typu CLR. Regularne metody są dołączone do klasy i są tylko bezpośrednio wywoływane za pośrednictwem statyczne lub wywoływania wystąpienia Konwencji.

Na platformie .NET obiekty delegowane są często używane w procedurze obsługi zdarzeń, definiując operacji asynchronicznych i w wyrażeniach lambda, które są podstawą LINQ. Dowiedz się więcej w [delegaci i wyrażenia lambda](delegates-lambdas.md) tematu.

## <a name="generics"></a>Typy ogólne

Ogólne umożliwić programiście wprowadzenie *parametr typu* podczas projektowania ich klasy, które umożliwia określenie dokładnie tego samego typu należy użyć zamiast parametru typu przez kod klienta (użytkownicy typu).

Typy ogólne zostały dodane do pomocy ekspertów w programowaniu w implementacji struktur danych typu ogólnego. Przed ich przybyciem kolejności dla typu, takie jak `List` typ ma być ogólna, będzie trzeba pracować z elementami, które były typu `object`. To było różnych semantycznego problemów, wraz z błędów możliwych subtelne środowiska uruchomieniowego i wydajności. Jest najbardziej notorious drugiego, gdy zawiera strukturę danych, na przykład liczby całkowite i ciągi, a `InvalidCastException` jest generowany na temat pracy z listy członków.

Poniższy przykład pokazuje podstawowe programu przy użyciu wystąpienia <xref:System.Collections.Generic.List%601> typów:

[!code-csharp[GenericsShort](../../samples/csharp/snippets/tour/GenericsShort.csx)]

Aby uzyskać więcej informacji, zobacz [ogólnych typów (Ogólne) — omówienie](generics.md) tematu.

## <a name="async-programming"></a>Programowanie asynchroniczne

Programowanie asynchroniczne jest najwyższej jakości pojęcie w ramach platformy .NET przy użyciu asynchroniczna pomoc techniczna w środowisku uruchomieniowym bibliotek platformy i konstrukcji języka .NET. Wewnętrznie, są oparte na obiektach (takie jak `Task`), który zalet systemu operacyjnego do wykonywania zadań I/O-granicę w jak najbardziej wydajny.

Aby dowiedzieć się więcej na temat programowania asynchronicznego w .NET, zacznij od [Przegląd Async](async.md) tematu.

## <a name="language-integrated-query-linq"></a>Language Integrated Query (LINQ)

LINQ to zaawansowany zestaw funkcji języka C# i VB, które umożliwiają pisanie prostego, deklaratywnego kod działających na danych. Dane mogą być w wielu formularzach (np. obiektów w pamięci, bazie danych SQL lub dokumentu XML), ale tworzonego zazwyczaj kodu LINQ nie różnią się od źródła danych.

Aby dowiedzieć się więcej i zobacz przykłady, zobacz [LINQ (Language Integrated Query)](using-linq.md) tematu.

## <a name="native-interoperability"></a>Współdziałanie natywne

Każdy system operacyjny, obejmuje interfejs programowania aplikacji (API), które świadczy usługi systemu. .NET oferuje kilka sposobów, aby wywołać tych interfejsów API.

Główne sposób interoperacyjności macierzystej jest za pośrednictwem "wywołania platformy" lub P/Invoke w skrócie, który jest obsługiwany na platformach Windows i Linux. Windows — tylko w sposób interoperacyjności macierzystej jest znany jako "Usługa międzyoperacyjna modelu COM," który jest używany do pracy z [składników COM](/cpp/atl/introduction-to-com) w kodzie zarządzanym. Jest on oparty na szczycie infrastruktury P/Invoke, ale działa w niewielkim stopniu różne sposoby.

Większość przez narzędzie Mono (i w związku z tym Xamarin) współdziałanie obsługę języka Java i języka Objective-C są zbudowane Analogicznie, oznacza to, że używają tych samych zasad.

Aby uzyskać więcej informacji na temat interoperacyjności macierzystej zobacz [interoperacyjności macierzystej](native-interop/index.md) artykułu.

## <a name="unsafe-code"></a>Niebezpieczny kod

W zależności od języka pomocy technicznej, CLR umożliwia dostęp do pamięci natywnej i wykonać arytmetyki wskaźnika za pomocą `unsafe` kodu. Te operacje są wymagane dla pewnych algorytmów i współdziałania systemu. Mimo że jest to wydajne, użyj niebezpieczny kod nie jest zalecane, chyba że jest niezbędne do współdziałania z interfejsów API systemu, lub implementować algorytm najbardziej efektywny sposób. Niebezpieczny kod nie może być wykonywane tak samo w różnych środowiskach i utraci również zalety modułu odśmiecania pamięci i bezpieczeństwo typów. Zaleca się ograniczenie oraz scentralizowanie możliwie niebezpieczny kod i dokładnie przetestuj kod.

Poniższy przykład to zmodyfikowana wersja `ToString()` metody z `StringBuilder` klasy. Przykład ilustruje jak przy użyciu `unsafe` kodu efektywnie można implementować algorytm gry przez poruszanie fragmentów pamięci bezpośrednio:

[!code-csharp[Unsafe](../../samples/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>Następne kroki

Jeśli interesuje Cię prezentacją funkcji w języku C#, zapoznaj się z [samouczka dla języka C#](../csharp/tour-of-csharp/index.md).

Jeśli interesuje Cię z przewodnikiem dotyczącym F# funkcje, zobacz [Przewodnik po przykładzie F# ](../fsharp/tour.md).

Jeśli chcesz rozpocząć pisanie kodu własny, odwiedź stronę [wprowadzenie](get-started.md).

Aby poznać ważne składniki .NET, zapoznaj się z [składniki architektury .NET](components.md).

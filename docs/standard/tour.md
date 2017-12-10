---
title: Samouczek platformy .NET
description: "Przewodnik po niektóre z widocznym funkcje platformy .NET."
keywords: ".NET, .NET core samouczek, programowania bezpieczeństwa typu języków zagrożenie, zarządzania pamięcią, Async"
author: cartermp
ms.author: wiwagn
ms.date: 05/22/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
ms.openlocfilehash: dd4062905b38f4dff99c03c9bb3849ac3b552e5d
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="tour-of-net"></a>Samouczek platformy .NET

.NET jest to platforma programistyczna ogólnego przeznaczenia. Ma ona najważniejsze funkcje, takie jak obsługa wielu języków programowania, modele programowania asynchronicznego i równoczesnych i natywnego współdziałanie umożliwiające szerokiego zakresu scenariuszy na wielu platformach.

Ten artykuł zawiera przewodnik niektóre z kluczowych funkcji programu .NET. Zobacz [składników architektury .NET](components.md) tematu, aby dowiedzieć się więcej o fragmentów architektury .NET i ich używać.

## <a name="how-to-run-the-code-samples"></a>Jak uruchomić przykłady kodu

Aby dowiedzieć się, jak skonfigurować środowisko deweloperskie do uruchamiania przykładów kodu, zobacz [wprowadzenie](get-started.md) tematu. Skopiuj i Wklej przykłady kodu z tej strony do środowiska, aby je wykonać. 

## <a name="programming-languages"></a>Języki programowania

.NET obsługuje wiele języków programowania. Implementowanie implementacje .NET [infrastruktury języka wspólnego (CLI)](https://www.visualstudio.com/license-terms/ecma-c-common-language-infrastructure-standards/), między innymi określającej współdziałania środowisko uruchomieniowe i język niezależny od języka. Oznacza to, że wybrano żadnego języka .NET do tworzenia aplikacji i usług na platformie .NET.

Firma Microsoft aktywnie rozwija i obsługuje trzech językach .NET: C#, F # i Visual Basic (VB). 

* C# jest proste, zaawansowane, bezpieczne i zorientowane obiektowo przy zachowaniu wyrazistość i przejrzysty wygląd stylu języka C języków. Każda osoba, która zapoznać się z C i podobne języki znajduje kilka problemów w dostosowywaniu C#. Zapoznaj się z [przewodnik C#](../csharp/index.md) Aby dowiedzieć się więcej na temat języka C#.

* F # i platform, funkcjonalny język programowania, który również obsługuje tradycyjne programowanie zorientowane obiektowo i konieczne jest. Zapoznaj się z [przewodnik F #](../fsharp/index.md) Aby dowiedzieć się więcej na temat języka F #.

* Visual Basic jest łatwe języka Aby dowiedzieć się, umożliwia tworzenie różnych aplikacji uruchamianych na platformie .NET. Między językami .NET składnia VB jest najbardziej zbliżony do zwykłych języka ludzi, często ułatwieniu dla osób nowych do rozwoju oprogramowania.

## <a name="automatic-memory-management"></a>Automatyczne zarządzanie pamięcią

Używa .NET [wyrzucanie elementów bezużytecznych (GC)](garbagecollection/index.md) aby zapewnić automatyczne zarządzanie pamięcią dla programów. Wykaz Globalny działa na opóźnieniem podejście do zarządzania pamięcią preferowanie przepływność aplikacji do natychmiastowego kolekcji pamięci. Aby dowiedzieć się więcej na temat .NET GC, zapoznaj się [podstawy dotyczące wyrzucania elementów bezużytecznych (GC)](garbagecollection/fundamentals.md).

Następujące dwa wiersze zarówno przydzielić pamięci:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

Brak — słowo kluczowe nie analogiczne do przydzielić pamięci, dezaktywowanie alokacji jest wykonywana automatycznie, gdy moduł garbage collector zwraca pamięci za pomocą jego planowanym uruchomieniu.

Moduł zbierający elementy bezużyteczne to jedna z usług, które ułatwiają zapewnienie *bezpieczeństwa pamięci*. Program jest bezpieczne, jeśli uzyskuje dostęp do pamięci tylko przydzielonej pamięci. Na przykład środowiska uruchomieniowego zapewnia, że aplikacja nie dostęp do pamięci nieprzydzielonego poza granice tablicy.

W poniższym przykładzie zgłasza wyjątek środowiska uruchomieniowego `InvalidIndexException` wyjątku, aby wymusić bezpieczeństwa pamięci:

[!code-csharp[MemoryManagement](../../samples/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="working-with-unmanaged-resources"></a>Praca z zasobów niezarządzanych

Odwołanie do niektórych obiektów *niezarządzane zasoby*. Niezarządzane zasoby są elementami, które nie są automatycznie zachowywane przez środowisko uruchomieniowe platformy .NET. Na przykład dojście do pliku jest niezarządzanym zasobem. A <xref:System.IO.FileStream> obiekt jest obiektem zarządzanym, ale odwołuje się do dojścia do pliku, który będzie zarządzany. Po zakończeniu przy użyciu <xref:System.IO.FileStream>, musisz zwolnić dojście do pliku.

W środowisku .NET, zaimplementować obiekty, które odwołują się niezarządzane zasoby <xref:System.IDisposable> interfejsu. Po zakończeniu przy użyciu obiektu, należy wywołać obiektu <xref:System.IDisposable.Dispose> metodę, która jest odpowiedzialna za zwolnienie żadnych niezarządzanych zasobów. Zapewnić wygodny sposób języków .NET `using` składnię takie obiekty, jak pokazano w poniższym przykładzie:

[!code-csharp[UnmanagedResources](../../samples/csharp/snippets/tour/UnmanagedResources.csx#L1-L6)]

Raz `using` zakończeniu bloku, środowisko uruchomieniowe platformy .NET automatycznie wywołuje `stream` obiektu <xref:System.IDisposable.Dispose> metodę, która zwalnia dojście do pliku. Środowisko uruchomieniowe robi to także jeśli wyjątek powoduje, że formant pozostaw blok.

Aby uzyskać więcej informacji zobacz następujące tematy:

* Język C#, zobacz [using — instrukcja (odwołanie w C#)](../csharp/language-reference/keywords/using-statement.md) tematu.
* W F #, zobacz [zarządzanie zasobami: use — słowo kluczowe](../fsharp/language-reference/resource-management-the-use-keyword.md).
* Dla VB, zobacz [przy użyciu — instrukcja (Visual Basic)](../visual-basic/language-reference/statements/using-statement.md) tematu.

## <a name="type-safety"></a>Zabezpieczenie typów

Obiekt jest wystąpienia określonego typu. Tylko operacje dozwolone dla danego obiektu są jego typu. A `Dog` typ może mieć `Jump` i `WagTail` metody, ale nie `SumTotal` metody. Program tylko wywołuje metody należących do danego typu. Inne wywołania spowodować błąd kompilacji lub wyjątek czasu wykonywania (w przypadku używania funkcji dynamicznego lub `object`).

Języków .NET są zorientowane obiektowo z hierarchii klas podstawowych i pochodnych. Środowisko uruchomieniowe platformy .NET umożliwia tylko rzutowania obiektu i wywołania, które są wyrównane z hierarchii obiektów. Należy pamiętać, że każdy typ zdefiniowany w dowolnym języku .NET pochodzi od podstawy <xref:System.Object> typu.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L19-L23)]

Zabezpieczenie typów umożliwia również ułatwić wymuszenie hermetyzacji gwarantując dokładność słowa kluczowe dostępu. Słowa kluczowe dostępu są artefaktów, które kontrolują dostęp do członków danego typu przez inny kod. Te są zwykle stosowane dla różnych typów danych w określonym typie, które są używane do zarządzania jego zachowania.

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#, VB i F # obsługuje lokalnego *wnioskowanie typu*. Wnioskowanie o typie oznacza, że kompilator deduces typ wyrażenia po lewej stronie wyrażenia po prawej stronie. To nie oznacza to, że bezpieczeństwo typów jest uszkodzony lub unikać. Wynikowy typ ma silnego typu z wszystko, co oznacza. W poprzednim przykładzie `dog` i `cat` są ulegną wprowadzenie wnioskowanie o typie, i różni się w pozostałej części przykładzie:

[!code-csharp[TypeSafety](../../samples/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F # jeszcze bardziej ma typ wnioskowania możliwości niż lokalne metody wnioskowanie znalezionych w języku C# i VB. Aby dowiedzieć się więcej, zobacz [wnioskowanie o typie](../fsharp/language-reference/type-inference.md).

## <a name="delegates-and-lambdas"></a>Delegaci i wyrażeń lambda

Delegat jest reprezentowana przez podpis metody. Dowolnej metody tego podpisem można przypisać do obiektu delegowanego i jest wykonywane, gdy jest wywoływany delegat.

Obiekty delegowane są podobne do wskaźników funkcji języka C++, z wyjątkiem tego, że są one bezpieczne typu. Są one rodzaj odłączonego metody w systemie typów CLR. Regularne metody są powiązane z klasą i są tylko bezpośrednio można wywołać za pomocą statyczny lub wywołaniem wystąpienia Konwencji.

W środowisku .NET delegatów są często używane w programów obsługi zdarzeń, definiując operacji asynchronicznych i wyrażenia lambda, które są podstawy LINQ. Dowiedz się więcej w [delegaci i wyrażeń lambda](delegates-lambdas.md) tematu.

## <a name="generics"></a>Typy ogólne

Zezwalaj na ogólne programisty wprowadzenie *parametr typu* podczas projektowania ich klasy, które umożliwia określenie dokładnego typu zastępującą parametr typu kodu klienta (użytkownicy typu).

Typy ogólne zostały dodane do pomocy programistów zaimplementować struktur danych typu ogólnego. Przed ich przybyciem kolejności dla typu, takich jak `List` wpisz, aby wartość była ogólna, będzie musiał pracować z elementami, które były typu `object`. Ma to różnych semantycznego problemów, wraz z błędy podczas wykonywania niewielkie możliwe i wydajności. Jest najbardziej odpowiedzialne tych przy zawiera struktury danych, na przykład liczby całkowite i ciągi oraz `InvalidCastException` jest zgłaszany na temat pracy z listy członków.

Poniższy przykład przedstawia działającego programu podstawowe za pomocą wystąpienia <xref:System.Collections.Generic.List%601> typów:

[!code-csharp[GenericsShort](../../samples/csharp/snippets/tour/GenericsShort.csx)]

Aby uzyskać więcej informacji, zobacz [ogólne typy (Ogólne) — omówienie](generics.md) tematu.

## <a name="async-programming"></a>Programowanie asynchroniczne

Programowanie asynchroniczne to pojęcie pierwszą klasą w .NET z obsługą asynchronicznych w czasie wykonywania, biblioteki framework oraz konstrukcji języka .NET. Wewnętrznie, są one oparte na obiekty (takie jak `Task`), który wykorzystać do wykonywania zadań I/E-granica jak najbardziej wydajny system operacyjny.

Aby dowiedzieć się więcej na temat programowania asynchronicznego w programie .NET, Rozpocznij od [omówienie Async](async.md) tematu.

## <a name="language-integrated-query-linq"></a>Język zapytania zintegrowanym (LINQ)

LINQ to zaawansowany zestaw funkcji języka C# i VB, dzięki którym można napisać kod prosty, deklaratywny pracy na danych. Dane mogą być w wielu formularzach (np. obiektów w pamięci, bazą danych SQL lub dokument XML), ale zazwyczaj programowanego kodu LINQ nie różnią się od źródła danych.

Aby dowiedzieć się więcej i zobaczyć niektóre przykłady, zobacz [LINQ (zapytania zintegrowane języka)](using-linq.md) tematu.

## <a name="native-interoperability"></a>Współdziałanie natywnego

Każdy system operacyjny, obejmuje interfejs programowania aplikacji (API), który udostępnia usług systemowych. .NET udostępnia kilka metod wywoływania tych interfejsów API.

Główne sposobów natywnego współdziałanie odbywa się za pośrednictwem "wywołanie platformy" lub P/Invoke skrócie, który jest obsługiwany na platformach systemu Linux i Windows. Tylko do systemu Windows w sposób możliwie natywnego współdziałanie nazywa się "Usługa międzyoperacyjna modelu COM," który jest używany do pracy z [składniki COM](/cpp/atl/introduction-to-com) w kodzie zarządzanym. Jest oparty na szczycie infrastruktury P/Invoke, ale działa w niewielkim stopniu różne sposoby.

Większość jego Mono (i w związku z tym w Xamarin) współdziałanie obsługę języka Java i Objective-C są wbudowane podobnie, oznacza to, używają tych samych zasad.

Dowiedz się więcej o natywnych współdziałanie w [natywnego współdziałanie](native-interop.md) tematu.

## <a name="unsafe-code"></a>Kod niezabezpieczony

W zależności od obsługi language CLR umożliwia dostęp do pamięci natywnej i wykonać arytmetyki wskaźnika za pośrednictwem `unsafe` kodu. Operacje te są wymagane dla niektórych algorytmów i współdziałanie systemu. Chociaż wydajne, użyj niebezpieczny kod nie jest zalecane chyba że jest współdziałanie z interfejsów API systemu, lub wdrożyć najbardziej efektywny algorytmu. Niebezpieczny kod nie może wykonać taki sam sposób jak w różnych środowiskach i również utraci zalety modułu zbierającego elementy bezużyteczne i bezpieczeństwo typów. Zaleca się ograniczenie i scentralizowanie możliwie niebezpieczny kod i dokładnie przetestuj kodu.

Poniższy przykład jest zmodyfikowanej wersji `ToString()` metody `StringBuilder` klasy. Zastosowano jak polecenie `unsafe` kodu wydajnie można wdrożyć algorytm przy bezpośrednio przenoszenia fragmentów pamięci:

[!code-csharp[Unsafe](../../samples/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>Następne kroki

Jeśli interesuje Cię Przewodnik po funkcji C#, zapoznaj się [samouczek z C#](../csharp/tour-of-csharp/index.md).

Jeśli interesuje Cię Przewodnik po funkcji F #, zobacz [samouczek programu F #](../fsharp/tour.md).

Jeśli chcesz rozpocząć pisanie kodu własny, odwiedź stronę [wprowadzenie](get-started.md).

Informacje na temat ważnych składników platformy .NET, zapoznaj się [składników architektury .NET](components.md).

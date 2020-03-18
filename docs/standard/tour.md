---
title: Przewodnik po środowisku .NET
description: Wycieczka z przewodnikiem po niektórych znanych funkcjach .NET.
author: cartermp
ms.author: wiwagn
ms.date: 05/22/2017
ms.technology: dotnet-standard
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
ms.openlocfilehash: 61d4792b1f1b92dd59442ee38810da96c6cf63bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241146"
---
# <a name="tour-of-net"></a>Przewodnik po środowisku .NET

.NET jest platformą deweloperska ogólnego przeznaczenia. Posiada kilka kluczowych funkcji, takich jak obsługa wielu języków programowania, asynchroniczne i równoczesne modele programowania i natywnej interoperacyjności, które umożliwiają szeroki zakres scenariuszy na wielu platformach.

Ten artykuł zawiera przewodnik po niektórych kluczowych funkcjach .NET. Zobacz [temat składników architektury .NET,](components.md) aby dowiedzieć się więcej o elementach architektury .NET i do czego są używane.

## <a name="how-to-run-the-code-samples"></a>Jak uruchomić przykłady kodu

Aby dowiedzieć się, jak skonfigurować środowisko programistyczne do uruchamiania przykładów kodu, zobacz [Wprowadzenie do](get-started.md) tematu. Skopiuj i wklej przykłady kodu z tej strony do środowiska, aby je wykonać.

## <a name="programming-languages"></a>Języki programowania

.NET obsługuje wiele języków programowania. Implementacje .NET implementują [infrastrukturę języka wspólnego (CLI),](https://visualstudio.microsoft.com/license-terms/ecma-c-common-language-infrastructure-standards/)która między innymi określa niezależne od języka działanie wykonawcze i współdziałanie języka. Oznacza to, że do tworzenia aplikacji i usług w usłudze .NET można wybrać dowolny język .NET.

Firma Microsoft aktywnie opracowuje i obsługuje trzy języki .NET: C#, F# i Visual Basic.

* C# jest proste, wydajne, bezpieczne dla typu i zorientowane obiektowe, zachowując wyrazistość i elegancję języków w stylu C. Każdy, kto zna C i podobne języki, ma kilka problemów z dostosowaniem się do języka C#. Zapoznaj się z [przewodnikiem po języku C#,](../csharp/index.yml) aby dowiedzieć się więcej o języku C#.

* F# jest wieloplatformowym, funkcjonalnym językiem programowania, który obsługuje również tradycyjne programowanie obiektowe i imperatywne. Zapoznaj się [z przewodnikiem F#,](../fsharp/index.yml) aby dowiedzieć się więcej o F#.

* Visual Basic to łatwy język, który można nauczyć się, że używasz do tworzenia różnych aplikacji, które są uruchamiane w programie .NET. Wśród języków .NET składnia języka Visual Basic jest najbliższa zwykłemu językowi ludzkiemu, co często ułatwia osobom nowym w tworzeniu oprogramowania.

## <a name="automatic-memory-management"></a>Automatyczne zarządzanie pamięcią

.NET używa [wyrzucania elementów bezużytecznych (GC)](garbage-collection/index.md) w celu zapewnienia automatycznego zarządzania pamięcią dla programów. GC działa na powolne podejście do zarządzania pamięcią, preferując przepływność aplikacji do natychmiastowego zbierania pamięci. Aby dowiedzieć się więcej o .NET GC, zapoznaj się [z podstawowymi kwotami wyrzucania elementów bezużytecznych (GC).](garbage-collection/fundamentals.md)

Następujące dwa wiersze przydzielają pamięć:

[!code-csharp[MemoryManagement](../../samples/snippets/csharp/snippets/tour/MemoryManagement.csx#L1-L2)]

Nie ma analogiczne słowo kluczowe do de-allocate pamięci, jak de-alokacji dzieje się automatycznie, gdy moduł zbierający elementy bezużyteczne odzyskuje pamięć za pośrednictwem zaplanowanego uruchomienia.

Moduł zbierający elementy bezużyteczne jest jedną z usług, które pomagają zapewnić *bezpieczeństwo pamięci*. Program jest bezpieczny w pamięci, jeśli uzyskuje dostęp tylko do przydzielonej pamięci. Na przykład program runtime zapewnia, że aplikacja nie uzyskuje dostępu do nieprzydzielonej pamięci poza granicami tablicy.

W poniższym przykładzie runtime zgłasza <xref:System.IndexOutOfRangeException> wyjątek, aby wymusić bezpieczeństwo pamięci:

[!code-csharp[MemoryManagement](../../samples/snippets/csharp/snippets/tour/MemoryManagement.csx#L4-L5)]

## <a name="working-with-unmanaged-resources"></a>Praca z zasobami niezarządzanymi

Niektóre obiekty odwołują się do *zasobów niezarządzanych*. Zasoby niezarządzane to zasoby, które nie są automatycznie obsługiwane przez program .NET. Na przykład dojście pliku jest zasobem niezarządzanym. Obiekt <xref:System.IO.FileStream> jest obiektem zarządzanym, ale odwołuje się do dojścia do pliku, który jest niezarządzany. Po zakończeniu korzystania z <xref:System.IO.FileStream>programu , należy zwolnić uchwyt pliku.

W platformie .NET obiekty, które <xref:System.IDisposable> odwołują się do zasobów niezarządzanych implementują interfejs. Po zakończeniu korzystania z obiektu, wywołać <xref:System.IDisposable.Dispose> metodę obiektu, który jest odpowiedzialny za zwolnienie żadnych zasobów niezarządzanych. Języki .NET zapewniają wygodną [ `using` instrukcję](../csharp/language-reference/keywords/using.md) dla takich obiektów, jak pokazano w poniższym przykładzie:

[!code-csharp[UnmanagedResources](../../samples/snippets/csharp/snippets/tour/UnmanagedResources.csx#L1-L6)]

Po `using` zakończeniu bloku program .NET automatycznie wywołuje `stream` <xref:System.IDisposable.Dispose> metodę obiektu, która zwalnia dojście do pliku. Środowiska uruchomieniowego również robi to, jeśli wyjątek powoduje formantu opuścić blok.

Aby uzyskać więcej informacji, zobacz następujące tematy:

* W przypadku języka C#, zobacz [using Instrukcji (C# Odwołanie)](../csharp/language-reference/keywords/using-statement.md) temat.
* Aby uzyskać f#, zobacz [Zarządzanie zasobami: użycie słowa kluczowego](../fsharp/language-reference/resource-management-the-use-keyword.md).
* W języku Visual Basic zobacz [temat Using Statement (Visual Basic).](../visual-basic/language-reference/statements/using-statement.md)

## <a name="type-safety"></a>Bezpieczeństwo typów

Obiekt jest wystąpieniem określonego typu. Tylko operacje dozwolone dla danego obiektu są te jego typu. Typ `Dog` może `Jump` mieć `WagTail` i metody, `SumTotal` ale nie metody. Program wywołuje tylko metody należące do danego typu. Wszystkie inne wywołania powodują błąd w czasie kompilacji lub wyjątek w czasie `object`wykonywania (w przypadku korzystania z funkcji dynamicznych lub ).

Języki .NET są zorientowane obiektowe z hierarchiami klas podstawowych i pochodnych. Program runtime .NET zezwala tylko na rzuty obiektowe i wywołania wyrównane z hierarchią obiektów. Należy pamiętać, że każdy typ zdefiniowany w <xref:System.Object> dowolnym języku .NET pochodzi od typu podstawowego.

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L19-L23)]

Bezpieczeństwo typów jest również używany do wymuszania hermetyzacji, gwarantując wierność słów kluczowych akcesora. Słowa kluczowe akcesora są artefakty, które kontrolują dostęp do elementów członkowskich danego typu przez inny kod. Są one zwykle używane dla różnych rodzajów danych w ramach typu, które są używane do zarządzania jego zachowanie.

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L3-L3)]

C#, Visual Basic i F# obsługują *wnioskowanie o typach*lokalnych . Wnioskowanie o typie oznacza, że kompilator wywnioskował typ wyrażenia po lewej stronie z wyrażenia po prawej stronie. Nie oznacza to, że bezpieczeństwo typu jest uszkodzone lub unikane. Wynikowy typ ma silny typ ze wszystkim, co implikuje. Z poprzedniego przykładu `dog` jest przepisany, aby wprowadzić wnioskowanie o typie, a pozostała część przykładu pozostaje bez zmian:

[!code-csharp[TypeSafety](../../samples/snippets/csharp/snippets/tour/TypeSafety.csx#L28-L34)]

F# ma jeszcze więcej możliwości wnioskowania typu niż wnioskowanie typu lokalnego metody znaleźć w języku C# i Visual Basic. Aby dowiedzieć się więcej, zobacz [Wnioskowanie o typie](../fsharp/language-reference/type-inference.md).

## <a name="delegates-and-lambdas"></a>Delegaci i wyrażenia lambda

Pełnomocnik jest reprezentowany przez podpis metody. Dowolną metodę z tym podpisem można przypisać do pełnomocnika i jest wykonywana po wywołaniu pełnomocnika.

Delegatów są jak wskaźniki funkcji C++, z tą różnicą, że są one typu bezpieczne. Są one rodzajem odłączonej metody w systemie typu CLR. Regularne metody są dołączone do klasy i są bezpośrednio wywoływane za pośrednictwem konwencji statycznych lub wywołania wystąpienia.

W .NET delegatów są powszechnie używane w programach obsługi zdarzeń, w definiowaniu operacji asynchronicznych i w wyrażeniach lambda, które są kamieniem węgielnym LINQ. Dowiedz się więcej w [temacie Delegatowie i lambdas.](delegates-lambdas.md)

## <a name="generics"></a>Typy ogólne

Rodzajowe pozwalają programisty wprowadzić *parametr typu* podczas projektowania ich klas, który umożliwia kod klienta (użytkowników typu) aby określić dokładny typ do użycia zamiast parametru typu.

Ogólne zostały dodane, aby pomóc programistom we wdrażaniu ogólnych struktur danych. Przed ich przybyciem, aby typ, `List` taki jak typ, był ogólny, musiałby pracować `object`z elementami typu . Miało to różne problemy z wydajnością i semantyczne, a także możliwe subtelne błędy w czasie wykonywania. Typowy błąd w czasie wykonywania jest, gdy struktura danych zawiera, na przykład, <xref:System.InvalidCastException> zarówno liczby całkowite i ciągi, a zostanie wygenerowany podczas przetwarzania członków listy.

W poniższym przykładzie przedstawiono podstawowy program <xref:System.Collections.Generic.List%601> uruchomiony przy użyciu wystąpienia typów:

[!code-csharp[GenericsShort](../../samples/snippets/csharp/snippets/tour/GenericsShort.csx)]

Aby uzyskać więcej informacji, zobacz ogólny [temat omówienie typów ogólnych (generyki).](generics.md)

## <a name="async-programming"></a>Programowanie asynchroniczne

Programowanie asynchroniczne to koncepcja pierwszej klasy w ramach platformy .NET z obsługą asynchroniczną w czasie wykonywania, bibliotekach framework i konstrukcjach języka .NET. Wewnętrznie są one oparte na obiektach (takich jak), `Task`które wykorzystują system operacyjny do wykonywania zadań związanych z we/wy tak wydajnie, jak to możliwe.

Aby dowiedzieć się więcej o programowaniu asynchronicznym w programie .NET, rozpocznij od tematu [asynchronicznego przeglądu.](async.md)

## <a name="language-integrated-query-linq"></a>Language Integrated Query (LINQ)

LINQ to zaawansowany zestaw funkcji dla języka C# i Visual Basic, które umożliwiają pisanie prostego, deklaratywnego kodu do obsługi danych. Dane mogą być w wielu formach (takich jak obiekty w pamięci, bazy danych SQL lub dokumentu XML), ale kod LINQ, który piszesz zazwyczaj nie różni się od źródła danych.

Aby dowiedzieć się więcej i wyświetlić niektóre przykłady, zobacz [LINQ (Language Integrated Query)](using-linq.md) temat.

## <a name="native-interoperability"></a>Współdziałanie natywne

Każdy system operacyjny zawiera interfejs programowania aplikacji (API), który zapewnia usługi systemowe. .NET udostępnia kilka sposobów wywoływania tych interfejsów API.

Głównym sposobem na natywną interoperacyjność jest za pośrednictwem "platforminvoke" lub P/Invoke w skrócie, który jest obsługiwany na platformach Linux i Windows. Tylko system Windows sposób wykonywania natywnej współdziałania jest znany jako "COM interop", który jest używany do pracy ze [składnikami COM](/cpp/atl/introduction-to-com) w kodzie zarządzanym. Jest zbudowany na górze infrastruktury P/Invoke, ale działa na subtelnie różne sposoby.

Większość wsparcia interoperacyjności Mono (a tym samym Xamarin' s) dla Java i Objective-C są zbudowane podobnie, to znaczy, że używają tych samych zasad.

Aby uzyskać więcej informacji na temat współdziałania natywnej, zobacz [native interoperability](native-interop/index.md) article.

## <a name="unsafe-code"></a>Niebezpieczny kod

W zależności od obsługi języka CLR umożliwia dostęp do pamięci natywnej i arytmetykę wskaźnika za pomocą `unsafe` kodu. Operacje te są potrzebne dla niektórych algorytmów i interoperacyjności systemu. Mimo że zaawansowane, użycie niebezpiecznego kodu jest odradzane, chyba że jest to konieczne do współdziałania z interfejsami API systemu lub zaimplementować najbardziej wydajny algorytm. Niebezpieczny kod może nie wykonywać w ten sam sposób w różnych środowiskach, a także traci korzyści z modułu odśmiecania pamięci i bezpieczeństwa typu. Zaleca się, aby ograniczyć i scentralizować niebezpieczny kod jak najwięcej i dokładnie przetestować ten kod.

Poniższy przykład jest zmodyfikowaną `ToString()` wersją `StringBuilder` metody z klasy. Ilustruje, `unsafe` jak za pomocą kodu można wydajnie zaimplementować algorytm, przenosząc bezpośrednio fragmenty pamięci:

[!code-csharp[Unsafe](../../samples/snippets/csharp/snippets/tour/Unsafe.csx)]

## <a name="next-steps"></a>Następne kroki

Jeśli jesteś zainteresowany zwiedzaniem funkcji języka C#, zapoznaj się [z przewodnikiem po języku C#.](../csharp/tour-of-csharp/index.md)

Jeśli jesteś zainteresowany zwiedzaniem funkcji Języka F#, zobacz [Przewodnik po F#](../fsharp/tour.md).

Jeśli chcesz rozpocząć pisanie własnego kodu, odwiedź [stronę Wprowadzenie.](get-started.md)

Aby dowiedzieć się więcej o ważnych składnikach .NET, zapoznaj się z [komponentami architektury .NET](components.md).

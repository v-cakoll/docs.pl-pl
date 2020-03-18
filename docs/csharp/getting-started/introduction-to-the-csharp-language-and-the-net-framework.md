---
title: Wprowadzenie do języka C# i systemu .NET Framework
description: Poznaj podstawy języków C# i .NET. Zapoznaj się z omówieniem języka Języka C# i ekosystemu .NET.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: d2fd879203932ea3f2211e38a2efdd626928962b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713910"
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>Wprowadzenie do języka Języka C# i platformy .NET Framework

C# to elegancki i bezpieczny dla typu język obiektowy, który umożliwia deweloperom tworzenie różnych bezpiecznych i niezawodnych aplikacji uruchamianych w ramach .NET Framework. C# służy do tworzenia aplikacji klienckich systemu Windows, usług sieci Web XML, składników rozproszonych, aplikacji klient-serwer, aplikacji baz danych i wiele, wiele więcej. Visual C# zapewnia zaawansowany edytor kodu, wygodnych projektantów interfejsu użytkownika, zintegrowanego debugera i wielu innych narzędzi, aby ułatwić tworzenie aplikacji opartych na języku C# i .NET Framework.  
  
> [!NOTE]
> Dokumentacja języka Visual C# zakłada, że masz zrozumienie podstawowych pojęć programowania. Jeśli jesteś początkującym początkującym, możesz chcieć eksplorować program Visual C# Express, który jest dostępny w sieci Web. Można również skorzystać z książek i zasobów sieci Web o Język U#, aby nauczyć się praktycznych umiejętności programowania.  
  
## <a name="c-language"></a>C# — język

Składnia Języka C# jest bardzo wyrazista, ale jest również prosta i łatwa do nauczenia. Składnia nawiasu klamrowego języka C# będzie natychmiast rozpoznawalna dla każdego, kto zna C, C++ lub Java. Deweloperzy, którzy znają którykolwiek z tych języków są zazwyczaj w stanie rozpocząć pracę wydajnie w języku C# w bardzo krótkim czasie. Składnia języka C# upraszcza wiele złożoności języka C++ i zapewnia zaawansowane funkcje, takie jak typy wartości null, wyliczenia, delegatów, wyrażenia lambda i bezpośredni dostęp do pamięci. C# obsługuje ogólne metody i typy, które zapewniają zwiększone bezpieczeństwo typów i wydajności i iteratory, które umożliwiają realizatorów klas kolekcji do definiowania niestandardowych zachowań iteracji, które są proste w użyciu przez kod klienta. Wyrażenia zapytań zintegrowanych z językiem (LINQ) sprawiają, że silnie typizona kwerenda jest konstrukcją języka pierwszej klasy.  
  
 Jako język obiektowy C# obsługuje pojęcia hermetyzacji, dziedziczenia i polimorfizmu. Wszystkie zmienne i metody, `Main` w tym metoda, punkt wejścia aplikacji, są hermetyzowane w definicjach klas. Klasa może dziedziczyć bezpośrednio z jednej klasy nadrzędnej, ale może zaimplementować dowolną liczbę interfejsów. Metody, które zastępują metody wirtualne `override` w klasie nadrzędnej wymagają słowa kluczowego jako sposób, aby uniknąć przypadkowego ponownego zdefiniowania. W języku C#, struktura jest jak klasa lekka; jest to typ przydzielonego stosu, który może implementować interfejsy, ale nie obsługuje dziedziczenia.  
  
 Oprócz tych podstawowych zasad obiektowych c# ułatwia tworzenie składników oprogramowania za pomocą kilku innowacyjnych konstrukcji językowych, w tym następujących:  
  
- Podpisy metody hermetyzowane nazywane *delegatów*, które umożliwiają powiadomienia o zdarzeniach bezpieczne dla typu.  
  
- Właściwości, które służą jako akcesory dla zmiennych prywatnych elementów członkowskich.  
  
- Atrybuty, które zapewniają deklaratywne metadane dotyczące typów w czasie wykonywania.  
  
- Komentarze do dokumentacji XML.  
  
- Language-Integrated Query (LINQ), który zapewnia wbudowane możliwości zapytania w różnych źródłach danych.  
  
 Jeśli musisz wchodzić w interakcje z innym oprogramowaniem systemu Windows, takim jak obiekty COM lub natywne biblioteki DLL w systemie Win32, możesz to zrobić w języku C# za pomocą procesu o nazwie "Interop". Interop umożliwia programom C# wykonywanie prawie wszystkiego, co może zrobić natywna aplikacja C++. C# obsługuje nawet wskaźniki i pojęcie "niebezpieczne" kod dla tych przypadków, w których bezpośredni dostęp do pamięci ma kluczowe znaczenie.  
  
 Proces kompilacji Języka C# jest prosty w porównaniu do C i C++ i bardziej elastyczny niż w języku Java. Nie ma oddzielnych plików nagłówkowych i nie wymaga, aby metody i typy były deklarowane w określonej kolejności. Plik źródłowy Języka C# może zdefiniować dowolną liczbę klas, struktur, interfejsów i zdarzeń.  
  
 Poniżej przedstawiono dodatkowe zasoby języka C#:  
  
- Aby uzyskać dobre ogólne wprowadzenie do języka, zobacz rozdział 1 [specyfikacji języka Języka C#.](/dotnet/csharp/language-reference/language-specification/introduction)  
  
- Aby uzyskać szczegółowe informacje na temat określonych aspektów języka Języka C#, zobacz [odwołanie c#](../language-reference/index.md).  
  
- Aby uzyskać więcej informacji na temat LINQ, zobacz [LINQ (Language-Integrated Query)](../programming-guide/concepts/linq/index.md).  

## <a name="net-framework-platform-architecture"></a>Architektura platformy .NET Framework

 Programy C# są uruchamiane na platformie .NET Framework, która jest integralnym składnikiem systemu Windows, który zawiera system wykonywania wirtualnego o nazwie środowisko wykonawcze języka wspólnego (CLR) i ujednolicony zestaw bibliotek klas. ŚRODOWISKO CLR jest komercyjną implementacją przez firmę Microsoft wspólnej infrastruktury językowej (CLI), międzynarodowego standardu, który jest podstawą tworzenia środowisk wykonawczych i programistycznych, w których języki i biblioteki współpracują ze sobą bezproblemowo.  
  
 Kod źródłowy napisany w języku C# jest kompilowany do [języka pośredniego (IL),](../../standard/managed-code.md) który jest zgodny ze specyfikacją CLI. Kod IL i zasoby, takie jak mapy bitowe i ciągi, są przechowywane na dysku w pliku wykonywalnym o nazwie zestawu, zazwyczaj z rozszerzeniem .exe lub .dll. Zestaw zawiera manifest, który zawiera informacje o typach zestawu, wersji, kultury i wymagania dotyczące zabezpieczeń.  
  
 Po wykonaniu programu C#, zestaw jest ładowany do clr, które mogą podjąć różne akcje na podstawie informacji w manifeście. Następnie jeśli spełnione są wymagania dotyczące zabezpieczeń, CLR wykonuje just-in-time (JIT) kompilacji do konwersji kodu IL do instrukcji komputera macierzystego. CLR udostępnia również inne usługi związane z automatycznym wyrzucaniem elementów bezużytecznych, obsługą wyjątków i zarządzaniem zasobami. Kod, który jest wykonywany przez CLR jest czasami określane jako "kod zarządzany", w przeciwieństwie do "niezarządzanego kodu", który jest kompilowany do języka komputera macierzystego, który jest przeznaczony dla określonego systemu. Na poniższym diagramie przedstawiono relacje w czasie kompilacji i czasu wykonywania plików kodu źródłowego Języka C#, bibliotek klas .NET Framework, zestawów i biblioteki CLR.  
  
 ![Od kodu źródłowego języka C# do wykonywania maszyny](./media/introduction-to-the-csharp-language-and-the-net-framework/net-architecture-relationships.png)  
  
 Współdziałanie językowe jest kluczową cechą platformy .NET Framework. Ponieważ kod IL opracowany przez kompilator Języka C# jest zgodny ze specyfikacją typowego typu (CTS), kod IL wygenerowany z języka C# może współdziałać z kodem wygenerowanym z wersji .NET języka Visual Basic, Visual C++ lub dowolnego z więcej niż 20 innych języków zgodnych z CTS. Pojedynczy zestaw może zawierać wiele modułów napisanych w różnych językach .NET, a typy mogą odwoływać się do siebie tak, jakby zostały napisane w tym samym języku.  
  
 Oprócz usług czasu wykonywania .NET Framework zawiera również obszerną bibliotekę ponad 4000 klas zorganizowanych w przestrzenie nazw, które zapewniają szeroką gamę przydatnych funkcji dla wszystkiego, od wprowadzania i danych wyjściowych plików po manipulowanie ciągami do xml analizowanie, do formantów formularzy systemu Windows. Typowa aplikacja C# używa biblioteki klas .NET Framework intensywnie do obsługi typowych "hydraulika" obowiązków.  
  
 Aby uzyskać więcej informacji na temat programu .NET Framework, zobacz [Omówienie programu Microsoft .NET Framework](../../framework/get-started/overview.md).  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do programu Visual C #](/visualstudio/ide/quickstart-csharp-console)

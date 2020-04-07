---
title: Wprowadzenie do języka C# i systemu .NET Framework
description: Poznaj podstawy języka C# i .NET. Zapoznaj się z omówieniem języka C# i ekosystemu .NET.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: 9feca97b141b08d418f6833374cbe3c7a0c26d66
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805773"
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>Wprowadzenie do języka C# i programu .NET Framework

C# to elegancki i bezpieczny dla typu język obiektowy, który umożliwia deweloperom tworzenie różnych bezpiecznych i niezawodnych aplikacji, które są uruchamiane w programie .NET Framework. Za pomocą języka C# można tworzyć aplikacje klienckie systemu Windows, usługi sieci Web XML, składniki rozproszone, aplikacje klient-serwer, aplikacje bazy danych i wiele, wiele więcej. Visual C# zapewnia zaawansowany edytor kodu, wygodne projektantów interfejsu użytkownika, zintegrowany debuger i wiele innych narzędzi, aby ułatwić tworzenie aplikacji na podstawie języka C# i .NET Framework.  
  
> [!NOTE]
> Visual C# dokumentacji zakłada, że masz zrozumienie podstawowych pojęć programowania. Jeśli jesteś kompletny początkujący, warto zapoznać się z programem Visual C# Express, który jest dostępny w sieci Web. Można również skorzystać z książek i zasobów sieci Web o języku C#, aby dowiedzieć się umiejętności programowania praktycznego.  
  
## <a name="c-language"></a>C# — język

Składnia C# jest bardzo wyrazisty, ale jest również proste i łatwe do nauczenia. Kręcona składnia języka C# będzie natychmiast rozpoznawalna dla wszystkich osób zaznajomionych z C, C++ lub Java. Deweloperzy, którzy znają którykolwiek z tych języków są zazwyczaj w stanie rozpocząć pracę wydajnie w języku C# w krótkim czasie. Składnia języka C# upraszcza wiele złożoności języka C++ i udostępnia zaawansowane funkcje, takie jak typy nullable, wyliczenia, delegatów, wyrażenia lambda i bezpośredni dostęp do pamięci. C# obsługuje ogólne metody i typy, które zapewniają zwiększone bezpieczeństwo i wydajność typu i iteratory, które umożliwiają realizatorom klas kolekcji definiowanie niestandardowych zachowań iteracji, które są proste w użyciu przez kod klienta. Wyrażenia linq (Language-Integrated Query) sprawiają, że silnie typizowana kwerenda jest konstrukcją języka pierwszej klasy.  
  
 Jako język obiektowy C# obsługuje pojęcia hermetyzacji, dziedziczenia i polimorfizmu. Wszystkie zmienne i metody, w tym `Main` metoda, punkt wejścia aplikacji, są hermetyzowane w definicjach klas. Klasa może dziedziczyć bezpośrednio z jednej klasy nadrzędnej, ale może implementować dowolną liczbę interfejsów. Metody, które zastępują metody wirtualne `override` w klasie nadrzędnej wymagają słowa kluczowego jako sposobu uniknięcia przypadkowego ponownego zdefiniowania. W języku C#, struktura jest jak lekka klasa; jest to typ przydzielony do stosu, który może implementować interfejsy, ale nie obsługuje dziedziczenia.  
  
 Oprócz tych podstawowych zasad zorientowanych obiektowo, C# ułatwia tworzenie składników oprogramowania za pomocą kilku innowacyjnych konstrukcji językowych, w tym:  
  
- Zhermetyzowane podpisy metod o nazwie *delegatów*, które umożliwiają powiadomienia o zdarzeniach bezpiecznych dla typu.  
  
- Właściwości, które służą jako akcesory dla prywatnych zmiennych członkowskich.  
  
- Atrybuty, które zapewniają deklaratywne metadane dotyczące typów w czasie wykonywania.  
  
- Komentarze do dokumentacji XML w ywu.  
  
- Zapytanie zintegrowane z językiem (LINQ), które zapewnia wbudowane możliwości zapytań w różnych źródłach danych.  
  
 Jeśli musisz wchodzić w interakcje z innym oprogramowaniem systemu Windows, takim jak obiekty COM lub natywne biblioteki DLL Win32, możesz to zrobić w języku C# za pośrednictwem procesu o nazwie "Interop". Interop umożliwia programom Języka C# zrobić prawie wszystko, co natywna aplikacja C++może zrobić. C# obsługuje nawet wskaźniki i pojęcie "niebezpieczny" kod dla tych przypadków, w których bezpośredni dostęp do pamięci jest krytyczny.  
  
 Proces kompilacji języka C# jest prosty w porównaniu do języka C i C++ i bardziej elastyczny niż w języku Java. Nie ma żadnych oddzielnych plików nagłówkowych i nie wymaga, aby metody i typy były deklarowane w określonej kolejności. Plik źródłowy języka C# może zdefiniować dowolną liczbę klas, struktur, interfejsów i zdarzeń.  
  
 Poniżej znajdują się dodatkowe zasoby języka C#:  
  
- Aby uzyskać dobre ogólne wprowadzenie do języka, zobacz rozdział 1 [specyfikacji języka C#.](/dotnet/csharp/language-reference/language-specification/introduction)  
  
- Aby uzyskać szczegółowe informacje na temat określonych aspektów języka C#, zobacz [odwołanie c#](../language-reference/index.md).  
  
- Aby uzyskać więcej informacji na temat LINQ, zobacz [LINQ (Zapytanie zintegrowane z językiem).](../programming-guide/concepts/linq/index.md)  

## <a name="net-framework-platform-architecture"></a>Architektura platformy .NET Framework

 Programy języka C# są uruchamiane w programie .NET Framework, integralnym składniku systemu Windows, który zawiera system wykonywania wirtualnego o nazwie środowisko uruchomieniowe języka wspólnego (CLR) i ujednolicony zestaw bibliotek klas. CLR jest komercyjną implementacją przez firmę Microsoft wspólnej infrastruktury językowej (CLI), międzynarodowego standardu, który jest podstawą do tworzenia środowisk wykonawczych i programistycznych, w których języki i biblioteki współpracują ze sobą bezproblemowo.  
  
 Kod źródłowy napisany w języku C# jest kompilowany do [języka pośredniego (IL),](../../standard/managed-code.md) który jest zgodny ze specyfikacją interfejsu wiersza polecenia. Kod IL i zasoby, takie jak mapy bitowe i ciągi, są przechowywane na dysku w pliku wykonywalnym o nazwie zestaw, zazwyczaj z rozszerzeniem .exe lub .dll. Zestaw zawiera manifest, który zawiera informacje o typach zestawu, wersji, kultury i wymagania dotyczące zabezpieczeń.  
  
 Po wykonaniu programu C# zestaw jest ładowany do clr, który może podjąć różne akcje na podstawie informacji w manifeście. Następnie, jeśli wymagania dotyczące zabezpieczeń są spełnione, CLR wykonuje kompilacji Just-In-Time (JIT) do konwersji kodu IL do natywnych instrukcji maszyny. Clr zapewnia również inne usługi związane z automatycznego wyrzucania elementów bezużytecznych, obsługi wyjątków i zarządzania zasobami. Kod, który jest wykonywany przez CLR jest czasami określane jako "kod zarządzany", w przeciwieństwie do "kodu niezarządzanego", który jest kompilowany do języka macierzystego maszyny, który jest przeznaczony dla określonego systemu. Na poniższym diagramie przedstawiono relacje w czasie kompilacji i wykonywania plików kodu źródłowego języka C#, bibliotek klas .NET Framework, zestawów i clr.  
  
 ![Od kodu źródłowego języka C# do wykonania komputera](./media/introduction-to-the-csharp-language-and-the-net-framework/net-architecture-relationships.png)  
  
 Współdziałanie języka jest kluczową cechą programu .NET Framework. Ponieważ kod IL wyprodukowany przez kompilator języka C# jest zgodny ze specyfikacją wspólnego typu (CTS), kod IL wygenerowany z języka C# może wchodzić w interakcje z kodem wygenerowanym z wersji .NET języka Visual Basic, Visual C++ lub dowolnego z więcej niż 20 innych języków zgodnych z cts. Pojedynczy zestaw może zawierać wiele modułów napisanych w różnych językach .NET, a typy mogą odwoływać się do siebie tak, jakby zostały napisane w tym samym języku.  
  
 Oprócz usług czasu wykonywania .NET Framework zawiera również obszerną bibliotekę ponad 4000 klas zorganizowanych w przestrzenie nazw, które zapewniają szeroką gamę przydatnych funkcji dla wszystkich, od wprowadzania i danych wyjściowych plików do manipulowania ciągami do analizowania XML, do formantów Windows Forms. Typowa aplikacja języka C# używa biblioteki klas .NET Framework intensywnie do obsługi typowych zadań "instalacyjnych".  
  
 Aby uzyskać więcej informacji na temat programu .NET Framework, zobacz [Omówienie programu Microsoft .NET Framework](../../framework/get-started/overview.md).  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do programu Visual C #](/visualstudio/ide/quickstart-csharp-console)

---
title: Wprowadzenie do języka C# i systemu .NET Framework
description: Poznaj podstawy języka C# i .NET. Zapoznaj się z omówieniem języka C# i ekosystemu .NET.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: 28fde47721e6354612ffec557da25c6d3bb775e4
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409227"
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>Wprowadzenie do języka C# i systemu .NET Framework

C# to elegancki i bezpieczny typowo język obiektowy, który umożliwia deweloperom tworzenie różnych bezpiecznych i niezawodnych aplikacji korzystających z [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Służy C# do utworzenia klienta Windows aplikacji, usług sieci Web XML, rozpowszechnianych komponentów, aplikacji typu klient serwer, aplikacji baz danych i wielu, m.in. Visual C# zapewnia zaawansowany edytor kodu, dogodne Projektowanie interfejsu użytkownika, zintegrowany debugger i wiele innych narzędzi, aby ułatwić opracowywanie aplikacji opartych na języku C# i [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
> [!NOTE]
> Dokumentacja języka Visual C# przyjęto założenie, iż zrozumienie podstawowych pojęć programowania. Jeśli jesteś kompletnym nowicjuszem, możesz chcieć zapoznaj się z Visual C# Express, który jest dostępny w sieci Web. Można również korzystać z książek i zasobów sieci Web o C#, aby uzyskać praktyczne umiejętności programowania.  
  
## <a name="c-language"></a>Język C#

 Składnia języka C# jest bardzo ekspresyjna, ale również jest proste i łatwe do opanowania. Nawias klamrowy składni języka C# będzie rozpoznawalny dla każdego, kto zna C, C++ lub Java. Deweloperzy, którzy nie znają żadnego z tych języków są zazwyczaj mogą rozpocząć produktywną pracę w języku C# w bardzo krótkim czasie. Składnia języka C# upraszcza wiele złożoności C++ i udostępnia zaawansowane funkcje, takie jak typy o wartości zerowalnej, wyliczeń, delegatów, wyrażeń lambda i bezpośredni dostęp do pamięci, które nie znajdują się w języku Java. C# obsługuje metody rodzajowe i typy, które zapewniają zwiększone bezpieczeństwo typu i wydajność oraz Iteratory, które umożliwiają implementacje klasy kolekcji do zdefiniowania iteracji niestandardowych zachowań, które są proste w użyciu przez kod klienta. [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] wyrażenia upewnij się, że wpisane pogrubieniem zapytanie staje się konstrukcją języka.  
  
 Jako język zorientowany na obiekt C# obsługuje pojęcia hermetyzacji, dziedziczenia i polimorfizmu. Wszystkie zmienne i metod, takich jak `Main` metody punktu wejścia aplikacji, są hermetyzowane w ramach definicji klasy. Klasy mogą dziedziczyć bezpośrednio z poziomu jednej klasy nadrzędnej, ale to może wprowadzić dowolną liczbę interfejsów. Metody, które zastępują metody wirtualne klasy nadrzędnej wymagają `override` słowa kluczowego jako sposobu uniknięcia przypadkowego przedefiniowania. W języku C# struktura przypomina klasy lightweight; jest typ przydzielanych ze stosów, które można implementować interfejsy, ale nie obsługuje dziedziczenia.  
  
 Oprócz tych podstawowych zasad zorientowane obiektowo C# ułatwia opracowanie składników oprogramowania za pośrednictwem kilku innowacyjnych konstrukcji językowych, takie jak następujące:  
  
- Hermetyzowane podpisów metody wywołanych *delegatów*, która umożliwia powiadomienia o zdarzeniach bezpiecznegop typu.  
  
- Właściwości, które służą jako Akcesoria dla zmiennych prywatnego elementu członkowskiego.  
  
- Atrybuty, które zapewniają deklaracyjne metadane dotyczące typów w czasie wykonywania.  
  
- Komentarze wbudowanej dokumentacji XML.  
  
- [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] między różnymi źródłami danych, która zapewnia wbudowane możliwości zapytania.  
  
 Jeśli masz oddziałują na inne oprogramowanie Windows, takich jak obiekty COM lub natywnych bibliotek Win32 dll, można to zrobić w C# dzięki procesowi zwanemu "Interop". Usługa międzyoperacyjna umożliwia programom C# niemal wszystko, co można wykonać macierzysta aplikacja C++. C# obsługuje nawet wskazówki i pojęcie "niebezpieczny" kod dla tych przypadków, w których bezpośredni dostęp do pamięci jest absolutnie kluczowego znaczenia.  
  
 Proces kompilacji C# jest prosty w porównaniu do C i C++ i bardziej elastyczny niż w języku Java. Brak ma osobnych plików nagłówka oraz wymagania można zadeklarować metody i typy w określonej kolejności. Plik źródłowy C# może zdefiniować dowolną liczbę klas, struktur, interfejsów i wydarzeń.  
  
 Poniżej przedstawiono dodatkowe zasoby C#:  
  
- Aby uzyskać obszerne ogólne wprowadzenie do języka, zobacz rozdział 1 [specyfikacji języka C#](../../csharp/language-reference/language-specification/index.md).  
  
- Aby uzyskać szczegółowe informacje dotyczące konkretnych aspektów języka C#, zobacz [odwołanie w C#](../../csharp/language-reference/index.md).  
  
- Aby uzyskać więcej informacji na temat [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], zobacz [LINQ (Language-Integrated Query)](../programming-guide/concepts/linq/index.md).  

## <a name="net-framework-platform-architecture"></a>Architektura platformy .NET Framework

 C# programy uruchamiane [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], integralny składnik systemu Windows, która zawiera wirtualne wykonanie systemu o nazwie środowisko uruchomieniowe języka wspólnego (CLR) i jednolity zbiór bibliotek klas. Środowisko CLR jest komercyjną implementacją przez firmę Microsoft common language infrastructure (CLI), międzynarodowego standardu, który jest podstawą tworzenia środowisk wykonywania i programistycznych w których języki i biblioteki współpracują ze sobą.  
  
 Kodu źródłowego napisanego w języku C# jest skompilowany w języku pośrednim (IL), który jest zgodny ze specyfikacją interfejsu wiersza polecenia. Kod IL i zasoby, takie jak mapy bitowe i ciągi znaków, są przechowywane na dysku w pliku wykonywalnym zwanym zestawem, zwykle z rozszerzeniem .exe lub .dll. Zestaw zawiera manifest, który zawiera informacje dotyczące typów, wersji, kultury i wymagania dotyczące zabezpieczeń zestawu.  
  
 Gdy wykonany zostaje program C#, zestaw jest ładowany do CLR, który może wykonać różne akcje w oparciu o informacje zawarte w manifeście. Następnie jeśli spełnione są wymagania bezpieczeństwa, CLR wykonuje dokładnie na czas (JIT) kompilacja, aby skonwertować kod IL do instrukcji maszyny macierzystej. Środowisko CLR oferuje również inne usługi związane z automatycznym wyrzucania elementów bezużytecznych, obsługa wyjątków i zarządzanie zasobami. Kod, który jest wykonywany przez środowisko CLR jest czasami określane jako "kod zarządzany" w przeciwieństwie do "Kod niezarządzanego" który jest skompilowany w macierzystym języku maszynowym, który jest przeznaczony dla określonego systemu. Poniższy diagram ilustruje relacje kompilacji i środowiska wykonawczego języka C# plików kodu źródłowego, biblioteki klas .NET Framework, zespołów i środowiska CLR.  
  
 ![Od C&#35; źródła kodu w celu wykonania maszyny](./media/introduction-to-the-csharp-language-and-the-net-framework/net-architecture-relationships.png)  
  
 Współdziałanie języków jest kluczowym elementem [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Ponieważ kod IL produkowany przez kompilator języka C# jest zgodny do wspólnych specyfikacji typu (CTS), kod IL generowany z C# mogą współdziałać z kodem, który został wygenerowany z wersji .NET, Visual Basic, Visual C++ lub ponad 20 innymi językami zgodnymi z CTS. Pojedynczy zestaw może zawierać wiele modułów napisanych w różnych językach .NET i typy mogą odwoływać się wzajemnie tak, jakby były one napisane w języku.  
  
 Oprócz wykonywania usług [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] obejmuje również rozbudowaną bibliotekę ponad 4000 klas zorganizowanych w przestrzenie nazw, które zapewniają szeroką gamę przydatnych funkcji wszystko od plików wejściowych i wyjściowych do manipulowania ciągami XML analizowanie kontrolek formularzy Windows Forms. Typowa aplikacja C# używa [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteki klas w szerokim zakresie, aby obsłużyć typowe obowiązku "hydrauliczne".  
  
 Aby uzyskać więcej informacji na temat programu .NET Framework, zobacz [Omówienie programu Microsoft .NET Framework](../../framework/get-started/overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [C#](../../csharp/index.md)
- [Wprowadzenie do języków Visual C# i Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)

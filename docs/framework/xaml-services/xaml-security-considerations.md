---
title: Zagadnienia dotyczące zabezpieczeń XAML
ms.date: 03/30/2017
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
ms.openlocfilehash: 76dce711e46d267c85b0fc9426be452d90b4d07c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622834"
---
# <a name="xaml-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń XAML
W tym temacie opisano najlepsze rozwiązania dotyczące zabezpieczeń w aplikacji, korzystając z XAML i interfejsu API programu .NET Framework XAML Services.  
  
## <a name="untrusted-xaml-in-applications"></a>Niezaufane XAML w aplikacjach  
 W najbardziej ogólnym sensie niezaufanej XAML jest dowolnego źródła XAML, które nie obejmują lub emitować aplikacji.  
  
 XAML, który jest skompilowany w lub przechowywane jako `resx`— nie jest natury niezaufanych typu zasobu w zestawie podpisany i zaufanych. XAML mogą ufać, jak zaufanie zespołu jako całości. W większości przypadków dotyczy tylko relacji zaufania aspektów luźne XAML, który jest źródłem XAML, które ładujesz ze strumienia lub innych operacji We/Wy. Luźne XAML nie jest określony składnik lub funkcję za pomocą infrastruktury pakowania i wdrażania modelu aplikacji. Jednak zestaw może zaimplementować zachowania, które obejmuje ładowanie luźne XAML.  
  
 Dla niezaufanych XAML należy traktować go ogólnie takie same tak, jakby była niezaufanego kodu. Użyj piaskownicy lub innych metafory, aby uniemożliwić dostęp do zaufanych kodu przez prawdopodobnie niezaufanych XAML.  
  
 Rodzaj możliwości w XAML zapewnia XAML prawo do konstruowania obiektów i ustawiać ich właściwości. Te funkcje obejmują, uzyskiwanie dostępu do konwerterów typów, mapowanie i uzyskiwania dostępu do zestawów w domenie aplikacji przy użyciu rozszerzenia znaczników `x:Code` bloków i tak dalej.  
  
 Oprócz możliwości poziomu języka XAML jest używana do definicji interfejsu użytkownika w wiele technologii. Ładowanie XAML niezaufanych może oznaczać ładowania złośliwego fałszowaniem interfejsu użytkownika.  
  
## <a name="sharing-context-between-readers-and-writers"></a>Udostępnianie kontekstu między czytników i składników zapisywania  
 Architektura usług programu .NET Framework XAML dla XAML czytników i składników zapisywania XAML wymaga często udostępnianie czytnik XAML Edytor XAML lub wspólny kontekst schematu XAML. Udostępnianie obiektów lub kontekstów może być wymagane, jeśli piszesz logikę pętli węzłów XAML lub zapewnianie niestandardowego Zapisz ścieżkę. Nie powinna współużytkować XAML czytnika wystąpień, kontekst schematu XAML niestandardowe lub ustawienia dla klasy czytnika/zapis XAML między kodem zaufanych i niezaufanych.  
  
 Większość scenariuszy i operacje dotyczące obiektu XAML zapisywania dla typu CLR na podstawie kopii po prostu użyć domyślny kontekst schematu XAML. Domyślny kontekst schematu XAML nie ma jawnie ustawień, które mogą negatywnie wpłynąć na pełne zaufanie. Ten sposób jest bezpiecznie udostępniać kontekstu między zaufanych i niezaufanych XAML czytnika/składniki modułów zapisujących. Jednakże, jeśli to zrobisz, nadal jest najlepszym rozwiązaniem jest zapewnienie takie czytniki i moduły zapisujące w oddzielnych <xref:System.AppDomain> zakresów z jednego z nich, które są specjalnie przeznaczone/piaskownicy częściowego zaufania.  
  
## <a name="xaml-namespaces-and-assembly-trust"></a>Przestrzenie nazw XAML i zaufania zestawu  
 Podstawowa składnia niekwalifikowaną i definicję dla interpretowanie niestandardowe mapowanie przestrzeni nazw XAML do zestawu XAML nie rozróżnia zaufanych i niezaufanych zestawu jako ładowany do domeny aplikacji. W efekcie jest technicznie możliwe dla niezaufanego zestawu, aby podszywały się pod zaufanym zestawie zamierzony mapowanie przestrzeni nazw XAML i przechwytywać deklarowanego obiektu źródło XAML i informacje o właściwościach. Jeśli masz wymagania dotyczące zabezpieczeń, aby uniknąć tej sytuacji, należy wprowadzać zamierzony mapowanie przestrzeni nazw XAML przy użyciu jednej z następujących technik:  
  
- Użyj w pełni kwalifikowanej nazwy zestawu z silną nazwę mapowania przestrzeni nazw XAML, wszystkie wprowadzone przez użytkownika aplikacji XAML.  
  
- Ogranicz mapowania ustalony zestaw elementów zestawy odwołań, tworząc określonego zestawu <xref:System.Xaml.XamlSchemaContext> dla Twojego XAML czytników i XAML obiektu modułów zapisujących. Zobacz <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>.  
  
## <a name="xaml-type-mapping-and-type-system-access"></a>Mapowanie typu XAML i dostęp do systemu typów  
 XAML obsługuje własny typ w systemie na wiele sposobów elementu równorzędnego do Implementowanie CLR na podstawowy system typu CLR. Dla niektórych aspektów rozpoznawania typu, gdy wykonujesz decyzji dotyczących zaufania o typie, w oparciu o informacje o typie należy Odrocz do informacji o typie w środowisku CLR, typy kopii. Jest tak, ponieważ niektóre z określonych funkcji raportowania w systemie typu XAML są pozostawione otwarte jako metod wirtualnych, a w związku z tym, nie są w pełni pod kontrolą oryginalnej implementacji usług programu .NET Framework XAML. Te punkty rozszerzeń istnieje, ponieważ w systemie typu XAML jest rozszerzalny, aby dopasować rozszerzalności XAML, sama i jego możliwe alternatywnych strategii mapowania typów w porównaniu z domyślną implementację kopii środowiska CLR i domyślny kontekst schematu XAML. Aby uzyskać więcej informacji, zobacz Uwagi dotyczące określonych na kilku właściwości <xref:System.Xaml.XamlType> i <xref:System.Xaml.XamlMember>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xaml.Permissions.XamlAccessLevel>

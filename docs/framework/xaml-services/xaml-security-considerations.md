---
title: "Zagadnienia dotyczące zabezpieczeń XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
caps.latest.revision: "7"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 59d0b835a0de3e84e2cb6e77ed368511bfe21b19
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="xaml-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń XAML
W tym temacie opisano najlepsze rozwiązania dotyczące zabezpieczeń w aplikacji, korzystając z języka XAML i .NET Framework XAML Services API.  
  
## <a name="untrusted-xaml-in-applications"></a>Niezaufane XAML w aplikacjach  
 W tym sensie, najbardziej ogólnym niezaufanej XAML jest dowolnego źródła XAML, które aplikacji nie zostały nie obejmują lub emisji.  
  
 XAML skompilowany w lub przechowywane jako `resx`— typ zasobu w zestawie zaufanych i podpisem nie jest z założenia niezaufanych. Można ufać XAML, jak zaufania zestawu jako całość. W większości przypadków dotyczy tylko aspekty zaufania utracić XAML, która jest źródłem XAML, że zostały załadowane z strumienia lub inne we/wy. Utracić XAML nie jest określony składnik lub funkcji z wdrażanie i opakowanie infrastruktury modelu aplikacji. Jednak zestaw może zastosować zachowania, które obejmuje ładowanie utracić XAML.  
  
 Dla XAML niezaufanych należy traktować go ogólnie takie same tak, jakby była kodzie niezaufanym. Aby uniemożliwić dostęp do zaufanego kodu XAML prawdopodobnie niezaufanych, należy użyć sandboxing lub innych metafory.  
  
 Rodzaj XAML możliwości daje XAML prawo do tworzenia obiektów i ustawiania ich właściwości. Te możliwości również obejmować dostęp do typy konwerterów mapowania i uzyskiwania dostępu do zestawów w domenie aplikacji przy użyciu rozszerzenia znaczników `x:Code` bloków i tak dalej.  
  
 Oprócz możliwości poziom języka XAML jest używany do definicji interfejsu użytkownika w wielu technologii. Ładowanie niezaufanych XAML może to oznaczać ładowania złośliwego fałszowaniem interfejsu użytkownika.  
  
## <a name="sharing-context-between-readers-and-writers"></a>Udostępnianie kontekstu między czytelników i zapisywania  
 Architektura usług .NET Framework XAML dla czytników XAML i autorzy XAML wymaga często udostępnianie czytnik XAML do zapisywania XAML lub udostępnionego kontekst schematu XAML. Udostępnianie obiektów lub kontekstów może być wymagane, jeśli pisania logiki pętli węzła XAML, lub zapewniając niestandardowego Zapisz ścieżkę. Nie powinna współużytkować wystąpień czytnika XAML, kontekst schematu XAML niestandardowe lub ustawienia dla klas odczytywania/zapisywania XAML między kodem zaufanych i niezaufanych.  
  
 Większość scenariuszy i operacji dotyczących obiektu XAML zapisywania dla typu CLR na podstawie kopii służy tylko domyślny kontekst schematu XAML. Domyślny kontekst schematu XAML nie ma jawnie ustawień, które mogą negatywnie wpłynąć na pełne zaufanie. W związku z tym jest bezpieczne udostępnianie kontekstu między składnikami odczytywania/zapisywania XAML zaufanych i niezaufanych. Jednak jeśli to zrobisz, nadal jest najlepszym rozwiązaniem, aby zachować takie czytniki i zapisywania w oddzielnym <xref:System.AppDomain> zakresów z jednego z nich w szczególności zamierzony/piaskownicy dla częściowej relacji zaufania.  
  
## <a name="xaml-namespaces-and-assembly-trust"></a>Przestrzeń nazw XAML i zaufanych zestawów  
 Podstawowa składnia niekwalifikowanych i definicję dla interpretowanie niestandardowe mapowania przestrzeni nazw XAML do zestawu XAML nie rozróżnia zaufanych i niezaufanych zestawu jako załadowane do tej domeny aplikacji. W związku z tym jest technicznie możliwe niezaufanego zestawu sfałszować zaufanym zestawem zamierzone mapowania przestrzeni nazw XAML i przechwytywania obiekt zadeklarowane źródłem XAML i informacje dotyczące właściwości. Jeśli wymagania dotyczące zabezpieczeń, aby uniknąć tej sytuacji, należy wprowadzać zamierzone mapowanie przestrzeni nazw XAML przy użyciu jednej z następujących metod:  
  
-   Użyj pełni kwalifikowanej nazwy zestawu z mocną nazwą w mapowania przestrzeni nazw XAML, wszelkie wprowadzone przez użytkownika aplikacji XAML.  
  
-   Ograniczanie mapowania ustalony zbiór zestawów odwołań, tworząc określonego zestawu <xref:System.Xaml.XamlSchemaContext> dla Twojego XAML czytników oraz XAML obiekt modułów zapisujących. Zobacz <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>.  
  
## <a name="xaml-type-mapping-and-type-system-access"></a>Mapowanie typu XAML i typ dostępu do systemu  
 XAML obsługuje własny typ system, czyli na wiele sposobów elementu równorzędnego do jak CLR implementuje podstawowe system typów CLR. Niektórych aspektów świadomości typu, gdzie są podejmowanie decyzji dotyczących typu, na podstawie informacji o jego typu zaufania należy odroczyć do informacji o typie CLR kopii typów. Jest tak, ponieważ niektóre z określonych funkcji raportowania system typów języka XAML pozostają otwarte, jako metody wirtualne i w związku z tym nie są całkowicie pod kontrolą oryginalnej implementacji usług .NET Framework XAML. Te punkty rozszerzeń istnieje, ponieważ system typu XAML nie jest otwarty, aby dopasować rozszerzalności języka XAML, sama i jego możliwych alternatywnych strategii mapowanie typu lub domyślna implementacja kopii CLR i domyślny kontekst schematu XAML. Aby uzyskać więcej informacji, zobacz uwagi określonych w przypadku kilku właściwości <xref:System.Xaml.XamlType> i <xref:System.Xaml.XamlMember>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xaml.Permissions.XamlAccessLevel>

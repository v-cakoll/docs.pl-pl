---
title: Emitowanie dynamicznych metod i zestawów
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 527da43807a0dbba8f5365c92f566053f10d49f5
ms.sourcegitcommit: c03eef711abe961a85db2b4d0715257d1524aef6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33848300"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Emitowanie dynamicznych metod i zestawów
W tej sekcji opisano zestaw typy zarządzane w <xref:System.Reflection.Emit> przestrzeni nazw, która umożliwia kompilatora lub narzędziu emitowanie metadanych i Microsoft języku pośrednim (MSIL) w czasie wykonywania i opcjonalnie Generowanie pliku przenośny plik wykonywalny (PE) na dysku. Liczba aparatów skryptów i kompilatory są użytkowników podstawowych tego obszaru nazw. W tej sekcji funkcje udostępniane przez <xref:System.Reflection.Emit> przestrzeni nazw jest określana jako odbicia emisji.  
  
 Emisja odbicia oferuje następujące możliwości:  
  
-   Zdefiniuj lekkie metody globalne wykonywania czasu, przy użyciu <xref:System.Reflection.Emit.DynamicMethod> klasy, a następnie wykonać ich używanie delegatów.  
  
-   Zdefiniuj zestawów w czasie wykonywania i uruchamiać je lub Zapisz je na dysku.  
  
-   Zdefiniuj zestawów w czasie wykonywania, uruchom, a następnie zwolnij je i Zezwalaj na wyrzucanie elementów bezużytecznych odzyskać ich zasobów.  
  
-   Zdefiniuj modułów w nowych zestawach w czasie wykonywania i uruchom lub zapisać je na dysku.  
  
-   Definiowanie typów modułów w czasie wykonywania, tworzenie wystąpień typów i wywołania metod.  
  
-   Zdefiniuj informacje symboliczne dla określonych modułów, które mogą być używane przez narzędzia, takie jak debugery i profilery kodu.  
  
 Oprócz typy zarządzane w <xref:System.Reflection.Emit> przestrzeni nazw, istnieją interfejsy niezarządzane metadanych, które zostały opisane w [interfejsy metadanych](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) odwołania dokumentacji. Emisja odbicia zarządzanych zapewnia silniejsze sprawdzanie błędów semantycznych i wyższym poziomie abstrakcji metadanych niż interfejsy niezarządzane metadanych.  
  
 Inne przydatne zasoby do pracy z metadanych i MSIL jest dokumentacji infrastruktury języka wspólnego (CLI), szczególnie "Partycji II: metadane definicji i semantyki" i "Partycji III: CIL instrukcji Set". Dokumentacja jest dostępna online na [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) i [witryny sieci Ecma Web](http://go.microsoft.com/fwlink/?LinkId=116487).  
  
## <a name="in-this-section"></a>W tej sekcji
  
[Emituj problemy z zabezpieczeniami w odbicia](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
W tym artykule opisano zabezpieczeń, które Emituj problemów dotyczących tworzenia dynamicznych zestawach za pomocą odbicia.  

[Porady: definiowanie i wykonywanie metod dynamicznych](how-to-define-and-execute-dynamic-methods.md)   
Pokazuje, jak wykonać prostą metodę dynamicznego i dynamiczna metoda powiązany z wystąpieniem klasy.

[Porady: Definiowanie typu ogólnego z odbiciem emisji](how-to-define-a-generic-type-with-reflection-emit.md)   
Przedstawia sposób tworzenia prostego typu ogólnego z dwoma parametrami typu, jak dotyczą parametrów typu klasy interfejsu i ograniczeń specjalnych oraz sposobu tworzenia elementów członkowskich, które używają parametrów typu klasy jako typy parametrów i zwracanych typów.

[Porady: definiowanie metody ogólnej za pomocą odbicia emisji](how-to-define-a-generic-method-with-reflection-emit.md)   
Przedstawia sposób tworzenia, emisji, a następnie wywołaj proste metody rodzajowej.

[Zestawów kolekcjonowanych generacji typu dynamicznego](collectible-assemblies.md)   
Wprowadza zestawów kolekcjonowanych, które są dynamiczne zestawy, które może być zwolniony bez zwalniania domeny aplikacji, w którym zostały utworzone.
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Reflection.Emit.OpCodes>  
 Tworzy wykaz kodów instrukcja MSIL, używanej do tworzenia treści metody.  
  
 <xref:System.Reflection.Emit>  
 Zawiera klasy zarządzane używane na emitowanie metod dynamicznych, zestawy i typów.  
  
 <xref:System.Type>  
 W tym artykule opisano <xref:System.Type> klasy, która reprezentuje typów w zarządzanych odbicia emisja odbicia i która jest kluczem do używania tych technologii.  
  
 <xref:System.Reflection>  
 Zawiera klasy zarządzane używane do eksplorowania metadanych i kod zarządzany.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Odbicie](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Wyjaśniono, jak metadanych i kod zarządzany.  
  
 [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Zawiera omówienie zestawów w implementacjach .NET.

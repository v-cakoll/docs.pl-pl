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
ms.openlocfilehash: 1a0ed1d02fd40a94d4ae63deea3c09b04bfc9bd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793318"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Emitowanie dynamicznych metod i zestawów
W tej sekcji opisano zestaw typów zarządzanych w <xref:System.Reflection.Emit> przestrzeni nazw, dzięki czemu kompilator lub narzędziu emitowanie metadanych oraz języka Microsoft intermediate language (MSIL) w czasie wykonywania i opcjonalnie generowania przenośnych plików wykonywalnych (PE) pliku na dysku. Kompilatory i aparatów skryptów są użytkownicy podstawowi tej przestrzeni nazw. W tej sekcji funkcje udostępniane przez <xref:System.Reflection.Emit> przestrzeni nazw jest określany jako odbicia emisji.  
  
 Emisji odbicia zapewnia następujące możliwości:  
  
- Zdefiniuj uproszczone globalnych metod wykonywania użycie <xref:System.Reflection.Emit.DynamicMethod> klasy i wykonać je przy użyciu delegatów.  
  
- Definiowanie zestawów w czasie wykonywania i uruchamiać je lub zapisać je na dysku.  
  
- Definiowanie zestawów w czasie wykonywania, uruchamiaj je, a następnie zwolnij je i Zezwalaj na wyrzucanie elementów bezużytecznych odzyskać ich zasobów.  
  
- Zdefiniuj modułów w nowych zestawów w czasie wykonywania i uruchomić lub zapisać je na dysku.  
  
- Definiowanie typów modułów w czasie wykonywania, tworzenie wystąpień typów i wywołania ich metod.  
  
- Zdefiniuj informacje o symbolach dla określonych modułów, które mogą być używane przez narzędzi, takich jak debugery i profilery kodu.  
  
 Oprócz typów zarządzanych w <xref:System.Reflection.Emit> przestrzeni nazw, istnieją interfejsy niezarządzane metadanych, które są opisane w [interfejsy metadanych](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) dokumentację referencyjną. Emisji odbicia zarządzanych zapewnia lepsze sprawdzanie błędów semantycznego i wyższym poziomie abstrakcji metadanych niż interfejsy niezarządzane metadanych.  
  
 Innym zasobem przydatne do pracy z MSIL i metadanych znajduje się dokumentacja Common Language Infrastructure (CLI), szczególnie "partycja II: Definicja metadanych i semantyka"oraz" Partition III: Zestaw instrukcji CIL". Dokumentacja jest dostępna online na [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) i [witryny sieci Ecma Web](https://go.microsoft.com/fwlink/?LinkId=116487).  
  
## <a name="in-this-section"></a>W tej sekcji
  
[Problemy związane z zabezpieczeniami, w odbiciu emisji](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
W tym artykule opisano zabezpieczeń, które emitują problemy związane z tworzenie dynamicznych zestawów przy użyciu odbicia.  

[Instrukcje: Definiowanie i wykonywanie metod dynamicznych](how-to-define-and-execute-dynamic-methods.md)   
Pokazuje, jak wykonać prostą metodę dynamiczną i metodę dynamiczną, która jest powiązana z wystąpienia klasy.

[Instrukcje: Definiowanie typu ogólnego przy użyciu odbicia emisji](how-to-define-a-generic-type-with-reflection-emit.md)   
Pokazuje, jak utworzyć prosty typ ogólny z dwoma parametrami typu, instrukcje dotyczą parametrów typu klasy, interfejsu i ograniczeń specjalnych i tworzenie elementów członkowskich, które używać parametrów typu klasy jako typy parametrów i zwracanych typów.

[Instrukcje: Definiowanie metody ogólnej przy użyciu odbicia emisji](how-to-define-a-generic-method-with-reflection-emit.md)   
Pokazuje, jak utworzyć, emisji i wywołania proste metody rodzajowej.

[Zestawy kolekcjonowane dla dynamicznego generowania typów](collectible-assemblies.md)   
Wprowadza kolekcjonowane zestawów, które są dynamicznych zestawów, które może być rozładowany bez rozładowywania domeny aplikacji, w którym zostały utworzone.
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Reflection.Emit.OpCodes>  
 Skatalogowano kody instrukcji MSIL, służących do tworzenia treści metod.  
  
 <xref:System.Reflection.Emit>  
 Zawiera klasy zarządzanej, używany do emitowania metody dynamicznej, zespoły i typów.  
  
 <xref:System.Type>  
 W tym artykule opisano <xref:System.Type> klasy, która reprezentuje typy w zarządzanych odbicia emisji odbicia i który ma kluczowe znaczenie dla korzystania z tych technologii.  
  
 <xref:System.Reflection>  
 Zawiera klasy zarządzane używane do eksplorowania metadanych i kod zarządzany.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Odbicie](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Wyjaśnia, jak eksplorować metadanych i kod zarządzany.  
  
 [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Omówienie zestawów w implementacji platformy .NET.

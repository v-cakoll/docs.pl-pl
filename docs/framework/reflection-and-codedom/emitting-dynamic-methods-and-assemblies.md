---
title: Emitowanie dynamicznych metod i zestawów
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: fda5a20eb7798086ec10415889454b4a8beba5f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180525"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Emitowanie dynamicznych metod i zestawów

W tej sekcji opisano zestaw <xref:System.Reflection.Emit> typów zarządzanych w obszarze nazw, które umożliwiają kompilatorowi lub narzędziu emitowanie metadanych i języka pośredniego firmy Microsoft (MSIL) w czasie wykonywania i opcjonalnie generowanie przenośnego pliku wykonywalnego (PE) na dysku. Aparaty skryptów i kompilatory są podstawowymi użytkownikami tej przestrzeni nazw. W tej sekcji funkcje udostępniane <xref:System.Reflection.Emit> przez obszar nazw jest określany jako emitować odbicia.  
  
Emitowanie odbicia zapewnia następujące możliwości:  
  
- Zdefiniuj lekkie metody <xref:System.Reflection.Emit.DynamicMethod> globalne w czasie wykonywania, przy użyciu klasy i wykonaj je przy użyciu pełnomocników.  
  
- Zdefiniuj zestawy w czasie wykonywania, a następnie uruchom je i/lub zapisz na dysku.  
  
- Zdefiniuj zestawy w czasie wykonywania, uruchom je, a następnie zwolnij je i pozwól wyrzucaniu elementów bezużytecznych odzyskać swoje zasoby.  
  
- Zdefiniuj moduły w nowych złożeniach w czasie wykonywania, a następnie uruchom i/lub zapisz je na dysku.  
  
- Zdefiniuj typy w modułach w czasie wykonywania, utwórz wystąpienia tych typów i wywołaj ich metody.  
  
- Zdefiniuj informacje symboliczne dla zdefiniowanych modułów, które mogą być używane przez narzędzia, takie jak debugery i profileery kodu.  
  
Oprócz typów zarządzanych w <xref:System.Reflection.Emit> obszarze nazw istnieją niezarządzane interfejsy metadanych, które są opisane w dokumentacji odwołania [do interfejsów metadanych.](../unmanaged-api/metadata/metadata-interfaces.md) Emitowane odbicie zarządzane zapewnia silniejsze sprawdzanie błędów semantycznych i wyższy poziom abstrakcji metadanych niż interfejsy metadanych niezarządzane.  
  
Innym użytecznym zasobem do pracy z metadanymi i MSIL jest dokumentacja wspólnej infrastruktury języka (CLI), w szczególności "Partition II: Definicja metadanych i semantyka" i "Partycja III: Zestaw instrukcji CIL". Dokumentacja jest dostępna online w [witrynie ecma w sieci Web](https://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
## <a name="in-this-section"></a>W tej sekcji
  
[Problemy z bezpieczeństwem w refleksji emitują](security-issues-in-reflection-emit.md)  
W tym artykule opisano problemy z zabezpieczeniami związane z tworzeniem zestawów dynamicznych przy użyciu emisji odbicia.  

[Jak: Definiowanie i wykonywanie metod dynamicznych](how-to-define-and-execute-dynamic-methods.md) Pokazuje, jak wykonać prostą metodę dynamiczną i metodę dynamiczną powiązaną z wystąpieniem klasy.

[Jak: Definiowanie typu ogólnego z emitować odbicie](how-to-define-a-generic-type-with-reflection-emit.md) Pokazuje, jak utworzyć prosty typ ogólny z dwoma parametrami typu, jak zastosować klasę, interfejs i ograniczenia specjalne do parametrów typu oraz jak utworzyć elementy członkowskie, które używają parametrów typu klasy jako typów parametrów i typów zwracanych.

[Jak: Zdefiniuj metodę rodzajową z emitować odbicie](how-to-define-a-generic-method-with-reflection-emit.md) Pokazuje, jak tworzyć, emitować i wywoływać prostą metodę rodzajową.

[Zespoły kolekcjonerskie do generowania typów dynamicznych](collectible-assemblies.md) Wprowadza zestawy kolekcjonerskie, które są zestawami dynamicznymi, które można zwolnić bez zwalniania domeny aplikacji, w której zostały utworzone.
  
## <a name="reference"></a>Dokumentacja  

<xref:System.Reflection.Emit.OpCodes>  
Kataloguje kody instrukcji MSIL, których można użyć do tworzenia obiektów metody.  
  
<xref:System.Reflection.Emit>  
Zawiera klasy zarządzane używane do emitowania metod dynamicznych, zestawów i typów.  
  
<xref:System.Type>  
Opisuje <xref:System.Type> klasę, która reprezentuje typy w zarządzanych odbicia i odbicia emitują i który jest kluczem do korzystania z tych technologii.  
  
<xref:System.Reflection>  
Zawiera klasy zarządzane używane do eksplorowania metadanych i kodu zarządzanego.  
  
## <a name="related-sections"></a>Sekcje pokrewne  

[Odbicie](reflection.md)  
W tym artykule wyjaśniono, jak eksplorować metadane i kod zarządzany.  
  
[Zestawy w środowisku .NET](../../standard/assembly/index.md)  
Zawiera omówienie zestawów w implementacjach platformy .NET.

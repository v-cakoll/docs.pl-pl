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
ms.openlocfilehash: 767382f27a96e8aacce4cc625de610949b3f02a3
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971039"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>Emitowanie dynamicznych metod i zestawów
W tej sekcji opisano zestaw typów zarządzanych w <xref:System.Reflection.Emit> przestrzeni nazw, które umożliwiają kompilatorowi lub narzędziu emitowanie metadanych i języka pośredniego firmy Microsoft (MSIL) w czasie wykonywania i opcjonalnie generowanie przenośnego pliku wykonywalnego (PE) na dysku. Aparaty skryptów i kompilatory są podstawowymi użytkownikami tej przestrzeni nazw. W tej sekcji funkcje zapewniane przez <xref:System.Reflection.Emit> przestrzeń nazw są określane jako emisja odbicia.  
  
 Emisja odbicia zapewnia następujące możliwości:  
  
- Zdefiniuj lekkie metody globalne w czasie wykonywania, używając <xref:System.Reflection.Emit.DynamicMethod> klasy i wykonuj je za pomocą delegatów.  
  
- Zdefiniuj zestawy w czasie wykonywania, a następnie uruchom je i/lub Zapisz na dysku.  
  
- Zdefiniuj zestawy w czasie wykonywania, uruchom je, a następnie zwolnij i zezwól na odzyskiwanie elementów bezużytecznych w celu odtworzenia zasobów.  
  
- Zdefiniuj moduły w nowych zestawach w czasie wykonywania, a następnie uruchom i/lub Zapisz je na dysku.  
  
- Zdefiniuj typy w modułach w czasie wykonywania, twórz wystąpienia tych typów i Wywołaj ich metody.  
  
- Zdefiniuj informacje symboliczne dla zdefiniowanych modułów, które mogą być używane przez narzędzia, takie jak debugery i program do tworzenia kodu.  
  
 Oprócz typów zarządzanych w <xref:System.Reflection.Emit> przestrzeni nazw istnieją niezarządzane interfejsy metadanych, które opisano w dokumentacji dotyczącej [interfejsów metadanych](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md) . Emitowane emisje odbicia udostępniają silniejsze sprawdzanie błędów semantycznych i wyższy poziom abstrakcji metadanych niż niezarządzane interfejsy metadanych.  
  
 Innym przydatnym zasobem do pracy z metadanymi i MSIL jest dokumentacja Common Language Infrastructure (CLI), szczególnie "partycja II: Definicja i semantyka metadanych "i" partycja III: Zestaw instrukcji CIL ". Dokumentacja jest dostępna online w [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) i w [witrynie sieci Web ECMA](https://go.microsoft.com/fwlink/?LinkId=116487).  
  
## <a name="in-this-section"></a>W tej sekcji
  
[Problemy z zabezpieczeniami w emisji odbicia](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
Opisuje problemy z zabezpieczeniami związane z tworzeniem zestawów dynamicznych przy użyciu emisji odbicia.  

[Instrukcje: Definiowanie i wykonywanie metod dynamicznych](how-to-define-and-execute-dynamic-methods.md)   
Pokazuje, jak wykonać prostą metodę dynamiczną i metodę dynamiczną powiązaną z wystąpieniem klasy.

[Instrukcje: Definiowanie typu ogólnego przy użyciu emisji odbicia](how-to-define-a-generic-type-with-reflection-emit.md)   
Pokazuje, jak utworzyć prosty typ ogólny z dwoma parametrami typu, jak zastosować klasę, interfejs i ograniczenia specjalne do parametrów typu oraz jak tworzyć składowe, które używają parametrów typu klasy jako typów parametrów i zwracanych typów.

[Instrukcje: Definiowanie metody ogólnej przy użyciu emisji odbicia](how-to-define-a-generic-method-with-reflection-emit.md)   
Pokazuje, jak tworzyć, emitować i wywoływać prostą metodę rodzajową.

[Zestawy kolekcjonowane do generowania typów dynamicznych](collectible-assemblies.md)   
Wprowadza zestawy kolekcjonowane, które są dynamicznymi zestawami, które można zwolnić bez zwalniania domeny aplikacji, w której zostały utworzone.
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Reflection.Emit.OpCodes>  
 Kataloguje kody instrukcji MSIL, których można użyć do kompilowania treści metody.  
  
 <xref:System.Reflection.Emit>  
 Zawiera klasy zarządzane używane do emitowania metod, zestawów i typów dynamicznych.  
  
 <xref:System.Type>  
 <xref:System.Type> Opisuje klasę, która reprezentuje typy w zarządzanym odbiciu i emitowaniu odbicia, które jest kluczem do korzystania z tych technologii.  
  
 <xref:System.Reflection>  
 Zawiera zarządzane klasy służące do eksplorowania metadanych i kodu zarządzanego.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Odbicie](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Wyjaśnia, jak eksplorować metadane i kod zarządzany.  
  
 [Zestawy w środowisku .NET](../../standard/assembly/index.md)  
 Zawiera omówienie zestawów w implementacjach platformy .NET.

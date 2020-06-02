---
title: Stosowanie atrybutów
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- attributes [.NET Framework], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
ms.openlocfilehash: 5557da1531eb55c13d1c7540a50b044d1a7b8a1d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276338"
---
# <a name="applying-attributes"></a>Stosowanie atrybutów
W celu zastosowania atrybutu do elementu kodu należy wykonać procedurę opisaną poniżej.  
  
1. Zdefiniuj nowy atrybut lub użyj istniejącego atrybutu, importując jego przestrzeń nazw ze środowiska .NET Framework.  
  
2. Zastosuj atrybut do elementu kodu, umieszczając go bezpośrednio przed elementem.  
  
     Każdy język ma własną składnię atrybutów. W językach C++ i C# atrybut jest ujęty w nawiasy kwadratowe i oddzielony od elementu znakiem odstępu, który może zawierać znak podziału wiersza. W języku Visual Basic atrybut jest ujęty w nawiasy kątowe i musi się znajdować w tym samym wierszu logicznym. Jeśli trzeba użyć podziału wiersza, można wstawić znak kontynuacji wiersza.
  
3. Określ parametry pozycyjne i nazwane atrybutu.  
  
     Parametry pozycyjne są wymagane i muszą się znajdować przed parametrami nazwanymi. Odpowiadają parametrom jednego z konstruktorów atrybutu. Parametry nazwane są opcjonalne i odnoszą się do właściwości odczytu/zapisu atrybutu. W językach C++ i C# Określ `name` = `value` dla każdego opcjonalnego parametru, gdzie `name` jest nazwą właściwości. W języku Visual Basic należy określić przyporządkowanie `name`:=`value`.  
  
 Atrybut jest emitowany do metadanych podczas kompilowania kodu. Jego udostępnianie środowisku uruchomieniowemu języka wspólnego i niestandardowym narzędziom lub aplikacjom odbywa się za pośrednictwem usług odbicia środowiska uruchomieniowego.  
  
 Zgodnie z konwencją wszystkie nazwy atrybutu kończą się ciągiem Attribute. Jednak niektóre języki przeznaczone dla tego środowiska uruchomieniowego, np. Visual Basic i C#, nie wymagają określania pełnej nazwy atrybutu. Na przykład, jeśli chcesz zainicjować, musisz <xref:System.ObsoleteAttribute?displayProperty=nameWithType> tylko odwołać się do niego jako **przestarzałe**.  
  
## <a name="applying-an-attribute-to-a-method"></a>Stosowanie atrybutu do metody  
 Poniższy przykład kodu pokazuje, jak deklarować element **System. ObsoleteAttribute**, który oznacza kod jako przestarzały. Ciąg tekstowy `"Will be removed in next version"` jest przekazywany do atrybutu. Atrybut sprawia, że podczas wywoływania kodu opisywanego przez atrybut kompilator generuje ostrzeżenie pokazujące przekazany ciąg.  
  
 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]  
  
## <a name="applying-attributes-at-the-assembly-level"></a>Stosowanie atrybutów na poziomie zestawów  
 Jeśli chcesz zastosować atrybut na poziomie zestawu, użyj **assembly** `Assembly` słowa kluczowego assembly (w Visual Basic). Poniższy kod przedstawia **AssemblyTitleAttribute** stosowane na poziomie zestawu.  
  
 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]  
  
 Zastosowanie tego atrybutu sprawia, że w manifeście zestawu w części pliku określającej metadane jest umieszczany ciąg `"My Assembly"`. Można wyświetlić atrybut przy użyciu [Dezasembler MSIL (Ildasm. exe)](../../framework/tools/ildasm-exe-il-disassembler.md) lub tworząc niestandardowy program do pobrania atrybutu.  
  
## <a name="see-also"></a>Zobacz także

- [Atrybuty](index.md)
- [Pobieranie informacji przechowywanych w atrybutach](retrieving-information-stored-in-attributes.md)
- [Pojęcia](/cpp/windows/attributed-programming-concepts)
- [Atrybuty (C#)](../../csharp/programming-guide/concepts/attributes/index.md)
- [Omówienie atrybutów (Visual Basic)](../../visual-basic/programming-guide/concepts/attributes/index.md)

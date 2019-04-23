---
title: 'Instrukcje: Badanie i tworzenie wystąpień typów ogólnych za pomocą odbicia'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ddddc746eb29c526adb8a15fc6ac40acc22954cf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337230"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a>Instrukcje: Badanie i tworzenie wystąpień typów ogólnych za pomocą odbicia
Informacje o typach ogólnych jest uzyskane w ten sam sposób jak informacje o innych typach:, sprawdzając <xref:System.Type> obiekt, który reprezentuje typ ogólny. Główna różnica polega na tym, typu ogólnego zawiera listę <xref:System.Type> obiekty reprezentujące jego parametrów typu rodzajowego. Pierwsza procedura w tej sekcji sprawdza typów ogólnych.  
  
 Możesz utworzyć <xref:System.Type> obiekt, który reprezentuje zbudowany typ przez powiązanie argumenty typu do parametrów typu w definicji typu ogólnego. Druga procedura pokazuje to.  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a>Aby zbadać typu ogólnego i jego parametrów typu  
  
1. Pobierz wystąpienia <xref:System.Type> który reprezentuje typ ogólny. W poniższym kodzie typ są uzyskiwane przy użyciu C# `typeof` — operator (`GetType` w języku Visual Basic `typeid` w programie Visual C++). Zobacz <xref:System.Type> temat poświęcony klasie dla innych sposobów uzyskania <xref:System.Type> obiektu. Należy pamiętać, że w dalszej części tej procedury, typ znajduje się w parametrze metody o nazwie `t`.  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. Użyj <xref:System.Type.IsGenericType%2A> właściwości, aby ustalić, czy typ ogólny, a następnie użyj <xref:System.Type.IsGenericTypeDefinition%2A> właściwości w celu określenia, czy typ jest definicja typu ogólnego.  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. Pobierz tablicę zawierającą argumenty typu generycznego, za pomocą <xref:System.Type.GetGenericArguments%2A> metody.  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. Dla każdego argumentu typu ustalenia, czy parametr typu (na przykład w definicji typu ogólnego) lub typu, który został określony dla parametru typu (na przykład w skonstruowanego typu), za pomocą <xref:System.Type.IsGenericParameter%2A> właściwości.  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. W systemie typów parametru typu generycznego jest reprezentowany przez wystąpienie <xref:System.Type>tak samo jak zwykła typy. Poniższy kod wyświetla nazwy i parametru położenie <xref:System.Type> obiekt, który reprezentuje parametr typu ogólnego. Pozycja parametru jest prosta informacje w tym miejscu; jest większe znaczenie, badając parametr typu, który został użyty jako argument typu z innym typem ogólnym.  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. Określić ograniczenia typu podstawowego i ograniczenia interfejsu parametr typu ogólnego przy użyciu <xref:System.Type.GetGenericParameterConstraints%2A> metodę, aby uzyskać wszystkie ograniczenia w jednej tablicy. Ograniczenia nie musi znajdować się w określonej kolejności.  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. Użyj <xref:System.Type.GenericParameterAttributes%2A> właściwości, aby odnaleźć specjalne ograniczenia dla parametru typu, na przykład wymaganie, że być typem referencyjnym. Właściwość zawiera również wartości, które reprezentują odchylenia, który może maskować off, jak pokazano w poniższym kodzie.  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. Atrybuty specjalne ograniczenia są flag i tę samą flagę (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) reprezentujący żadnych specjalnych ograniczenia reprezentuje również bez kowariancji i kontrawariancji. W związku z tym aby przetestować na jeden z tych warunków należy użyć odpowiedniej maski. W takim przypadku należy użyć <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> do izolowania flagi specjalne ograniczenia.  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a>Tworzenia wystąpienia typu ogólnego  
 Typ ogólny jest jako szablonu. Nie można utworzyć jego wystąpienia, jeśli nie podasz rzeczywistego typy dla jego parametrów typu rodzajowego. Aby to zrobić w czasie wykonywania, przy użyciu odbicia, wymaga <xref:System.Type.MakeGenericType%2A> metody.  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a>Do utworzenia wystąpienia typu ogólnego  
  
1. Pobierz <xref:System.Type> obiekt, który reprezentuje typ ogólny. Poniższy kod umożliwia pobranie typu ogólnego <xref:System.Collections.Generic.Dictionary%602> na dwa sposoby: za pomocą <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> przeciążenie metody z ciąg opisujący typ i wywołując <xref:System.Type.GetGenericTypeDefinition%2A> metoda skonstruowanego typu `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` w Visual Basic). <xref:System.Type.MakeGenericType%2A> Metoda wymaga definicji typu ogólnego.  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. Skonstruuj tablicę argumentów typu podstawiane dla parametrów typu. Tablica musi zawierać prawidłową liczbę <xref:System.Type> obiektów w tej samej kolejności, w jakiej występują na liście parametrów typu. W tym przypadku klucza (pierwszy parametr typu) jest typu <xref:System.String>, i wartości w słowniku są wystąpieniami klasy o nazwie `Example`.  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. Wywołaj <xref:System.Type.MakeGenericType%2A> metodę, aby powiązać argumentów typu parametrów typu i konstruowania typu.  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. Użyj <xref:System.Activator.CreateInstance%28System.Type%29> przeciążenia metody, aby utworzyć obiekt skonstruowanego typu. Poniższy kod przechowuje dwa wystąpienia `Example` klasy w wynikowym `Dictionary<String, Example>` obiektu.  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu przedstawia `DisplayGenericType` metodę, aby sprawdzić definicji typu ogólnego i typy utworzone używana w kodzie i wyświetlić swoje informacje. `DisplayGenericType` Metoda ma pokazać, jak używać <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, i <xref:System.Type.GenericParameterPosition%2A> właściwości i <xref:System.Type.GetGenericArguments%2A> metody.  
  
 Przykładzie zdefiniowano też `DisplayGenericParameter` metodę, aby sprawdzić parametr typu ogólnego i wyświetlić swoje ograniczenia.  
  
 Przykładowy kod definiuje zestaw typów testu, w tym typ ogólny, który ilustruje ograniczeniami parametrów typu i pokazuje sposób wyświetlania informacji na temat tych typów.  
  
 Przykład tworzy typ z <xref:System.Collections.Generic.Dictionary%602> klasy, tworząc tablicę argumentów typu i wywoływania <xref:System.Type.MakeGenericType%2A> metody. Porównuje program <xref:System.Type> obiekt skonstruowany przy użyciu <xref:System.Type.MakeGenericType%2A> z <xref:System.Type> uzyskany przy użyciu obiektu `typeof` (`GetType` w języku Visual Basic), demonstrując są takie same. Podobnie, program używa <xref:System.Type.GetGenericTypeDefinition%2A> metody uzyskiwania definicji typu ogólnego typu skonstruowany i porównuje go do <xref:System.Type> obiekt reprezentujący <xref:System.Collections.Generic.Dictionary%602> klasy.  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Zawiera kod języka C# `using` instrukcji (`Imports` w języku Visual Basic) niezbędne do kompilacji.  
  
-   Nie odwołania do zestawu dodatkowe są wymagane.  
  
-   Skompilować kod w wierszu polecenia przy użyciu csc.exe i vbc.exe, cl.exe. Aby skompilować kod w programie Visual Studio, umieść go w szablonie projektu aplikacji konsoli.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [Odbicie i typy ogólne](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
- [Wyświetlanie informacji o typie](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [Typy ogólne](../../../docs/standard/generics/index.md)

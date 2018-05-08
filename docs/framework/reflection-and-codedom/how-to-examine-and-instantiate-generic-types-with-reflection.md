---
title: 'Porady: zbadanie i tworzenie wystąpień typów ogólnych za pomocą odbicia'
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
ms.openlocfilehash: b0f964ac73f070b99cdfd06e9037d06ce7888938
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a>Porady: zbadanie i tworzenie wystąpień typów ogólnych za pomocą odbicia
Informacje o typach ogólnych są uzyskiwane w taki sam sposób jak informacje o innych typów:, sprawdzając <xref:System.Type> obiekt, który reprezentuje typ ogólny. Różnica zasady jest typem ogólnym listę <xref:System.Type> obiekty reprezentujące jego parametrów typu ogólnego. Pierwsza procedura w tej sekcji sprawdza typów ogólnych.  
  
 Można utworzyć <xref:System.Type> obiekt, który reprezentuje skonstruowanego typu przez powiązanie argumentów typu do parametrów typu w definicji typu ogólnego. Druga procedura pokazuje to.  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a>Aby sprawdzić typu ogólnego i jego parametrów typu  
  
1.  Pobranie wystąpienia <xref:System.Type> reprezentujący typ ogólny. W poniższym kodzie typ są uzyskiwane przy użyciu języka C# `typeof` — operator (`GetType` w języku Visual Basic `typeid` w programie Visual C++). Zobacz <xref:System.Type> klasy tematu inne sposoby <xref:System.Type> obiektu. Należy pamiętać, że w pozostałej części tej procedury, typ znajduje się w parametrze metody o nazwie `t`.  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2.  Użyj <xref:System.Type.IsGenericType%2A> właściwość, aby ustalić, czy typ jest rodzajowy i użyj <xref:System.Type.IsGenericTypeDefinition%2A> właściwości w celu określenia, czy typ jest definicją typu ogólnego.  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3.  Pobierz tablicę, która zawiera argumenty typu ogólnego, używając <xref:System.Type.GetGenericArguments%2A> metody.  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4.  Argumentu typu, należy ustalić, czy jest on parametr typu (na przykład w definicji typu ogólnego) lub typu, który został określony dla parametru typu (na przykład w skonstruowanego typu), za pomocą <xref:System.Type.IsGenericParameter%2A> właściwości.  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5.  W systemie typów parametru typu ogólnego jest reprezentowany przez wystąpienie <xref:System.Type>, podobnie jak w zwykłym typy. Poniższy kod wyświetla nazwę i parametr pozycję <xref:System.Type> obiekt, który reprezentuje parametr typu ogólnego. Pozycja parametru jest prosta informacji jest większe znaczenie, badając parametr typu, który został użyty jako argument typu innego typu ogólnego.  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6.  Określić ograniczenia typu podstawowego i ograniczenia interfejsu parametru typu ogólnego przy użyciu <xref:System.Type.GetGenericParameterConstraints%2A> metodę, aby uzyskać wszystkie ograniczenia w jednej macierzy. Ograniczenia nie gwarantuje się w określonej kolejności.  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7.  Użyj <xref:System.Type.GenericParameterAttributes%2A> właściwości, aby odnaleźć ograniczeń specjalnych na parametr typu, np. wymaganie jej typ referencyjny. Właściwość także wartości, które reprezentują wariancję, które można zamaskować off, jak pokazano w poniższym kodzie.  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8.  Atrybuty specjalne ograniczenia są flagi i tę samą flagę (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) reprezentujący żadnych specjalnych ograniczenia reprezentuje również nie Kowariancja i kontrawariancja. W związku z tym aby przetestować dla dowolnego z tych warunków należy użyć odpowiednią maskę. W takim przypadku należy użyć <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> do izolowania flagi ograniczeń specjalnych.  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a>Utworzenie wystąpienia typu ogólnego  
 Jest typem ogólnym jako szablonu. Nie można utworzyć wystąpień, chyba że zostanie rzeczywiste typy jego parametrów typu ogólnego. Aby to zrobić w czasie wykonywania, za pomocą odbicia, wymaga <xref:System.Type.MakeGenericType%2A> metody.  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a>Do utworzenia wystąpienia typu ogólnego  
  
1.  Pobierz <xref:System.Type> obiekt, który reprezentuje typ ogólny. Poniższy kod umożliwia pobranie typu ogólnego <xref:System.Collections.Generic.Dictionary%602> na dwa sposoby: za pomocą <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> przeciążenie metody zawierające ciąg opisujący typ i wywołując <xref:System.Type.GetGenericTypeDefinition%2A> metoda skonstruowanego typu `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` w Visual Basic). <xref:System.Type.MakeGenericType%2A> Metoda wymaga definicji typu ogólnego.  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2.  Konstruować tablicę argumentów typu do zastąpienia dla parametrów typu. Tablica musi zawierać prawidłową liczbę <xref:System.Type> obiektów w tej samej kolejności, w jakiej występują na liście parametrów typu. W tym przypadku klucz (pierwszy parametr typu) jest typu <xref:System.String>, a wartości w słowniku są wystąpieniami klasy o nazwie `Example`.  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3.  Wywołanie <xref:System.Type.MakeGenericType%2A> metodę, aby powiązać argumentów typu parametrów typu i konstruowania typu.  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4.  Użyj <xref:System.Activator.CreateInstance%28System.Type%29> przeciążenie metody można utworzyć typu skonstruowanego obiektu. Poniższy kod przechowuje dwa wystąpienia `Example` klasy w wynikowym `Dictionary<String, Example>` obiektu.  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod definiuje `DisplayGenericType` metodę Przeanalizuj definicje typu ogólnego i typy utworzone używane w kodzie i wyświetlać swoje informacje. `DisplayGenericType` Metody przedstawia sposób użycia <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, i <xref:System.Type.GenericParameterPosition%2A> właściwości i <xref:System.Type.GetGenericArguments%2A> metody.  
  
 Definiuje również przykład `DisplayGenericParameter` metody do badania parametr typu ogólnego i wyświetlić jej ograniczenia.  
  
 Przykładowy kod definiuje zestaw typów testu, w tym typu ogólnego, przedstawiono ograniczenia parametru typu, która przedstawia sposób wyświetlania informacji na temat tych typów.  
  
 Przykład tworzy typu z <xref:System.Collections.Generic.Dictionary%602> klasy, tworząc tablicę argumentów typu i wywoływanie <xref:System.Type.MakeGenericType%2A> metody. Program porównuje <xref:System.Type> tworzony przy użyciu obiektu <xref:System.Type.MakeGenericType%2A> z <xref:System.Type> uzyskany przy użyciu obiektu `typeof` (`GetType` w języku Visual Basic), z którego wynika, że są one takie same. Podobnie, program używa <xref:System.Type.GetGenericTypeDefinition%2A> metodę, aby uzyskać definicji typu ogólnego utworzony typ i porównuje go do <xref:System.Type> reprezentujący obiekt <xref:System.Collections.Generic.Dictionary%602> klasy.  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Zawiera kod C# `using` instrukcje (`Imports` w języku Visual Basic) niezbędne do kompilacji.  
  
-   Nie odwołania do zestawów dodatkowe są wymagane.  
  
-   Kompilowanie kodu w wierszu polecenia przy użyciu csc.exe, vbc.exe lub cl.exe. Aby skompilować kod w programie Visual Studio, należy umieścić w szablonie Projekt aplikacji konsoli.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Type>  
 <xref:System.Reflection.MethodInfo>  
 [Odbicie i typy ogólne](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)  
 [Wyświetlanie informacji o typie](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [Typy ogólne](../../../docs/standard/generics/index.md)

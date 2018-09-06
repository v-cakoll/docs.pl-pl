---
title: Używanie klasy StringBuilder w programie .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Remove method
- strings [.NET Framework], capacities
- StringBuilder object
- Replace method
- AppendFormat method
- Append method
- Insert method
- strings [.NET Framework], StringBuilder object
ms.assetid: 5c14867c-9a99-45bc-ae7f-2686700d377a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 099e2de40458e42c9df34e74dee8d9fc7c425dea
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891775"
---
# <a name="using-the-stringbuilder-class-in-net"></a>Używanie klasy StringBuilder w programie .NET
<xref:System.String> Obiektu jest niezmienny. Za każdym razem, gdy używasz jednej z metod w <xref:System.String?displayProperty=nameWithType> klasy, należy utworzyć nowy obiekt ciągu w pamięci, co wymaga nowego przydziału miejsca dla tego nowego obiektu. W sytuacjach, w których trzeba wykonać powtarzanych modyfikacji ciągu, obciążenie związane z utworzeniem nowej <xref:System.String> obiekt może być kosztowne. <xref:System.Text.StringBuilder?displayProperty=nameWithType> Klasa może być używana, gdy chcesz zmodyfikować ciąg bez tworzenia nowego obiektu. Na przykład za pomocą <xref:System.Text.StringBuilder> klasy może zwiększyć wydajność, gdy łączenie wielu ciągów w pętli.  
  
## <a name="importing-the-systemtext-namespace"></a>Importowanie Namespace System.Text  
 <xref:System.Text.StringBuilder> Klasa znajduje się w <xref:System.Text> przestrzeni nazw.  Aby uniknąć konieczności podać w pełni kwalifikowaną nazwę typu w kodzie, można importować <xref:System.Text> przestrzeni nazw:  
  
 [!code-cpp[Conceptual.StringBuilder#11](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#11)]
 [!code-csharp[Conceptual.StringBuilder#11](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#11)]
 [!code-vb[Conceptual.StringBuilder#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#11)]  
  
## <a name="instantiating-a-stringbuilder-object"></a>Utworzenie wystąpienia obiektu StringBuilder  
 Można utworzyć nowe wystąpienie klasy <xref:System.Text.StringBuilder> klasy przez inicjowanie zmiennej za pomocą jednej z metod przeciążonego konstruktora, jak pokazano w poniższym przykładzie.  
  
 [!code-cpp[Conceptual.StringBuilder#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#1)]
 [!code-csharp[Conceptual.StringBuilder#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#1)]
 [!code-vb[Conceptual.StringBuilder#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#1)]  
  
## <a name="setting-the-capacity-and-length"></a>Ustawienia pojemności i długość  
 Mimo że <xref:System.Text.StringBuilder> to obiekt dynamiczny, który pozwala zwiększyć liczbę znaków w ciągu, który hermetyzuje on można określić wartość maksymalnej liczby znaków, które może przechowywać. Wartość ta jest wywoływana pojemność obiektu i nie należy mylić z długość ciągu, bieżący <xref:System.Text.StringBuilder> przechowuje. Na przykład, możesz utworzyć nowe wystąpienie klasy <xref:System.Text.StringBuilder> klasy z ciągiem "Hello", który ma długość równą 5, a może określić, że obiekt ma maksymalną pojemność wynoszącą 25. Po zmodyfikowaniu <xref:System.Text.StringBuilder>, nie alokację rozmiar wykorzystywany aż do osiągnięcia pojemności. W takiej sytuacji nowe miejsce jest przydzielany automatycznie i podwaja się pojemności. Należy określić pojemność <xref:System.Text.StringBuilder> klasy przy użyciu jednej z przeciążenia konstruktorów. Poniższy przykład określa, że `myStringBuilder` obiektu można rozszerzyć do maksymalnie 25 miejsca do magazynowania.  
  
 [!code-cpp[Conceptual.StringBuilder#2](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#2)]
 [!code-csharp[Conceptual.StringBuilder#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#2)]
 [!code-vb[Conceptual.StringBuilder#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#2)]  
  
 Ponadto można użyć odczytu/zapisu <xref:System.Text.StringBuilder.Capacity%2A> właściwości, aby ustawić maksymalną długość obiektu. W poniższym przykładzie użyto **pojemności** właściwość, aby określić maksymalną długość.  
  
 [!code-cpp[Conceptual.StringBuilder#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#3)]
 [!code-csharp[Conceptual.StringBuilder#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#3)]
 [!code-vb[Conceptual.StringBuilder#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#3)]  
  
 <xref:System.Text.StringBuilder.EnsureCapacity%2A> Metoda może służyć do sprawdzania pojemności bieżącego **StringBuilder**. Jeśli pojemność jest większa niż wartość przekazany, nie zostanie zmienione; Jednak jeśli pojemność jest mniejsza niż wartość sukces, bieżąca pojemność jest zmieniany na pasuje do wartości przekazane.  
  
 <xref:System.Text.StringBuilder.Length%2A> Również można przeglądać lub ustaw właściwości. Jeśli ustawisz **długość** właściwość z wartością, która jest większa niż **pojemności** właściwości **pojemności** właściwość automatycznie zmieni się na taką samą wartość jak  **Długość** właściwości. Ustawienie **długość** właściwość z wartością, która jest mniejsza niż długość ciągu w bieżącej **StringBuilder** skraca ciągu.  
  
## <a name="modifying-the-stringbuilder-string"></a>Modyfikowanie ciągu StringBuilder  
 W poniższej tabeli wymieniono metody, można użyć do zmodyfikowania zawartości **StringBuilder**.  
  
|Nazwa metody|Zastosowanie|  
|-----------------|---------|  
|<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>|Dołącza informacje do końca bieżącego **StringBuilder**.|  
|<xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType>|Zastępuje specyfikatora formatu przekazany ciąg znaków z tekstu sformatowanego.|  
|<xref:System.Text.StringBuilder.Insert%2A?displayProperty=nameWithType>|Wstawia ciąg lub obiekt w określonym indeksie bieżącego **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Remove%2A?displayProperty=nameWithType>|Usuwa określoną liczbę znaków z bieżącego **StringBuilder**.|  
|<xref:System.Text.StringBuilder.Replace%2A?displayProperty=nameWithType>|Zamienia określony znak pod określonym indeksem.|  
  
### <a name="append"></a>Dołącz  
 **Append** metoda może służyć do dodawania tekstu lub ciąg reprezentujący obiekt do końca ciągu reprezentowane przez bieżącą **StringBuilder**. Poniższy przykład inicjuje **StringBuilder** do "Hello World", a następnie dołącza jakiś tekst na końcu obiektu. Miejsce jest przydzielane automatycznie, zgodnie z potrzebami.  
  
 [!code-cpp[Conceptual.StringBuilder#4](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#4)]
 [!code-csharp[Conceptual.StringBuilder#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#4)]
 [!code-vb[Conceptual.StringBuilder#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#4)]  
  
### <a name="appendformat"></a>Appendformat —  
 <xref:System.Text.StringBuilder.AppendFormat%2A?displayProperty=nameWithType> Metoda dodaje tekst na końcu <xref:System.Text.StringBuilder> obiektu. Obsługuje ona funkcję formatowania złożonego (Aby uzyskać więcej informacji, zobacz [formatowania złożonego](../../../docs/standard/base-types/composite-formatting.md)) przez wywołanie metody <xref:System.IFormattable> implementacji obiektu lub obiektów do sformatowania. W związku z tym akceptuje ciągi formatu standardowego dla wartości liczbowych, daty i godziny oraz wyliczenia, ciągi formatów niestandardowych dla liczbowe i wartości daty i godziny i ciągi formatu zdefiniowany dla typów niestandardowych. (Aby uzyskać informacje na temat formatowania, zobacz [typy formatowania](../../../docs/standard/base-types/formatting-types.md).) Można użyć tej metody można dostosować format zmiennych i Dołącz te wartości do <xref:System.Text.StringBuilder>. W poniższym przykładzie użyto <xref:System.Text.StringBuilder.AppendFormat%2A> metodę, aby umieścić wartość całkowitą sformatowane jako wartość waluty na końcu <xref:System.Text.StringBuilder> obiektu.  
  
 [!code-cpp[Conceptual.StringBuilder#5](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#5)]
 [!code-csharp[Conceptual.StringBuilder#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#5)]
 [!code-vb[Conceptual.StringBuilder#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#5)]  
  
### <a name="insert"></a>Insert  
 <xref:System.Text.StringBuilder.Insert%2A> Metoda dodaje ciąg lub obiekt do określonej pozycji w bieżącym <xref:System.Text.StringBuilder> obiektu. W poniższym przykładzie użyto tej metody można wstawić słowa do szóstego położenie <xref:System.Text.StringBuilder> obiektu.  
  
 [!code-cpp[Conceptual.StringBuilder#6](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#6)]
 [!code-csharp[Conceptual.StringBuilder#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#6)]
 [!code-vb[Conceptual.StringBuilder#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#6)]  
  
### <a name="remove"></a>Usuń  
 Możesz użyć **Usuń** metodę, aby usunąć określoną liczbę znaków z bieżącego <xref:System.Text.StringBuilder> obiektu, rozpoczynając od określonego indeksu zaczynającego się od zera. W poniższym przykładzie użyto **Usuń** metodę, aby skrócić <xref:System.Text.StringBuilder> obiektu.  
  
 [!code-cpp[Conceptual.StringBuilder#7](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#7)]
 [!code-csharp[Conceptual.StringBuilder#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#7)]
 [!code-vb[Conceptual.StringBuilder#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#7)]  
  
### <a name="replace"></a>Zastąp  
 **Zastąp** metoda może służyć do Zastąp znaki w obrębie <xref:System.Text.StringBuilder> obiektu na inny określony znak. W poniższym przykładzie użyto **Zastąp** metodę wyszukiwania <xref:System.Text.StringBuilder> obiektu dla wszystkich wystąpień wykrzyknika (!) znak i zastąpić je znak zapytania (?).  
  
 [!code-cpp[Conceptual.StringBuilder#8](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.StringBuilder/cpp/example.cpp#8)]
 [!code-csharp[Conceptual.StringBuilder#8](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/Example.cs#8)]
 [!code-vb[Conceptual.StringBuilder#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/Example.vb#8)]  
  
## <a name="converting-a-stringbuilder-object-to-a-string"></a>Konwersja obiektu StringBuilder na ciąg  
 Należy przekonwertować <xref:System.Text.StringBuilder> obiekt <xref:System.String> obiekt przed można przekazać ciągu, reprezentowane przez <xref:System.Text.StringBuilder> obiekt do metody, która ma <xref:System.String> parametru lub wyświetlić ją w interfejsie użytkownika. Wykonaj tę konwersję, wywołując <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> metody. Poniższy przykład wywołuje szereg <xref:System.Text.StringBuilder> metody, a następnie wywołania <xref:System.Text.StringBuilder.ToString?displayProperty=nameWithType> metodę w celu wyświetlenia ciągu.  
  
 [!code-csharp[Conceptual.StringBuilder#10](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/tostringexample1.cs#10)]
 [!code-vb[Conceptual.StringBuilder#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/tostringexample1.vb#10)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Text.StringBuilder?displayProperty=nameWithType>  
- [Podstawowe operacje na ciągach](../../../docs/standard/base-types/basic-string-operations.md)  
- [Formatowanie typów](../../../docs/standard/base-types/formatting-types.md)
